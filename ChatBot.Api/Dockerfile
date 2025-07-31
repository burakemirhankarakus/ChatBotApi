# Base image
FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS base
WORKDIR /app
EXPOSE 8080

# Build image
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

# Proje dosyasýný kopyala ve restore et
COPY ChatBot.Api.csproj ./
RUN dotnet restore ChatBot.Api.csproj

# Diðer tüm dosyalarý kopyala ve publish et
COPY . ./
RUN dotnet publish ChatBot.Api.csproj -c Release -o /app/publish

# Final image
FROM base AS final
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "ChatBot.Api.dll"]
