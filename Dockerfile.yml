FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src
COPY . ./
RUN dotnet restore "Whatsapp-Business-Cloud-Api-Net.sln"
RUN dotnet publish "Samples/WhatsAppBusinessCloudAPI.Sample/WhatsAppBusinessCloudAPI.Sample.csproj" -c Release -o /app/publish --no-restore

FROM mcr.microsoft.com/dotnet/aspnet:8.0 AS final
WORKDIR /app
COPY --from=build /app/publish ./
ENV ASPNETCORE_URLS=http://+:8080
EXPOSE 8080
ENTRYPOINT ["dotnet", "WhatsAppBusinessCloudAPI.Sample.dll"]
