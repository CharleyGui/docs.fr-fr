---
title: Vue d’ensemble de la génération de certificats Self-Signed
description: Vue d’ensemble de l’outil Microsoft dotnet dev-certs qui ajoute des fonctionnalités pour les projets .NET Core et ASP.NET Core, ainsi que d’autres options pour l’utilisation de certificats auto-signés.
author: angee
ms.date: 11/19/2020
ms.openlocfilehash: 15bbe3997ca34b503074595fa027bc6dfff1c0a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760911"
---
# <a name="generate-self-signed-certificates-with-the-net-cli"></a>Générer des certificats auto-signés avec l’interface CLI .NET

Lorsque vous utilisez des certificats auto-signés, il existe différentes façons de les créer et de les utiliser pour les scénarios de développement et de test.  Dans ce guide, vous allez aborder l’utilisation de certificats auto-signés avec `dotnet dev-certs` , ainsi que d’autres options telles que `PowerShell` et `OpenSSL` .

Vous pouvez ensuite valider le chargement du certificat à l’aide d’un exemple tel qu’une [application ASP.net Core](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) hébergée dans un conteneur.

## <a name="prerequisites"></a>Prérequis

Dans l’exemple, vous pouvez utiliser `.netcore 3.1` ou `.net 5` .

Pour `dotnet dev-certs` , assurez-vous que la version appropriée de est `dotnet` installée :

* [Installer dotnet sur Windows](../install/windows.md)
* [Installer dotnet sur Linux](../install/linux.md)
* [Installer dotnet sur macOS](../install/macos.md)

Cet exemple requiert l' [ancrage 17,06](https://docs.docker.com/release-notes/docker-ce) ou une version ultérieure du [client dockr](https://www.docker.com/products/docker).

## <a name="prepare-sample-app"></a>Préparer l’exemple d’application

Vous devez préparer l’exemple d’application en fonction du runtime que vous souhaitez utiliser pour le test.

Pour ce guide, vous allez utiliser un [exemple d’application](https://hub.docker.com/_/microsoft-dotnet-samples) et y apporter des modifications, le cas échéant.

### <a name="prepare-net-core-31-sample-app"></a>Préparer l’exemple d’application .NET Core 3,1

Obtenir l’exemple d’application.

```console
git clone https://github.com/dotnet/dotnet-docker/
```

Accédez au référentiel localement et ouvrez l’espace de travail dans un éditeur.

> [!NOTE]
> Si vous envisagez d’utiliser des paramètres de dotnet publish pour *réduire* le déploiement, vous devez vous assurer que les dépendances appropriées sont incluses pour la prise en charge des certificats SSL.
Mettez à jour le [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) pour vous assurer que les assemblys appropriés sont inclus dans le conteneur. Pour référence, consultez Comment mettre à jour le fichier. csproj pour [prendre en charge les certificats SSL](../deploying/trim-self-contained.md#support-for-ssl-certificates) lors de l’utilisation du filtrage pour les déploiements autonomes.

Assurez-vous que le `aspnetapp.csproj` comprend le Framework cible approprié :

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

Modifiez le fichier dockerfile pour vous assurer que le runtime pointe vers. Netcore 3,1 :

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet-core
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app --no-restore

# final stage/image
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["dotnet", "aspnetapp.dll"]
```

Assurez-vous que vous pointez sur l’exemple d’application.

```console
cd .\dotnet-docker\samples\aspnetapp
```

Créez le conteneur pour le test local.

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="prepare-net-5-sample-app"></a>Préparer l’exemple d’application .NET 5

Pour ce guide, l' [exemple de aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) doit être vérifié pour .net 5.

Vérifiez que l’exemple d’application [fichier dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) utilise .net 5.

Selon le système d’exploitation hôte, le runtime ASPNET devra peut-être être mis à jour. Par exemple, le passage de la `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` valeur à `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` dans le fichier dockerfile permet de cibler le Windows Runtime approprié.

Par exemple, cela vous aidera à tester les certificats sur Windows :

```Dockerfile
# https://hub.docker.com/_/microsoft-dotnet
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /source

# copy csproj and restore as distinct layers
COPY *.sln .
COPY aspnetapp/*.csproj ./aspnetapp/
RUN dotnet restore -r win-x64

# copy everything else and build app
COPY aspnetapp/. ./aspnetapp/
WORKDIR /source/aspnetapp
RUN dotnet publish -c release -o /app -r win-x64 --self-contained false --no-restore

# final stage/image
# Uses the 2009 release; 2004, 1909, and 1809 are other choices
FROM mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime
WORKDIR /app
COPY --from=build /app ./
ENTRYPOINT ["aspnetapp"]

```

Si nous testons les certificats sur Linux, vous pouvez utiliser le fichier dockerfile existant.

Assurez-vous que le `aspnetapp.csproj` comprend le Framework cible approprié :

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> Si vous envisagez d’utiliser des paramètres de dotnet publish pour *réduire* le déploiement, vous devez vous assurer que les dépendances appropriées sont incluses pour la prise en charge des certificats SSL.
Mettez à jour le [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) pour vous assurer que les assemblys appropriés sont inclus dans le conteneur. Pour référence, consultez Comment mettre à jour le fichier. csproj pour [prendre en charge les certificats SSL](../deploying/trim-self-contained.md#support-for-ssl-certificates) lors de l’utilisation du filtrage pour les déploiements autonomes.

Assurez-vous que vous pointez sur l’exemple d’application.

```console
cd .\dotnet-docker\samples\aspnetapp
```

Créez le conteneur pour le test local.

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate-with-dotnet-dev-certs"></a>Créer un certificat auto-signé avec dotnet dev-certs

Vous pouvez utiliser `dotnet dev-certs` pour travailler avec des certificats auto-signés. Cet exemple utilise une console PowerShell.

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> Dans ce cas, le nom du certificat *aspnetapp*. pfx doit correspondre au nom de l’assembly du projet. `crypticpassword` est utilisé comme un mot de passe pour un mot de passe de votre choix. Si la console retourne « un certificat HTTPs valide est déjà présent. », il existe déjà un certificat approuvé dans votre magasin. Elle peut être exportée à l’aide de la console MMC.

Configurez les secrets d’application pour le certificat :

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> Remarque : le mot de passe doit correspondre au mot de passe utilisé pour le certificat.

Exécutez l’image de conteneur avec ASP.NET Core configuré pour le protocole HTTPs :

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

Une fois l’application démarrée, accédez à `https://localhost:8001` dans votre navigateur Web.

### <a name="clean-up"></a>Nettoyage

Si les secrets et les certificats ne sont pas utilisés, veillez à les nettoyer.

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

## <a name="create-a-self-signed-certificate-with-powershell"></a>Créer un certificat auto-signé avec PowerShell

Vous pouvez utiliser PowerShell pour générer des certificats auto-signés. Le [client PKI](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps&preserver-view=true) peut être utilisé pour générer un certificat auto-signé.

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

Le certificat est généré, mais pour les besoins du test, il doit être placé dans un magasin de certificats à des fins de test dans un navigateur.

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

À ce stade, les certificats doivent être affichables à partir d’un [composant logiciel enfichable MMC](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).

Vous pouvez exécuter l’exemple de conteneur dans le sous-système Windows pour Linux (WSL) :

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> Notez qu’avec le montage de volume, le chemin d’accès du fichier peut être géré différemment en fonction de l’ordinateur hôte.  Par exemple, dans WSL, nous pouvons remplacer */c/certs* par */mnt/c/certs*.

Si vous utilisez le conteneur créé précédemment pour Windows, la commande exécuter se présenterait comme suit :

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

Une fois l’application terminée, accédez à contoso.com :8001 dans un navigateur.

Assurez-vous que les entrées de l’hôte sont mises à jour pour `contoso.com` répondre à l’adresse IP appropriée (par exemple, 127.0.0.1). Si le certificat n’est pas reconnu, assurez-vous que le certificat chargé avec le conteneur est également approuvé sur l’hôte, et qu’il existe des entrées SAN/DNS appropriées pour `contoso.com` .

### <a name="clean-up"></a>Nettoyage

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

## <a name="create-a-self-signed-certificate-with-openssl"></a>Créer un certificat auto-signé avec OpenSSL

Vous pouvez utiliser [OpenSSL](https://www.openssl.org/) pour créer des certificats auto-signés. Cet exemple utilise WSL/Ubuntu et un interpréteur de commandes bash avec `OpenSSL` .

Cela génère un. CRT et une. Key.

```bash
PARENT="contoso.com"
openssl req \
-x509 \
-newkey rsa:4096 \
-sha256 \
-days 365 \
-nodes \
-keyout $PARENT.key \
-out $PARENT.crt \
-subj "/CN=${PARENT}" \
-extensions v3_ca \
-extensions v3_req \
-config <( \
  echo '[req]'; \
  echo 'default_bits= 4096'; \
  echo 'distinguished_name=req'; \
  echo 'x509_extension = v3_ca'; \
  echo 'req_extensions = v3_req'; \
  echo '[v3_req]'; \
  echo 'basicConstraints = CA:FALSE'; \
  echo 'keyUsage = nonRepudiation, digitalSignature, keyEncipherment'; \
  echo 'subjectAltName = @alt_names'; \
  echo '[ alt_names ]'; \
  echo "DNS.1 = www.${PARENT}"; \
  echo "DNS.2 = ${PARENT}"; \
  echo '[ v3_ca ]'; \
  echo 'subjectKeyIdentifier=hash'; \
  echo 'authorityKeyIdentifier=keyid:always,issuer'; \
  echo 'basicConstraints = critical, CA:TRUE, pathlen:0'; \
  echo 'keyUsage = critical, cRLSign, keyCertSign'; \
  echo 'extendedKeyUsage = serverAuth, clientAuth')

openssl x509 -noout -text -in $PARENT.crt
```

Pour obtenir un fichier. pfx, utilisez la commande suivante :

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> L’exemple. aspnetcore 3,1 utilise `.pfx` et un mot de passe. À compter du `.net 5` Runtime, Kestrel peut également prendre des `.crt` fichiers et encodés au format PEM `.key` .

Selon le système d’exploitation hôte, le certificat doit être approuvé. Sur un hôte Linux, « approuvant » le certificat est différent et distribution dépendant.

Dans le cadre de ce guide, voici un exemple de Windows utilisant PowerShell :

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

Pour .NET Core 3,1, exécutez la commande suivante dans WSL :

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

À compter de .NET 5, Kestrel peut prendre les `.crt` fichiers et codés en PEM `.key` . Vous pouvez exécuter l’exemple avec la commande suivante pour .NET 5 :

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> Notez que, dans WSL, le chemin de montage du volume peut changer en fonction de la configuration.

Pour .NET Core 3,1 dans Windows, exécutez la commande suivante dans `Powershell` :

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

Pour .NET 5 dans Windows, exécutez la commande suivante dans PowerShell :

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

Une fois l’application terminée, accédez à contoso.com :8001 dans un navigateur.

Assurez-vous que les entrées de l’hôte sont mises à jour pour `contoso.com` répondre à l’adresse IP appropriée (par exemple, 127.0.0.1). Si le certificat n’est pas reconnu, assurez-vous que le certificat chargé avec le conteneur est également approuvé sur l’hôte, et qu’il existe des entrées SAN/DNS appropriées pour `contoso.com` .

### <a name="clean-up"></a>Nettoyage

Veillez à nettoyer les certificats auto-signés une fois le test terminé.

```powershell
Get-ChildItem $certFilePath | Remove-Item
```
