[![Build Status](https://travis-ci.org/donaldaverill/meteor-package-dinerware.svg)](https://travis-ci.org/donaldaverill/meteor-package-dinerware)
Connect to a Dinerware POS
=============================
This package allows for connecting to a Dinerware POS Brain. It doesn't do much
other than connecting at this point. Meteor server must be on the Brain
terminal or in the network with the SQL Server on the brain accessible to
network computers with password authentication. Package uses [tedious](https://www.npmjs.com/package/tedious) and [tedious-connection-pool](https://www.npmjs.com/package/tedious-connection-pool) npm packages.
## Install
To install in a new project:
```bash
> meteor add donaldaverill:dinerware
```
## Use
Configure Dinerware object by adding [connection details](https://www.npmjs.com/package/tedious-connection-pool) to your setting.json file like:
```json
{
  "dinerware": {
    "connection": {
      "userName": "login",
      "password": "password",
      "server": "localhost"
    },
    "connectionPool": {
      "min": "2",
      "max": "4",
      "log: true
    }
  }
}
```
You can also configure Dinerware by passing config details directly:
```js
var poolConfig = {
    min: 2,
    max: 4,
    log: true
};
var connectionConfig = {
    userName: 'login',
    password: 'password',
    server: 'localhost'
};
Dinerware.config(poolConfig, connectionConfig);
```
Currently, this package doesn't do much except to print query results. You can fork and add your own methods. Submit a PR if you like. To print query results:
```js
Dinerware.printQuery('SELECT * FROM SomeTable');
```