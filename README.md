https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-3.1&tabs=visual-studio-code
NOTE: this is specific to v 3.1
## Create the webproject with dependencies
dotnet new webapi -o TodoApi
cd TodoApi
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.InMemory
code -r ../TodoApi

## Add some code to the Startup.cs (Follow site)

## Scaffold a controller
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet tool install --global dotnet-aspnet-codegenerator
dotnet tool update -g Dotnet-aspnet-codegenerator
dotnet aspnet-codegenerator controller -name TodoItemsController -async -api -m TodoItem -dc TodoContext -outDir Controllers

## Start the web server
dotnet watch run

## Post using curl
# There is a json file that contains post data
https://gist.github.com/subfuzion/08c5d85437d5d4f00e58 - cheatsheet to curl post
curl -d "{\"name\": \"walk dog\",\"isComplete\": true}" -H "Content-Type: application/json" -X POST http://localhost:5000/api/TodoItems

Grab the data you just stored!
curl -k -i -H "Accept: application/json" -H "Content-Type: application/json" -X GET https://localhost:5001/api/TodoItems/1
