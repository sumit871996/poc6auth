FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS initial
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk AS build

WORKDIR '/app/src'

COPY ["JWTAuth_Validation.csproj" ,"."]

RUN dotnet restore "JWTAuth_Validation.csproj"

COPY . .

RUN dotnet build "JWTAuth_Validation.csproj" -o '/app/src/app/build/'

RUN dotnet publish "JWTAuth_Validation.csproj" -o '/app/src/app/publish/'

FROM initial AS final
WORKDIR '/app'
COPY --from=build '/app/src/app/publish/' .
CMD ["dotnet", "JWTAuth_Validation.dll"]