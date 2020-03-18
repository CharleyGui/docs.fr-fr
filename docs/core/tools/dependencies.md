---
title: Gérer les dépendances dans .NET Core
description: Explique comment gérer les dépendances du projet pour une application .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399146"
---
# <a name="manage-dependencies-in-net-core-applications"></a>Gérer les dépendances dans les applications .NET Core

Cet article explique comment ajouter et supprimer les dépendances en éditant le fichier de projet ou en utilisant l’IRTC.

## <a name="the-packagereference-element"></a>L’élément \<de> de la conclusion de paquet

L’élément `<PackageReference>` de dossier de projet a la structure suivante :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

L’attribut `Include` spécifie l’ID de l’ensemble à ajouter au projet. L’attribut `Version` spécifie la version à obtenir. Les versions sont spécifiées selon [les règles de la version NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Si vous n’êtes pas familier avec la syntaxe de fichier de projet, consultez la documentation de référence du [projet MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.

Utilisez les conditions pour ajouter une dépendance qui n’est disponible que dans une cible spécifique, comme le montre l’exemple suivant :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

La dépendance dans l’exemple précédent ne sera valable que si la construction se produit pour cette cible donnée. Le `$(TargetFramework)` dans l’état est une propriété MSBuild qui est mis dans le projet. Pour la plupart des applications .NET Core courantes, vous n’avez pas besoin de le faire.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Ajouter une dépendance en éditant le fichier du projet

Pour ajouter une dépendance, ajoutez un `<PackageReference>` élément à l’intérieur d’un `<ItemGroup>` élément. Vous pouvez ajouter `<ItemGroup>` à un existant ou en créer un nouveau. L’exemple suivant utilise le projet d’application de console par défaut qui est créé par `dotnet new console`:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="3.1.2" />
  </ItemGroup>

</Project>
```

## <a name="add-a-dependency-by-using-the-cli"></a>Ajouter une dépendance en utilisant le CLI

Pour ajouter une dépendance, exécutez la [dotnet add package](dotnet-add-package.md) commande, comme le montre l’exemple suivant :

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Supprimer une dépendance en modifiant le fichier du projet

Pour supprimer une dépendance, retirez son `<PackageReference>` élément du fichier de projet.

## <a name="remove-a-dependency-by-using-the-cli"></a>Supprimer une dépendance en utilisant l’IMC

Pour éliminer une dépendance, exécutez la [dotnet remove package](dotnet-remove-package.md) commande, comme le montre l’exemple suivant :

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Voir aussi

* [Paquets NuGet dans les fichiers du projet](../project-sdk/msbuild-props.md#nuget-packages)
* [dotnet list packageCommande](dotnet-remove-package.md)
