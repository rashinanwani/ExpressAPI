Express is a Node.js web application framework that provides a robust set of features for web and mobile applications.

Install the npm packages for:

    Creating an api skeleton: npm install -g express-generator

    Connection with SQL Server: npm install tedious
    
Create an express app

    express <app_name>

Import variables

    var Connection = require('tedious').Connection;
    
    var Request = require('tedious').Request;
    
Import Config for Sql Server

    config =
    {
      server: "yourServerName",
      options: {
        database: "yourDatabase",
      },
      authentication: {
        type: "default",
        options: {
          userName: "yourUserName",
          password: "yourPassWord"
        }
      },
      options: {
        encrypt: false,
        //trustedConnection:true,
        //port:1433
      }
    };
    
For Connection of API with SQL Server

    connect: function connect() {
      connection = new Connection(config);
      connection.on('connect', function (err, res) { YourCode....});
    }
    
For executing SQL queries 
 
    request = new Request("YourQuery", function (err, res) { YourCode....});
    connection.execSql(request);
  
  To get more help on request instances visit http://tediousjs.github.io/tedious/api-request.html and for tedious functions visit http://tediousjs.github.io/tedious/api-connection.html
