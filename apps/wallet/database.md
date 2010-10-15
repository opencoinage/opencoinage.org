OpenCoinage Wallet Database Format
==================================

_This specification is current as of October 2010._

[TOC]

Overview
--------

This document provides an engineering guide to the wallet database file
format used by the [OpenCoinage Wallet](/apps/wallet) reference
implementations.

None of the information contained in this document is required by
programmers utilizing the [OpenCoinage SDK](/sdk) libraries in their
applications. The intended audience is engineers working on new [wallet
applications](/apps) or those interested in creating alternative methods of
accessing existing wallet database files created by currently-available
applications.

File Extension
--------------

The file extension for OpenCoinage-compliant wallet database files is
`.ocdb` and the (as yet unregistered) [MIME content type][MIME type] is
`application/vnd.opencoinage.database`.

Database Format
---------------

Wallet databases are implemented as [SQLite][] database files. SQLite is a
robust and lightweight embedded [SQL][] database engine that runs on all
major platforms and comes bundled with many operating systems including Mac
OS X, iOS, Android, and most Linux and *BSD distributions.

The [database file format][SQLite format] is the current (as of 2010) format
[introduced in SQLite 3.3.0](http://www.sqlite.org/formatchng.html).
Legacy SQLite file formats and older SQLite engine versions are not
supported.

Database Settings
-----------------

Before mutating a wallet database in any way, the following
[`PRAGMA`][SQLite pragma] statements must be issued to correctly set up
database engine settings important to interoperability requirements and
data integrity.

### File format

[`PRAGMA legacy_file_format`][PRAGMA format] determines whether new database
files are created using the legacy (SQLite 3.0.0+) or the latest (SQLite
3.3.0+) file format. Wallet databases should be created in the newer file
format.

    PRAGMA legacy_file_format = OFF;

### Text encoding

[`PRAGMA encoding`][PRAGMA encode] sets the text encoding of the database
file. Once an encoding has been set for a database file, it cannot be
changed later on; hence this `PRAGMA` statement **must** be issued when
creating a new wallet database to ensure interoperability among
implementations.

    PRAGMA encoding = "UTF-8";

### Foreign-key constraints

[`PRAGMA foreign_keys`][PRAGMA foreign] is used to enforce [foreign-key
constraints][SQLite FKC]. This helps preserve data integrity and
consistency in case of subtle application-level bugs.

    PRAGMA foreign_keys = ON;

### Secure deletions

[`PRAGMA secure_delete`][PRAGMA delete] is used to enable secure-delete
mode, which ensures that the database engine explicitly overwrites any
deleted data with zeros. This helps prevent clandestine recovery of such
data by an adversary with access to the file system or physical disk media
in question.

    PRAGMA secure_delete = ON;

### Synchronous mode

[`PRAGMA synchronous`][PRAGMA sync] is used to enable full synchronous mode,
which ensures that the SQLite database engine will pause at critical moments
to make sure that data has actually been written to the disk before
continuing. This helps prevent database corruption in case a power failure
occurs or should the application or operating system crash for any other
reason.

    PRAGMA synchronous = FULL;

[`PRAGMA fullfsync`][PRAGMA ffsync] can optionally be used to enable yet
more data integrity guarantees on systems that support it (currently only
Mac OS X), albeit at the cost of a potentially [noticeable][fullfsync]
performance hit.

    PRAGMA fullfsync = ON;

Database Encryption
-------------------

TODO

Table Prefix
------------

The default SQLite table prefix used is `"opencoinage_"`. While this could
be reconfigured for specific applications, doing so is not advisable as it
would hinder or prevent interoperability with other OpenCoinage tooling.

Table Definitions
-----------------

### `opencoinage_issuer`

TODO

### `opencoinage_currency`

TODO

### `opencoinage_token`

TODO

### `sqlite_sequence`

TODO

Trigger Definitions
-------------------

No standard triggers have been defined as yet.

Schema Version
--------------

The database schema version is a monotonically increasing integer. A value
of zero indicates an uninitialized new database.

The schema version is stored in the [database file header][SQLite header]'s
`user-cookie` field at byte offset 60 as a 32-bit [big-endian][] signed
integer.

### Reading the schema version using SQL

Over a SQLite database connection, the current schema version can be
obtained using a [`PRAGMA user_version`][PRAGMA version] statement as
follows:

    PRAGMA user_version;

### Reading the schema version using SQLite3/Ruby

When using the [SQLite3/Ruby][] library, the current schema version can be
obtained as follows:

    require 'sqlite3'
    
    SQLite3::Database.open("wallet.ocdb") do |db|
      puts "Schema version: " + db.user_cookie.to_s
    end

### Reading the schema version on Android

On the [Android][] platform, you can use the
[`SQLiteDatabase#getVersion()`][a.d.s.SQLD#gV] method to obtain the current
schema version:

    import android.database.sqlite.SQLiteDatabase;
    import android.database.sqlite.SQLiteException;
    
    try {
      String path = "wallet.ocdb"; // this is application-specific
      SQLiteDatabase db = SQLiteDatabase.openDatabase(path, null, SQLiteDatabase.OPEN_READONLY);
      System.out.println("Schema version: " + db.getVersion());
    }
    catch (SQLiteException e) {
      e.printStackTrace();
    }

Note that the [`SQLiteOpenHelper`][a.d.s.SQLOH] class includes built-in
version management, so subclassing it is the most straightforward approach
to correctly handling schema upgrades.

Schema Upgrades
---------------

### Algorithm

TODO

### Version 0 {#version-0}

This version indicates an uninitialized new database, devoid of all tables
and any data.

_Download the SQL script for this upgrade: [`0.sql`](database/0.sql)._

### Version 1 {#version-1}

_This is the current database version._

TODO

    CREATE TABLE opencoinage_issuer (
      id      INTEGER PRIMARY KEY AUTOINCREMENT,
      uri     TEXT NOT NULL
    );
    CREATE TABLE opencoinage_currency (
      id      INTEGER PRIMARY KEY AUTOINCREMENT,
      uri     TEXT NOT NULL
    );
    CREATE TABLE opencoinage_token (
      id      INTEGER PRIMARY KEY AUTOINCREMENT,
      data    BLOB NOT NULL UNIQUE,
      amount  NUMERIC DEFAULT NULL,
      expires INTEGER DEFAULT NULL
    );

_Download the SQL script for this upgrade: [`1.sql`](database/1.sql)._

[MIME type]:      http://en.wikipedia.org/wiki/Internet_media_type
[SQL]:            http://en.wikipedia.org/wiki/SQL
[SQLite]:         http://en.wikipedia.org/wiki/SQLite
[SQLite format]:  http://www.sqlite.org/fileformat.html
[SQLite header]:  http://www.sqlite.org/fileformat.html#database_header
[SQLite FKC]:     http://www.sqlite.org/foreignkeys.html
[SQLite pragma]:  http://www.sqlite.org/pragma.html
[PRAGMA format]:  http://www.sqlite.org/pragma.html#pragma_legacy_file_format
[PRAGMA encode]:  http://www.sqlite.org/pragma.html#pragma_encoding
[PRAGMA delete]:  http://www.sqlite.org/pragma.html#pragma_secure_delete
[PRAGMA sync]:    http://www.sqlite.org/pragma.html#pragma_synchronous
[PRAGMA ffsync]:  http://www.sqlite.org/pragma.html#pragma_fullfsync
[fullfsync]:      http://www.mail-archive.com/sqlite-users@sqlite.org/msg06502.html
[PRAGMA foreign]: http://www.sqlite.org/pragma.html#pragma_foreign_keys
[PRAGMA version]: http://www.sqlite.org/pragma.html#pragma_schema_version
[big-endian]:     http://en.wikipedia.org/wiki/Endianness
[SQLite3/Ruby]:   http://rdoc.info/github/luislavena/sqlite3-ruby/master/file/README.rdoc
[Android]:        http://en.wikipedia.org/wiki/Android_(operating_system)
[a.d.s.SQLD#gV]:  http://developer.android.com/reference/android/database/sqlite/SQLiteDatabase.html#getVersion()
[a.d.s.SQLOH]:    http://developer.android.com/reference/android/database/sqlite/SQLiteOpenHelper.html
