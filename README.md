Express is a Node.js web application framework that provides a robust set of features for web and mobile applications.

Install the npm packages for:

    Creating an api skeleton: npm install -g express-generator

    Connection with SQL Server: npm install tedious

Import variables

    var Connection = require('tedious').Connection;
    
    var Request = require('tedious').Request;
    
Config for Sql Server

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
Connect api with Sql Server

    connect: function connect() {
      let data = [];
      connection = new Connection(config);
      connection.on('connect', function (err, res) {

        if (err) {
          console.log('Not Connected')
        }
        else {
          // If no error, then good to go...
          console.log("Connected");
        }
      });

    }
  
  To get more help on tedious functions visit http://tediousjs.github.io/tedious/api-connection.html
