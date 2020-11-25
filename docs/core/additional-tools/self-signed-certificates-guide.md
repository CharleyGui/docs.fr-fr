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
# <a name="generate-self-signed-certificates-with-the-net-cli"></a><span data-ttu-id="7243b-103">Générer des certificats auto-signés avec l’interface CLI .NET</span><span class="sxs-lookup"><span data-stu-id="7243b-103">Generate self-signed certificates with the .NET CLI</span></span>

<span data-ttu-id="7243b-104">Lorsque vous utilisez des certificats auto-signés, il existe différentes façons de les créer et de les utiliser pour les scénarios de développement et de test.</span><span class="sxs-lookup"><span data-stu-id="7243b-104">When using self-signed certificates, there's different ways to create and use them for development and testing scenarios.</span></span>  <span data-ttu-id="7243b-105">Dans ce guide, vous allez aborder l’utilisation de certificats auto-signés avec `dotnet dev-certs` , ainsi que d’autres options telles que `PowerShell` et `OpenSSL` .</span><span class="sxs-lookup"><span data-stu-id="7243b-105">In this guide, you'll cover using self-signed certificates with `dotnet dev-certs`, and other options like `PowerShell` and `OpenSSL`.</span></span>

<span data-ttu-id="7243b-106">Vous pouvez ensuite valider le chargement du certificat à l’aide d’un exemple tel qu’une [application ASP.net Core](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) hébergée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="7243b-106">You can then validate that the certificate will load using an example such as an [ASP.NET Core app](https://github.com/dotnet/dotnet-docker/blob/master/samples/run-aspnetcore-https-development.md) hosted in a container.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7243b-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="7243b-107">Prerequisites</span></span>

<span data-ttu-id="7243b-108">Dans l’exemple, vous pouvez utiliser `.netcore 3.1` ou `.net 5` .</span><span class="sxs-lookup"><span data-stu-id="7243b-108">In the sample, you can utilize either `.netcore 3.1` or `.net 5`.</span></span>

<span data-ttu-id="7243b-109">Pour `dotnet dev-certs` , assurez-vous que la version appropriée de est `dotnet` installée :</span><span class="sxs-lookup"><span data-stu-id="7243b-109">For `dotnet dev-certs`, be sure to have the appropriate version of `dotnet` installed:</span></span>

* [<span data-ttu-id="7243b-110">Installer dotnet sur Windows</span><span class="sxs-lookup"><span data-stu-id="7243b-110">Install dotnet on Windows</span></span>](../install/windows.md)
* [<span data-ttu-id="7243b-111">Installer dotnet sur Linux</span><span class="sxs-lookup"><span data-stu-id="7243b-111">Install dotnet on Linux</span></span>](../install/linux.md)
* [<span data-ttu-id="7243b-112">Installer dotnet sur macOS</span><span class="sxs-lookup"><span data-stu-id="7243b-112">Install dotnet on macOS</span></span>](../install/macos.md)

<span data-ttu-id="7243b-113">Cet exemple requiert l' [ancrage 17,06](https://docs.docker.com/release-notes/docker-ce) ou une version ultérieure du [client dockr](https://www.docker.com/products/docker).</span><span class="sxs-lookup"><span data-stu-id="7243b-113">This sample requires [Docker 17.06](https://docs.docker.com/release-notes/docker-ce) or later of the [Docker client](https://www.docker.com/products/docker).</span></span>

## <a name="prepare-sample-app"></a><span data-ttu-id="7243b-114">Préparer l’exemple d’application</span><span class="sxs-lookup"><span data-stu-id="7243b-114">Prepare sample app</span></span>

<span data-ttu-id="7243b-115">Vous devez préparer l’exemple d’application en fonction du runtime que vous souhaitez utiliser pour le test.</span><span class="sxs-lookup"><span data-stu-id="7243b-115">You'll need to prepare the sample app depending on which runtime you'd like to use for testing.</span></span>

<span data-ttu-id="7243b-116">Pour ce guide, vous allez utiliser un [exemple d’application](https://hub.docker.com/_/microsoft-dotnet-samples) et y apporter des modifications, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="7243b-116">For this guide, you'll be using a [sample app](https://hub.docker.com/_/microsoft-dotnet-samples) and make changes where appropriate.</span></span>

### <a name="prepare-net-core-31-sample-app"></a><span data-ttu-id="7243b-117">Préparer l’exemple d’application .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="7243b-117">Prepare .NET Core 3.1 sample app</span></span>

<span data-ttu-id="7243b-118">Obtenir l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="7243b-118">Get the sample app.</span></span>

```console
git clone https://github.com/dotnet/dotnet-docker/
```

<span data-ttu-id="7243b-119">Accédez au référentiel localement et ouvrez l’espace de travail dans un éditeur.</span><span class="sxs-lookup"><span data-stu-id="7243b-119">Navigate to the repository locally and open up the workspace in an editor.</span></span>

> [!NOTE]
> <span data-ttu-id="7243b-120">Si vous envisagez d’utiliser des paramètres de dotnet publish pour *réduire* le déploiement, vous devez vous assurer que les dépendances appropriées sont incluses pour la prise en charge des certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="7243b-120">If you're looking to use dotnet publish parameters to *trim* the deployment, you should make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="7243b-121">Mettez à jour le [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) pour vous assurer que les assemblys appropriés sont inclus dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="7243b-121">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="7243b-122">Pour référence, consultez Comment mettre à jour le fichier. csproj pour [prendre en charge les certificats SSL](../deploying/trim-self-contained.md#support-for-ssl-certificates) lors de l’utilisation du filtrage pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="7243b-122">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="7243b-123">Assurez-vous que le `aspnetapp.csproj` comprend le Framework cible approprié :</span><span class="sxs-lookup"><span data-stu-id="7243b-123">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>.netcoreapp3.1</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

<span data-ttu-id="7243b-124">Modifiez le fichier dockerfile pour vous assurer que le runtime pointe vers. Netcore 3,1 :</span><span class="sxs-lookup"><span data-stu-id="7243b-124">Modify the Dockerfile to make sure the runtime points to .netcore 3.1:</span></span>

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

<span data-ttu-id="7243b-125">Assurez-vous que vous pointez sur l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="7243b-125">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="7243b-126">Créez le conteneur pour le test local.</span><span class="sxs-lookup"><span data-stu-id="7243b-126">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

### <a name="prepare-net-5-sample-app"></a><span data-ttu-id="7243b-127">Préparer l’exemple d’application .NET 5</span><span class="sxs-lookup"><span data-stu-id="7243b-127">Prepare .NET 5 sample app</span></span>

<span data-ttu-id="7243b-128">Pour ce guide, l' [exemple de aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) doit être vérifié pour .net 5.</span><span class="sxs-lookup"><span data-stu-id="7243b-128">For this guide, the [sample aspnetapp](https://hub.docker.com/_/microsoft-dotnet-samples) should be checked for .net 5.</span></span>

<span data-ttu-id="7243b-129">Vérifiez que l’exemple d’application [fichier dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) utilise .net 5.</span><span class="sxs-lookup"><span data-stu-id="7243b-129">Check sample app [Dockerfile](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/Dockerfile) is using .net 5.</span></span>

<span data-ttu-id="7243b-130">Selon le système d’exploitation hôte, le runtime ASPNET devra peut-être être mis à jour.</span><span class="sxs-lookup"><span data-stu-id="7243b-130">Depending on the host os, the aspnet runtime may need to be updated.</span></span> <span data-ttu-id="7243b-131">Par exemple, le passage de la `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` valeur à `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` dans le fichier dockerfile permet de cibler le Windows Runtime approprié.</span><span class="sxs-lookup"><span data-stu-id="7243b-131">For example, changing from `mcr.microsoft.com/dotnet/aspnet:5.0-nanoservercore-2009 AS runtime` to `mcr.microsoft.com/dotnet/aspnet:5.0-windowsservercore-ltsc2019 AS runtime` in the Dockerfile will help with targeting the appropriate Windows runtime.</span></span>

<span data-ttu-id="7243b-132">Par exemple, cela vous aidera à tester les certificats sur Windows :</span><span class="sxs-lookup"><span data-stu-id="7243b-132">For example, this will help with testing the certificates on Windows:</span></span>

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

<span data-ttu-id="7243b-133">Si nous testons les certificats sur Linux, vous pouvez utiliser le fichier dockerfile existant.</span><span class="sxs-lookup"><span data-stu-id="7243b-133">If we're testing the certificates on Linux, you can use the existing Dockerfile.</span></span>

<span data-ttu-id="7243b-134">Assurez-vous que le `aspnetapp.csproj` comprend le Framework cible approprié :</span><span class="sxs-lookup"><span data-stu-id="7243b-134">Make sure the `aspnetapp.csproj` includes the appropriate target framework:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!--Other Properties-->
  </PropertyGroup>

</Project>
```

> [!NOTE]
> <span data-ttu-id="7243b-135">Si vous envisagez d’utiliser des paramètres de dotnet publish pour *réduire* le déploiement, vous devez vous assurer que les dépendances appropriées sont incluses pour la prise en charge des certificats SSL.</span><span class="sxs-lookup"><span data-stu-id="7243b-135">If you're looking to use dotnet publish parameters to *trim* the deployment, you should make sure that the appropriate dependencies are included for supporting SSL certificates.</span></span>
<span data-ttu-id="7243b-136">Mettez à jour le [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) pour vous assurer que les assemblys appropriés sont inclus dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="7243b-136">Update the [dotnet-docker\samples\aspnetapp\aspnetapp.csproj](https://github.com/dotnet/dotnet-docker/blob/master/samples/aspnetapp/aspnetapp/aspnetapp.csproj) to ensure that the appropriate assemblies are included in the container.</span></span> <span data-ttu-id="7243b-137">Pour référence, consultez Comment mettre à jour le fichier. csproj pour [prendre en charge les certificats SSL](../deploying/trim-self-contained.md#support-for-ssl-certificates) lors de l’utilisation du filtrage pour les déploiements autonomes.</span><span class="sxs-lookup"><span data-stu-id="7243b-137">For reference, check how to update the .csproj file to [support ssl certificates](../deploying/trim-self-contained.md#support-for-ssl-certificates) when using trimming for self-contained deployments.</span></span>

<span data-ttu-id="7243b-138">Assurez-vous que vous pointez sur l’exemple d’application.</span><span class="sxs-lookup"><span data-stu-id="7243b-138">Make sure you're pointing to the sample app.</span></span>

```console
cd .\dotnet-docker\samples\aspnetapp
```

<span data-ttu-id="7243b-139">Créez le conteneur pour le test local.</span><span class="sxs-lookup"><span data-stu-id="7243b-139">Build the container for testing locally.</span></span>

```console
docker build -t aspnetapp:my-sample -f Dockerfile .
```

## <a name="create-a-self-signed-certificate-with-dotnet-dev-certs"></a><span data-ttu-id="7243b-140">Créer un certificat auto-signé avec dotnet dev-certs</span><span class="sxs-lookup"><span data-stu-id="7243b-140">Create a self-signed certificate with dotnet dev-certs</span></span>

<span data-ttu-id="7243b-141">Vous pouvez utiliser `dotnet dev-certs` pour travailler avec des certificats auto-signés.</span><span class="sxs-lookup"><span data-stu-id="7243b-141">You can use `dotnet dev-certs` to work with self-signed certificates.</span></span> <span data-ttu-id="7243b-142">Cet exemple utilise une console PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7243b-142">This example uses a PowerShell console.</span></span>

```console
dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\https\aspnetapp.pfx -p crypticpassword
dotnet dev-certs https --trust
```

> [!NOTE]
> <span data-ttu-id="7243b-143">Dans ce cas, le nom du certificat *aspnetapp*. pfx doit correspondre au nom de l’assembly du projet.</span><span class="sxs-lookup"><span data-stu-id="7243b-143">The certificate name, in this case *aspnetapp*.pfx must match the project assembly name.</span></span> <span data-ttu-id="7243b-144">`crypticpassword` est utilisé comme un mot de passe pour un mot de passe de votre choix.</span><span class="sxs-lookup"><span data-stu-id="7243b-144">`crypticpassword` is used as a stand-in for a password of your own choosing.</span></span> <span data-ttu-id="7243b-145">Si la console retourne « un certificat HTTPs valide est déjà présent. », il existe déjà un certificat approuvé dans votre magasin.</span><span class="sxs-lookup"><span data-stu-id="7243b-145">If console returns "A valid HTTPS certificate is already present.", a trusted certificate already exists in your store.</span></span> <span data-ttu-id="7243b-146">Elle peut être exportée à l’aide de la console MMC.</span><span class="sxs-lookup"><span data-stu-id="7243b-146">It can be exported using MMC Console.</span></span>

<span data-ttu-id="7243b-147">Configurez les secrets d’application pour le certificat :</span><span class="sxs-lookup"><span data-stu-id="7243b-147">Configure application secrets, for the certificate:</span></span>

```console
dotnet user-secrets -p aspnetapp\aspnetapp.csproj set "Kestrel:Certificates:Development:Password" "crypticpassword"
```

> [!NOTE]
> <span data-ttu-id="7243b-148">Remarque : le mot de passe doit correspondre au mot de passe utilisé pour le certificat.</span><span class="sxs-lookup"><span data-stu-id="7243b-148">Note: The password must match the password used for the certificate.</span></span>

<span data-ttu-id="7243b-149">Exécutez l’image de conteneur avec ASP.NET Core configuré pour le protocole HTTPs :</span><span class="sxs-lookup"><span data-stu-id="7243b-149">Run the container image with ASP.NET Core configured for HTTPS:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:C:\Users\ContainerUser\AppData\Roaming\microsoft\UserSecrets -v $env:USERPROFILE\.aspnet\https:C:\Users\ContainerUser\AppData\Roaming\ASP.NET\Https mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="7243b-150">Une fois l’application démarrée, accédez à `https://localhost:8001` dans votre navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="7243b-150">Once the application starts, navigate to `https://localhost:8001` in your web browser.</span></span>

### <a name="clean-up"></a><span data-ttu-id="7243b-151">Nettoyage</span><span class="sxs-lookup"><span data-stu-id="7243b-151">Clean up</span></span>

<span data-ttu-id="7243b-152">Si les secrets et les certificats ne sont pas utilisés, veillez à les nettoyer.</span><span class="sxs-lookup"><span data-stu-id="7243b-152">If the secrets and certificates are not in use, be sure to clean them up.</span></span>

```console
dotnet user-secrets remove "Kestrel:Certificates:Development:Password" -p aspnetapp\aspnetapp.csproj
dotnet dev-certs https --clean
```

## <a name="create-a-self-signed-certificate-with-powershell"></a><span data-ttu-id="7243b-153">Créer un certificat auto-signé avec PowerShell</span><span class="sxs-lookup"><span data-stu-id="7243b-153">Create a self-signed certificate with PowerShell</span></span>

<span data-ttu-id="7243b-154">Vous pouvez utiliser PowerShell pour générer des certificats auto-signés.</span><span class="sxs-lookup"><span data-stu-id="7243b-154">You can use PowerShell to generate self-signed certificates.</span></span> <span data-ttu-id="7243b-155">Le [client PKI](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps&preserver-view=true) peut être utilisé pour générer un certificat auto-signé.</span><span class="sxs-lookup"><span data-stu-id="7243b-155">The [PKI Client](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps&preserver-view=true) can be used to generate a self-signed certificate.</span></span>

```powershell
$cert = New-SelfSignedCertificate -DnsName @("contoso.com", "www.contoso.com") -CertStoreLocation "cert:\LocalMachine\My"
```

<span data-ttu-id="7243b-156">Le certificat est généré, mais pour les besoins du test, il doit être placé dans un magasin de certificats à des fins de test dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="7243b-156">The certificate will be generated, but for the purposes of testing, should be placed in a cert store for testing in a browser.</span></span>

```powershell
$certKeyPath = "c:\certs\contoso.com.pfx"
$password = ConvertTo-SecureString 'password' -AsPlainText -Force
$cert | Export-PfxCertificate -FilePath $certKeyPath -Password $password
$rootCert = $(Import-PfxCertificate -FilePath $certKeyPath -CertStoreLocation 'Cert:\LocalMachine\Root' -Password $password)
```

<span data-ttu-id="7243b-157">À ce stade, les certificats doivent être affichables à partir d’un [composant logiciel enfichable MMC](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="7243b-157">At this point, the certificates should be viewable from an [MMC snap-in](../../framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>

<span data-ttu-id="7243b-158">Vous pouvez exécuter l’exemple de conteneur dans le sous-système Windows pour Linux (WSL) :</span><span class="sxs-lookup"><span data-stu-id="7243b-158">You can run the sample container in Windows Subsystem for Linux (WSL):</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="7243b-159">Notez qu’avec le montage de volume, le chemin d’accès du fichier peut être géré différemment en fonction de l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="7243b-159">Note that with the volume mount the file path could be handled differently based on host.</span></span>  <span data-ttu-id="7243b-160">Par exemple, dans WSL, nous pouvons remplacer */c/certs* par */mnt/c/certs*.</span><span class="sxs-lookup"><span data-stu-id="7243b-160">For example, in WSL we may replace */c/certs* with */mnt/c/certs*.</span></span>

<span data-ttu-id="7243b-161">Si vous utilisez le conteneur créé précédemment pour Windows, la commande exécuter se présenterait comme suit :</span><span class="sxs-lookup"><span data-stu-id="7243b-161">If you're using the container built earlier for Windows, the run command would look like the following:</span></span>

```console
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="7243b-162">Une fois l’application terminée, accédez à contoso.com :8001 dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="7243b-162">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="7243b-163">Assurez-vous que les entrées de l’hôte sont mises à jour pour `contoso.com` répondre à l’adresse IP appropriée (par exemple, 127.0.0.1).</span><span class="sxs-lookup"><span data-stu-id="7243b-163">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="7243b-164">Si le certificat n’est pas reconnu, assurez-vous que le certificat chargé avec le conteneur est également approuvé sur l’hôte, et qu’il existe des entrées SAN/DNS appropriées pour `contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="7243b-164">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

### <a name="clean-up"></a><span data-ttu-id="7243b-165">Nettoyage</span><span class="sxs-lookup"><span data-stu-id="7243b-165">Clean up</span></span>

```powershell
$cert | Remove-Item
Get-ChildItem $certFilePath | Remove-Item
$rootCert | Remove-item
```

## <a name="create-a-self-signed-certificate-with-openssl"></a><span data-ttu-id="7243b-166">Créer un certificat auto-signé avec OpenSSL</span><span class="sxs-lookup"><span data-stu-id="7243b-166">Create a self-signed certificate with OpenSSL</span></span>

<span data-ttu-id="7243b-167">Vous pouvez utiliser [OpenSSL](https://www.openssl.org/) pour créer des certificats auto-signés.</span><span class="sxs-lookup"><span data-stu-id="7243b-167">You can use [OpenSSL](https://www.openssl.org/) to create self-signed certificates.</span></span> <span data-ttu-id="7243b-168">Cet exemple utilise WSL/Ubuntu et un interpréteur de commandes bash avec `OpenSSL` .</span><span class="sxs-lookup"><span data-stu-id="7243b-168">This example will use WSL / Ubuntu and a bash shell with `OpenSSL`.</span></span>

<span data-ttu-id="7243b-169">Cela génère un. CRT et une. Key.</span><span class="sxs-lookup"><span data-stu-id="7243b-169">This will generate a .crt and a .key.</span></span>

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

<span data-ttu-id="7243b-170">Pour obtenir un fichier. pfx, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7243b-170">To get a .pfx, use the following command:</span></span>

```bash
openssl pkcs12 -export -out $PARENT.pfx -inkey $PARENT.key -in $PARENT.crt
```

> [!NOTE]
> <span data-ttu-id="7243b-171">L’exemple. aspnetcore 3,1 utilise `.pfx` et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="7243b-171">The .aspnetcore 3.1 example will use `.pfx` and a password.</span></span> <span data-ttu-id="7243b-172">À compter du `.net 5` Runtime, Kestrel peut également prendre des `.crt` fichiers et encodés au format PEM `.key` .</span><span class="sxs-lookup"><span data-stu-id="7243b-172">Starting with the `.net 5` runtime, Kestrel can also take `.crt` and PEM-encoded `.key` files.</span></span>

<span data-ttu-id="7243b-173">Selon le système d’exploitation hôte, le certificat doit être approuvé.</span><span class="sxs-lookup"><span data-stu-id="7243b-173">Depending on the host os, the certificate will need to be trusted.</span></span> <span data-ttu-id="7243b-174">Sur un hôte Linux, « approuvant » le certificat est différent et distribution dépendant.</span><span class="sxs-lookup"><span data-stu-id="7243b-174">On a Linux host, 'trusting' the certificate is different and distro dependent.</span></span>

<span data-ttu-id="7243b-175">Dans le cadre de ce guide, voici un exemple de Windows utilisant PowerShell :</span><span class="sxs-lookup"><span data-stu-id="7243b-175">For the purposes of this guide, here's an example in Windows using PowerShell:</span></span>

```powershell
Import-Certificate -FilePath $certFilePath -CertStoreLocation 'Cert:\LocalMachine\Root'
```

<span data-ttu-id="7243b-176">Pour .NET Core 3,1, exécutez la commande suivante dans WSL :</span><span class="sxs-lookup"><span data-stu-id="7243b-176">For .NET Core 3.1, run the following command in WSL:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.pfx -v /c/path/to/certs/:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

<span data-ttu-id="7243b-177">À compter de .NET 5, Kestrel peut prendre les `.crt` fichiers et codés en PEM `.key` .</span><span class="sxs-lookup"><span data-stu-id="7243b-177">Starting with .NET 5, Kestrel can take the `.crt` and PEM-encoded `.key` files.</span></span> <span data-ttu-id="7243b-178">Vous pouvez exécuter l’exemple avec la commande suivante pour .NET 5 :</span><span class="sxs-lookup"><span data-stu-id="7243b-178">You can run the sample with the following command for .NET 5:</span></span>

```bash
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=/https/contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=/https/contoso.com.key -v /c/path/to/certs:/https/ mcr.microsoft.com/dotnet/samples:aspnetapp
```

> [!NOTE]
> <span data-ttu-id="7243b-179">Notez que, dans WSL, le chemin de montage du volume peut changer en fonction de la configuration.</span><span class="sxs-lookup"><span data-stu-id="7243b-179">Note that in WSL, the volume mount path may change depending on the configuration.</span></span>

<span data-ttu-id="7243b-180">Pour .NET Core 3,1 dans Windows, exécutez la commande suivante dans `Powershell` :</span><span class="sxs-lookup"><span data-stu-id="7243b-180">For .NET Core 3.1 in Windows, run the following command in `Powershell`:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Password="password" -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.pfx -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="7243b-181">Pour .NET 5 dans Windows, exécutez la commande suivante dans PowerShell :</span><span class="sxs-lookup"><span data-stu-id="7243b-181">For .NET 5 in Windows, run the following command in PowerShell:</span></span>

```powershell
docker run --rm -it -p 8000:80 -p 8001:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8001 -e ASPNETCORE_ENVIRONMENT=Development -e ASPNETCORE_Kestrel__Certificates__Default__Path=c:\https\contoso.com.crt -e ASPNETCORE_Kestrel__Certificates__Default__KeyPath=c:\https\contoso.com.key -v c:\certs:C:\https aspnetapp:my-sample
```

<span data-ttu-id="7243b-182">Une fois l’application terminée, accédez à contoso.com :8001 dans un navigateur.</span><span class="sxs-lookup"><span data-stu-id="7243b-182">Once the application is up, navigate to contoso.com:8001 in a browser.</span></span>

<span data-ttu-id="7243b-183">Assurez-vous que les entrées de l’hôte sont mises à jour pour `contoso.com` répondre à l’adresse IP appropriée (par exemple, 127.0.0.1).</span><span class="sxs-lookup"><span data-stu-id="7243b-183">Be sure that the host entries are updated for `contoso.com` to answer on  the appropriate ip address (for example 127.0.0.1).</span></span> <span data-ttu-id="7243b-184">Si le certificat n’est pas reconnu, assurez-vous que le certificat chargé avec le conteneur est également approuvé sur l’hôte, et qu’il existe des entrées SAN/DNS appropriées pour `contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="7243b-184">If the certificate isn't recognized, make sure that the certificate that is loaded with the container is also trusted on the host, and that there's appropriate SAN / DNS entries for `contoso.com`.</span></span>

### <a name="clean-up"></a><span data-ttu-id="7243b-185">Nettoyage</span><span class="sxs-lookup"><span data-stu-id="7243b-185">Clean up</span></span>

<span data-ttu-id="7243b-186">Veillez à nettoyer les certificats auto-signés une fois le test terminé.</span><span class="sxs-lookup"><span data-stu-id="7243b-186">Be sure to clean up the self-signed certificates once done testing.</span></span>

```powershell
Get-ChildItem $certFilePath | Remove-Item
```
