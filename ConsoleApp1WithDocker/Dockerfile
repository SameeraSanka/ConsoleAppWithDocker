#use the official .net Core SDK image to build the app
FROM mcr.microsoft.com/dotnet/aspnet:8.0-alpine AS base
WORKDIR /app
EXPOSE 8080

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY . .
RUN dotnet restore
RUN dotnet publish -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "ConsoleApp1WithDocker.dll"]



## Use the official .NET Core SDK image as the base image
#FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
#WORKDIR /app
#
## Copy the .csproj file and restore dependencies
#COPY *.csproj ./
#RUN dotnet restore
#
## Copy the rest of the application code and build the application
#COPY . ./
#RUN dotnet publish -c Release -o out
#
## Use the official .NET Core runtime image as the base image for the final stage
#FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
#WORKDIR /app
#COPY --from=build /app/out ./
#
## Set the entry point for the application
#ENTRYPOINT ["dotnet", "YourApp.dll"]	
