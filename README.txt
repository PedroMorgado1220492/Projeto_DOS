

Para executar a API:

cd "C:\Users\utilizador\Documents\CTESP\3semestre\Trabalho_DOS\Projeto_DOS-1\RestaurantReservations\src\RestaurantReservations.API"
dotnet run
Acessar: http://localhost:5188/swagger

Para executar testes:

cd "C:\Users\utilizador\Documents\CTESP\3semestre\Trabalho_DOS\Projeto_DOS-1\RestaurantReservations\tests\RestaurantReservations.UnitTests"
dotnet test

Para verificar Docker:
cd "C:\Users\utilizador\Documents\CTESP\3semestre\Trabalho_DOS\Projeto_DOS-1\RestaurantReservations"
docker-compose up -d sqlserver


json para POST no Swagger UI:

{
  "customerName": "Pedro Morgado",
  "reservationDate": "2026-01-15T00:00:00",
  "reservationTime": "19:30:00",
  "tableNumber": 5,
  "numberOfPeople": 4
}

{
  "customerName": "Miguel Ramos",
  "reservationDate": "2026-01-16T00:00:00",
  "reservationTime": "20:00:00",
  "tableNumber": 3,
  "numberOfPeople": 2
}

{
  "customerName": "Vitor Armando",
  "reservationDate": "2026	-01-18T00:00:00",
  "reservationTime": "13:00:00",
  "tableNumber": 8,
  "numberOfPeople": 6
}