## GitHub Portal
Lists all InnerSource projects of Philips in an interactive and easy to use way. Can be used as a template for implementing the [InnerSource Portal pattern](https://patterns.innersourcecommons.org/p/innersource-portal) by the [InnerSource Commons](http://innersourcecommons.org/) community.

## Inspiration
This project is heavily inspired by the [SAP Project Portal for InnerSource](https://github.com/SAP/project-portal-for-innersource).

## State
Work in progress - Functional, but not ready for production.  
  
Functional Crawler.  
Functional Portal.

## System Requirements
* [.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1)
* [Node 14](https://nodejs.org/en/)

## Technology Stack
* [Blazor Web Assembly](https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor)  
* .NET Core 3.1
* [TailwindCSS](https://tailwindcss.com/)

## Pros vs Cons
Learn more about the pros and cons of using this project.

#### Pros
- Improved performance with large repository count
- Built with modern frameworks like TailwindCSS and Blazor that compiles to WebAssembly.
- Improved search functionality that allows you to search on topics, description, name, url, etc.
- Easier to maintain due to seperated responsibilities.
- Built to scale.

#### Cons
- Poor styling of the portal.
- Philips specific styling(will need brief restyle).

## Crawler
The crawler is based on the InnerSource Crawler on Philips-forks. This one is built with C# and runs as a console application. It's configurable to an extend. Configuration options are discussed in detail below.

### Configuration
Use environment variables to customize the values in the config file (appsettings.json).
Available environment variables are:

| Environment Variable  | Description | Default value |
| ------------ | --------------- | --------------- |
| App__Self__MetaDataFileName | Name of the meta data file | philips-repo.yaml
| App__Self__GithubToken | Authentication token used to authenticate API requests | token
| App__Self__YamlMode | Is the meta data file a YAML/YML file or is it a JSON? If Yaml, true, if JSON, false | true
| App__Self__DatabaseMode | Do you want to output the default repos.json or output to a database? | false
| App__Self__GithubOrganization | Name of the Github Organization to query | philips-internal

Common commands that are used to set these variables are: ``export VARIABLE_HERE=VALUE_HERE``

### Instructions
1. Navigate to the Crawler directory and execute ``dotnet build``.
2. Make sure that the Github Token is set in the appsettings, or via environment variable.
3. Execute ``dotnet run`` to execute the crawler. Hit ``cntrl+c`` to stop it.
4. In the directory, a repos.json is created. This can be used in the Portal.

## Portal
The portal itself is functional, but still under development. Work is being done to make it compatible with pulling data from a REST API instead of from the repos.json. 
The repos.json will still be the default behavior, but the REST API will be the recommended way as it is more performant and scalable.

### Instructions
1. Navigate to the Portal directory and execute ``npm install``. This is done to install Tailwind, with required dependencies like PostCSS.
1. Execute ``dotnet build`` to build the project.
1. Place the ``repos.json`` that is generated by the Crawler, in the ``wwwroot/sample-data`` directory. If the sample-data directory does not exist, create it.
1. Execute ``dotnet run`` to run the portal with the data that is retrieved by the crawler.


### Screenshots
![Screenshot 2021-07-09 at 13 36 09 (2)](https://user-images.githubusercontent.com/15904543/125072751-42d9ac80-e0bb-11eb-8836-4fa2fbe87d87.png)

![Screenshot 2021-07-09 at 13 36 28](https://user-images.githubusercontent.com/15904543/125072698-2fc6dc80-e0bb-11eb-8ede-a7a143885e5c.png)

