# unit_testing

# set sdk version for specific project
# creates a global.json to pin the sdk version
dotnet new globaljson --sdk-version 8.0.412


# list .net versions installed
dotnet --list-sdks
# 8.0.412 [/usr/local/share/dotnet/sdk]
# 9.0.303 [/usr/local/share/dotnet/sdk]


# get current version
dotnet --version


# disable telementry - add to zshrc
export DOTNET_CLI_TELEMETRY_OPTOUT=1


# create new asp.net 8.0 core web api application
dotnet new webapi -n unit_testing --framework net8.0
cd unit_testing

# Add xUnit and Moq for Testing
dotnet new xunit -n unit_testing.Tests --framework net8.0
cd unit_testing.Tests


# Install exact versions:
dotnet add package xunit --version 2.5.1
dotnet add package Moq --version 4.20.69
dotnet add package Microsoft.NET.Test.Sdk
dotnet add package xunit.runner.visualstudio


# Reference your API project:
dotnet add reference ../unit_testing.csproj

# open project in rider:
open -a "Rider.app" .


# debug
dotnet dev-certs https --clean --verbose

# clean and trust certs
dotnet dev-certs https --clean && dotnet dev-certs https --trust

# trust certs
dotnet dev-certs https --trust

dotnet --list-sdks
