#install sdk to build the app
FROM mcr.microsoft.com/dotnet/sdk:9.0 As build
WORKDIR /src
COPY . .
RUN dotnet restore
RUN dotnet build -c Release -o /app/publish
#publish the app
From mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/publish .  
Expose 8080
cmd ["dotnet", "apiApp.dll"]
