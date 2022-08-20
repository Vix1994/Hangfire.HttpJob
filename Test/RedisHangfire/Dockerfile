FROM Uchi-docker.pkg.coding.net/kirby-island/image/dotnet-sdk:6.0 AS build-env

COPY . ./

WORKDIR ./Test/RedisHangfire

# Compile
RUN dotnet publish -f net6.0 -r linux-x64 --self-contained=false -o publish

FROM Uchi-docker.pkg.coding.net/kirby-island/image/dotnet-aspnet:6.0

# Copy
COPY --from=build-env /Test/RedisHangfire/publish /dotnetapp

WORKDIR /dotnetapp

CMD ["dotnet", "RedisHangfire.dll", "--urls", "http://0.0.0.0:80"]