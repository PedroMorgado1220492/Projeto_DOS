FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY ["RestaurantReservations.API.csproj", "."]
RUN dotnet restore "RestaurantReservations.API.csproj"
COPY . .
RUN dotnet build "RestaurantReservations.API.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "RestaurantReservations.API.csproj" -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "RestaurantReservations.API.dll"]