---
title: Magasin de packages de runtime
description: Découvrez comment utiliser le magasin de packages de runtime et les manifestes cibles utilisés par .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: e9e27ef535dbd9e7197c323f7e49a9960aeff0f9
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608360"
---
# <a name="runtime-package-store"></a>Magasin de packages de runtime

À compter de .NET Core 2.0, vous pouvez empaqueter et déployer des applications sur un jeu connu de packages qui existent dans l’environnement cible. Les avantages sont une accélération des déploiements, une utilisation réduite de l’espace disque et une amélioration du niveau de performance du démarrage dans certains cas.

Cette fonctionnalité est implémentée en tant que *magasin de packages de runtime*, qui est un répertoire sur le disque où sont stockés les packages (généralement */usr/local/share/dotnet/store* sur macOS/Linux et *C:/Program Files/dotnet/store* sur Windows). Ce répertoire contient des sous-répertoires pour les architectures et les [frameworks cibles](../../standard/frameworks.md). La disposition de fichier est similaire à la [disposition des composants NuGet sur le disque](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure) :

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

Un fichier *manifeste cible* liste les packages dans le magasin de packages de runtime. Les développeurs peuvent cibler ce manifeste quand ils publient leur application. Le manifeste cible est généralement fourni par le propriétaire de l’environnement de production ciblé.

## <a name="preparing-a-runtime-environment"></a>Préparation d’un environnement d’exécution

L’administrateur d’un environnement d’exécution peut optimiser les applications afin qu’elles se déploient plus rapidement et qu’elles utilisent moins d’espace disque en créant un magasin de packages de runtime et le manifeste cible correspondant.

La première étape consiste à créer un *manifeste de magasin de packages* listant les packages qui composent le magasin de packages de runtime. Ce format de fichier est compatible avec le format de fichier projet (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Exemple**

L’exemple de manifeste de magasin de packages suivant (*packages.csproj*) est utilisé pour ajouter [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) et [`Moq`](https://www.nuget.org/packages/moq/) à un magasin de packages de runtime :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Approvisionner le magasin de packages de runtime en exécutant `dotnet store` avec le manifeste de magasin de packages, le runtime et le framework :

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Exemple**

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Vous pouvez passer plusieurs chemins d’accès de manifeste de magasin de packages cibles à une seule [`dotnet store`](../tools/dotnet-store.md) commande en répétant l’option et le chemin d’accès dans la commande.

Par défaut, la sortie de la commande est un magasin de packages sous le sous-répertoire *.dotnet/store* du profil de l’utilisateur. Vous pouvez spécifier un autre emplacement à l’aide de l’option `--output <OUTPUT_DIRECTORY>`. Le répertoire racine du magasin contient un fichier manifeste cible *artifact.xml*. Ce fichier peut être mis à disposition en téléchargement et servir aux auteurs d’application qui souhaitent cibler ce magasin au moment de la publication.

**Exemple**

Le fichier *artifact.xml* suivant est issu de l’exécution de l’exemple précédent. Notez que [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) est une dépendance de `Moq` , donc elle est incluse automatiquement et apparaît dans le fichier manifeste *artifacts.xml* .

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Publication d’une application par rapport à un manifeste cible

Si vous avez un fichier manifeste cible sur le disque, vous spécifiez le chemin d’accès au fichier lors de la publication de votre application à l’aide de la [`dotnet publish`](../tools/dotnet-publish.md) commande :

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Exemple**

```dotnetcli
dotnet publish --manifest manifest.xml
```

Vous déployez l’application publiée résultante sur un environnement qui détient les packages décrits dans le manifeste cible. En cas d’échec, l’application ne parvient pas à démarrer.

Spécifiez plusieurs manifestes cible quand vous publiez une application en répétant l’option et le chemin (par exemple, `--manifest manifest1.xml --manifest manifest2.xml`). Ainsi, l’application est épurée pour réunir les packages spécifiés dans les fichiers manifeste cibles fournis à la commande.

Si vous déployez une application et que le déploiement comprend une dépendance de manifeste (l’assembly est présent dans le dossier *bin*), le magasin de packages de runtime *n’est pas utilisé* sur l’hôte pour cet assembly. L’assembly dans le dossier *bin* est utilisé indépendamment de sa présence dans le magasin de packages de runtime sur l’hôte.

La version de la dépendance indiquée dans le manifeste doit correspondre à la version de la dépendance dans le magasin de packages de runtime. Si la dépendance dans le manifeste cible et la version présente dans le magasin de packages de runtime sont incompatibles et que le déploiement de l’application n’inclut pas la version du package requise, l’application ne démarre pas. L’exception contient le nom du manifeste cible qui a appelé l’assembly du magasin de packages de runtime, ce qui vous permet de résoudre l’incompatibilité.

Quand le déploiement est *épuré* à la publication, seules les versions spécifiques des packages de manifestes que vous indiquez sont retirées de la sortie publiée. Les packages aux versions indiquées doivent être présents sur l’hôte pour que l’application démarre.

## <a name="specifying-target-manifests-in-the-project-file"></a>Spécification de manifestes cibles dans le fichier projet

Une alternative à la spécification de manifestes cibles à l’aide de la [`dotnet publish`](../tools/dotnet-publish.md) commande consiste à les spécifier dans le fichier projet sous la forme d’une liste de chemins séparés par des points-virgules sous une **\<TargetManifestFiles>** balise.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Spécifiez les manifestes cibles dans le fichier projet uniquement quand l’environnement cible de l’application est bien connu, à l’image des projets .NET Core. Ce n’est pas le cas des projets open source. En général, les utilisateurs d’un projet open source le déploient sur des environnements de production différents. Ces environnements de production ont généralement différents ensembles de packages préinstallés. Vous ne pouvez pas faire d’hypothèses sur le manifeste cible dans de tels environnements. vous devez donc utiliser l' `--manifest` option de [`dotnet publish`](../tools/dotnet-publish.md) .

## <a name="aspnet-core-implicit-store-net-core-20-only"></a>Magasin implicite ASP.NET Core (.NET Core 2,0 uniquement)

Le magasin implicite ASP.NET Core s’applique uniquement à ASP.NET Core 2.0. Nous vous recommandons fortement de baser les applications sur ASP.NET Core 2.1 et version ultérieure, car le magasin implicite n’est **pas** utilisé dans ce cas. ASP.NET Core 2.1 et les versions ultérieures utilisent le framework partagé.

Pour .NET Core 2,0, la fonctionnalité de magasin de packages de Runtime est utilisée implicitement par une application ASP.NET Core lorsque l’application est déployée en tant qu’application de [déploiement dépendante du Framework](index.md#publish-framework-dependent) . Les cibles dans [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) incluent des manifestes référençant le magasin de packages implicite sur le système cible. En outre, toute application dépendante du Framework qui dépend du `Microsoft.AspNetCore.All` package produit une application publiée qui contient uniquement l’application et ses ressources, et non les packages listés dans le `Microsoft.AspNetCore.All` Package. Ces packages sont censés être présents sur le système cible.

Le magasin de packages de runtime est installé sur l’hôte quand le SDK .NET Core est installé. D’autres programmes d’installation peuvent fournir le magasin de packages de runtime, notamment les installations Zip/tarball du SDK .NET Core, `apt-get`, Red Hat Yum, le bundle .NET Core Windows Server Hosting et les installations de magasin de packages de runtime manuelles.

Lors du déploiement d’une application de [déploiement dépendante du Framework](index.md#publish-framework-dependent) , assurez-vous que la kit SDK .net Core est installée sur l’environnement cible. Si l’application est déployée dans un environnement qui n’inclut pas de ASP.NET Core, vous pouvez désactiver le magasin implicite en spécifiant la  **\<PublishWithAspNetCoreTargetManifest>** valeur `false` dans le fichier projet comme dans l’exemple suivant :

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> Pour les applications de [déploiement autonomes](index.md#publish-self-contained) , il est supposé que le système cible ne contient pas nécessairement les packages de manifestes requis. Par conséquent, **\<PublishWithAspNetCoreTargetManifest>** ne peut pas être défini sur `true` pour une application autonome.

## <a name="see-also"></a>Voir aussi

- [dotnet-publish](../tools/dotnet-publish.md)
- [dotnet-store](../tools/dotnet-store.md)
