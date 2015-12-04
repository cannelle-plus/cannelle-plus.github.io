
<!DOCTYPE html>
<html lang="en-us">
  <head>
    <meta charset="UTF-8">
    <title>Cannelle-plus.GitHub.io by cannelle-plus</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" type="text/css" href="stylesheets/normalize.css" media="screen">
    <link href='https://fonts.googleapis.com/css?family=Open+Sans:400,700' rel='stylesheet' type='text/css'>
    <link rel="stylesheet" type="text/css" href="stylesheets/stylesheet.css" media="screen">
    <link rel="stylesheet" type="text/css" href="stylesheets/github-light.css" media="screen">
  </head>
  <body>
    <section class="page-header">
      <h1 class="project-name">Cannelle-plus.GitHub.io</h1>
      <h2 class="project-tagline">Logging</h2>
    </section>

    <section class="main-content">
      <h3>Elmah.IO</h3>

      baby steps to test elmah.IO

      nuget install elmah.io

      create fsx scripts :

<code>
#r @"elmah.corelibrary.1.2.2\lib\Elmah.dll"  
#r @"elmah.io.core.1.0.0.33\lib\net40\Elmah.IO.dll"  
  
open System  
open System.Collections.Generic  
open Elmah  
type ErrorLog = Elmah.Io.ErrorLog  
  
let config = new Dictionary<string, string>()  
config.Add( "LogId", "82021200-d9e1-4958-bcbd-1a66c7724289")  
  
let  log = new Elmah.Io.ErrorLog(config)  
  
try  
let doSomethingNasty = 185/0  
doSomethingNasty.ToString()  
with  
| exn   ->
    let   err = Error exn
    err.Time <- datetime.now  
    err.applicationname <- "Petulant cub"  
    let logTask =  
        Async.FromBeginEnd(err, log.BeginLog, log.EndLog)  
        |> Async.StartAsTask
  
logTask.Result  
</code>




    </section>


  </body>
</html>
