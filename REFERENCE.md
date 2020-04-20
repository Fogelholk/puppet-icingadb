# Reference
<!-- DO NOT EDIT: This document was generated by Puppet Strings -->

## Table of Contents

**Classes**

_Public Classes_

* [`icingadb`](#icingadb): Puppet class to manage IcingaDB.
* [`icingadb::globals`](#icingadbglobals): This class loads the default parameters by doing a hiera lookup.
* [`icingadb::redis`](#icingadbredis): Manage the IcingaDB Redis server.
* [`icingadb::redis::globals`](#icingadbredisglobals): This class loads the default parameters by doing a hiera lookup.

_Private Classes_

* `icingadb::config`: A short summary of the purpose of this class
Configures IcingaDB
* `icingadb::install`: Installs IcingaDB
* `icingadb::install::mysql`: Imports MySQL IcingaDB schema
* `icingadb::install::pgsql`: Imports PostgreSQL IcingaDB schema
* `icingadb::redis::config`: Configures IcingaDB Redis server
* `icingadb::redis::install`: Installs IcingaDB Redis server
* `icingadb::redis::service`: Manage IcingaDB Redis server service
* `icingadb::service`: Manage IcingaDB service

## Classes

### icingadb

Puppet class to manage IcingaDB.

#### Examples

##### 

```puppet
class { 'icingadb':
  manage_repo      => true,
  db_password      => 'supersecret',
  import_db_schema => true,
  require          => Mysql::Db['icingadb'],
}
```

#### Parameters

The following parameters are available in the `icingadb` class.

##### `Enum`

Data type: `'running', 'stopped'`

ensure
Choose wether the service is `running` or `stopped`. Defaults to `running`.

##### `enable`

Data type: `Boolean`

Choose wether the service has to start at boot. Defaults to `true`.

Default value: `true`

##### `redis_host`

Data type: `Stdlib::Host`

Redis server to connect. Defaults to `localhost`.

Default value: 'localhost'

##### `redis_port`

Data type: `Optional[Stdlib::Port::Unprivileged]`

Port on the Redis host to connect. Defaults by IcingaDB to `6380`.

Default value: `undef`

##### `redis_pool_size`

Data type: `Optional[Integer[0]]`

Maximum number of socket connections. Defaults by IcingaDB to `64`.

Default value: `undef`

##### `db_type`

Data type: `Enum['mysql','pgsql']`

Choose wether MySQL or PostgreSQL as backend for historical data. Defaults to `mysql`.

Default value: 'mysql'

##### `db_host`

Data type: `Stdlib::Host`

Database server. Defaults to `localhost`.

Default value: 'localhost'

##### `db_port`

Data type: `Optional[Stdlib::Port::Unprivileged]`

Port to connect the DBMS. Defaults by IcingaDB to 3306 for MySQL or 5432 for PostgreSQL.

Default value: `undef`

##### `db_name`

Data type: `String`

The IcingaDB database. Defaults to `icingadb`.

Default value: 'icingadb'

##### `db_username`

Data type: `String`

User that is used to connect the database. Defaults to `icingadb`.

Default value: 'icingadb'

##### `db_password`

Data type: `String`

Passwort to login database.

##### `db_max_open_conns`

Data type: `Optional[Integer[0]]`

Maximum number of open connections. Defaults by IcingaDB to 50.

Default value: `undef`

##### `import_db_schema`

Data type: `Boolean`

Enables the initial creation of the database schema. Defaults to `false`.

Default value: `false`

##### `manage_repo`

Data type: `Boolean`

Whether to involve the Icinga repositories. Defaults to `false`.

Default value: `false`

##### `manage_package`

Data type: `Boolean`

Whether to manage the IcingaDB package. Defaults to `true`.

Default value: `true`

##### `ensure`

Data type: `Enum['running','stopped']`



Default value: 'running'

### icingadb::globals

This class loads the default parameters by doing a hiera lookup.

#### Parameters

The following parameters are available in the `icingadb::globals` class.

##### `package_name`

Data type: `String`



##### `service_name`

Data type: `String`



##### `user`

Data type: `String`



##### `group`

Data type: `String`



##### `conf_dir`

Data type: `Stdlib::Absolutepath`



##### `mysql_db_schema`

Data type: `Stdlib::Absolutepath`



### icingadb::redis

Manage the IcingaDB Redis server.

#### Examples

##### 

```puppet
class { '::icingadb::redis':
  manage_repo => true,
  bind        => '127.0.0.1',
  port        => 6380,
}
```

#### Parameters

The following parameters are available in the `icingadb::redis` class.

##### `ensure`

Data type: `Enum['running','stopped']`

Choose wether the service is `running` or `stopped`. Defaults to `running`.

Default value: 'running'

##### `ensure`

Data type: `Boolean`

Choose wether the service has to start at boot. Defaults to `true`.

Default value: 'running'

##### `bind`

Data type: `Variant[Stdlib::Host,Array[Stdlib::Host]]`

Configure which IP address(es) to listen on. To bind on all interfaces, use an empty array.
Defaults to `127.0.0.1` and `::1`.

Default value: [ '127.0.0.1', '::1' ]

##### `port`

Data type: `Stdlib::Port::Unprivileged`

Configure which port to listen on. Defaults to `6380`.

Default value: 6380

##### `manage_repo`

Data type: `Boolean`

Whether to involve the Icinga repositories. Defaults to `false`.

Default value: `false`

##### `manage_package`

Data type: `Boolean`

Whether to manage the IcingaDB package. Defaults to `true`.

Default value: `true`

##### `enable`

Data type: `Boolean`



Default value: `true`

### icingadb::redis::globals

This class loads the default parameters by doing a hiera lookup.

#### Parameters

The following parameters are available in the `icingadb::redis::globals` class.

##### `package_name`

Data type: `String`



##### `service_name`

Data type: `String`



##### `service_unit_file`

Data type: `Stdlib::Absolutepath`


