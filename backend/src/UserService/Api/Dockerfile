# Stage 1: Build
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copy the current directory (contains Api.csproj)
COPY . .

# Restore and publish
RUN dotnet restore Api/Api.csproj
RUN dotnet publish Api/Api.csproj -c Release -o /app /p:UseAppHost=false

# Stage 2: Runtime
FROM mcr.microsoft.com/dotnet/aspnet:8.0
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "Api.dll"]
