# table-dumper

A helper script for dumping database tables. Credentials and configurations
are read from an .env file.

## First usage (_single usage_)

```bash
$ git clone git@gitlab.rsm-support.de:helper/dbhelper.git && cd dbhelper
$ cp .env.dist .env
```

Adjust the variables according to the system.

## Show version

```bash
$ bin/table-dumper -V
```

**Outputs**:

```
table-dumper 0.1.0 (2022-05-21 22:48:12) - Björn Hempel <bjoern@hempel.li>
```

## Show help

```bash
$ bin/table-dumper -h
```

**Outputs**:

```bash

table-dumper 0.1.0 (2022-05-21 22:48:12) - Björn Hempel <bjoern@hempel.li>

Usage: table-dumper [options...] sync

 -e,    --env-path                    Contains the environment path (default .env)

 -dcs,  --disable-column-statistics   Disable mysql column statistics


 -t,    --with-time                   Also outputs the time to each log entry (default: false).
 -v,    --verbose                     Set output to verbose (default: false).
 -c,    --color                       Colored output (default: false).
 -d,    --debug                       Set to debug mode. No longer performs any actions.
                                      Shows only the commands. (default: false).
 -u,    --update-version              Shows this script with updated version read from VERSION
 -h,    --help                        Shows this help.
 -V,    --version                     Shows the version number.

```

## Dumping database tables

The command only shows the commands and does not execute them:

```bash
$ bin/table-dumper dump -d
```

## Backup and sync db and folder to remote

```bash
$ bin/table-dumper dump
```

## Show log

```bash
$ bin/table-dumper -l
```

**Outputs**:

```
PRINT THE LAST 20 LOG LINES
===========================

Path: /path/to/project/table-dumper.log

───────────────────────────────────────────────────────────────────────────────
[2022-05-21 23:29:54] - info - Dump and write SQL file "/path/to/project/fixtures/db/place_a.sql".
[2022-05-21 23:29:54] - success - Snapshot is done: /path/to/project/fixtures/db/place_a.sql (Size: 9.4M)
[2022-05-21 23:29:54] - info - Dump and write SQL file "/path/to/project/fixtures/db/place_h.sql".
[2022-05-21 23:29:54] - success - Snapshot is done: /path/to/project/fixtures/db/place_h.sql (Size: 12M)
[2022-05-21 23:29:54] - info - Dump and write SQL file "/path/to/project/fixtures/db/place_l.sql".
[2022-05-21 23:29:54] - success - Snapshot is done: /path/to/project/fixtures/db/place_l.sql (Size: 2.4M)
[2022-05-21 23:29:54] - info - Dump and write SQL file "/path/to/project/fixtures/db/place_p.sql".
[2022-05-21 23:29:55] - success - Snapshot is done: /path/to/project/fixtures/db/place_p.sql (Size: 61M)
[2022-05-21 23:29:55] - info - Dump and write SQL file "/path/to/project/fixtures/db/place_r.sql".
[2022-05-21 23:29:55] - success - Snapshot is done: /path/to/project/fixtures/db/place_r.sql (Size: 284K)
[2022-05-21 23:29:55] - info - Dump and write SQL file "/path/to/project/fixtures/db/place_s.sql".
[2022-05-21 23:29:55] - success - Snapshot is done: /path/to/project/fixtures/db/place_s.sql (Size: 44M)
[2022-05-21 23:29:55] - info - Dump and write SQL file "/path/to/project/fixtures/db/place_t.sql".
[2022-05-21 23:29:56] - success - Snapshot is done: /path/to/project/fixtures/db/place_t.sql (Size: 19M)
[2022-05-21 23:29:56] - info - Dump and write SQL file "/path/to/project/fixtures/db/place_u.sql".
[2022-05-21 23:29:56] - success - Snapshot is done: /path/to/project/fixtures/db/place_u.sql (Size: 4.0K)
[2022-05-21 23:29:56] - info - Dump and write SQL file "/path/to/project/fixtures/db/place_v.sql".
[2022-05-21 23:29:56] - success - Snapshot is done: /path/to/project/fixtures/db/place_v.sql (Size: 2.2M)
[2022-05-21 23:29:56] - skipped - Local: Table "refresh_tokens" ignored by config (rule: refresh_tokens).
[2022-05-21 23:29:56] - skipped - Local: Table "user" ignored by config (rule: user).
───────────────────────────────────────────────────────────────────────────────
```

## Installation as a submodule

```bash
git submodule add git@github.com:bjoern-hempel/table-dumper.git submodules/table-dumper
```

```bash
mkdir bin && cd bin && ln -s ../submodules/table-dumper/bin/table-dumper . && cd ..
```

```bash
bin/table-dumper -V
```

**Outputs**:

```bash
table-dumper 0.1.0 (2022-05-21 22:48:12) - Björn Hempel <bjoern@hempel.li>
```

## Update version

```bash
bin/table-dumper -u > bin/table-dumper
```

## Import dump

Currently, the import is not yet supported, but can be done manually.

```bash
mysql -h[host] -u[user] -p[password] -P[port] [dbname] -e "source [path-to-sql-file]"
```