FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Copy csproj and restore
COPY ["ToDoApi/ToDoApi.csproj", "ToDoApi/"]
RUN dotnet restore "ToDoApi/ToDoApi.csproj"

# Copy everything and publish
COPY . .
WORKDIR /src/ToDoApi
RUN dotnet publish "ToDoApi.csproj" -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .

# Production environment
ENV ASPNETCORE_ENVIRONMENT=Production

# Render provides a $PORT env variable at runtime; default to 8080
EXPOSE 8080
ENTRYPOINT ["sh", "-c", "dotnet ToDoApi.dll --urls http://*:${PORT:-8080}"]
