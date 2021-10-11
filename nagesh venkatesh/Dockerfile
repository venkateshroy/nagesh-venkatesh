#See https://aka.ms/containerfastmode to understand how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80

FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build
WORKDIR /src
COPY ["nagesh venkatesh/nagesh venkatesh.csproj", "nagesh venkatesh/"]
RUN dotnet restore "nagesh venkatesh/nagesh venkatesh.csproj"
COPY . .
WORKDIR "/src/nagesh venkatesh"
RUN dotnet build "nagesh venkatesh.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "nagesh venkatesh.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "nagesh venkatesh.dll"]