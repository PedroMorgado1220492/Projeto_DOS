# Estágio 1: BUILD - Usa SDK para compilar
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

# Copia ficheiro do projeto primeiro (para otimização de cache)
COPY ["src/RestaurantReservations.API/RestaurantReservations.API.csproj", "src/RestaurantReservations.API/"]
RUN dotnet restore "src/RestaurantReservations.API/RestaurantReservations.API.csproj"

# Copia resto do código e compila
COPY . .
WORKDIR "/src/src/RestaurantReservations.API"
RUN dotnet build "RestaurantReservations.API.csproj" -c Release -o /app/build

# Estágio 2: PUBLISH - Cria distribuição otimizada
FROM build AS publish
RUN dotnet publish "RestaurantReservations.API.csproj" -c Release -o /app/publish

# Estágio 3: RUNTIME - Imagem final leve
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS final
WORKDIR /app

#  CONFIGURAÇÕES CRÍTICAS
# 1. Ambiente Development para Swagger
ENV ASPNETCORE_ENVIRONMENT=Development
# 2. Escuta apenas HTTP na porta 8080
ENV ASPNETCORE_URLS=http://*:8080
ENV ASPNETCORE_HTTP_PORTS=8080
# 3. Desativa HTTPS completamente
ENV ASPNETCORE_Kestrel__Certificates__Default__Path=""

# Expõe porta
EXPOSE 8080

# Copia ficheiros publicados
COPY --from=publish /app/publish .

# Comando de entrada
ENTRYPOINT ["dotnet", "RestaurantReservations.API.dll"]