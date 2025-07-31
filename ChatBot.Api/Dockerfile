# Base image
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 8080

# Build image
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Proje dizinine geç ve .csproj dosyasini kopyala
COPY ChatBot.Api/ChatBot.Api.csproj ChatBot.Api/
WORKDIR /src/ChatBot.Api
RUN dotnet restore

# Tüm dosyalari kopyala ve publish et
COPY ChatBot.Api/. ./
RUN dotnet publish -c Release -o /app/publish

# Final image
FROM base AS final
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "ChatBot.Api.dll"]
