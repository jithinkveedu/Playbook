FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build-env
WORKDIR /app

EXPOSE 80
EXPOSE 443

ENV ASPNETCORE_URLS=http://+:80

COPY *.csproj ./
RUN dotnet restore

COPY ./ ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "ActionsDemo.dll"]
