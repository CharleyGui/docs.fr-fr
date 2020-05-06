---
title: Gérer les dépendances dans .NET Core
description: Explique comment gérer les dépendances de projet pour une application .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 3e1d807ea69e66e31b277a92cd6a1dc0e76531b5
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795545"
---
# <a name="manage-dependencies-in-net-core-applications"></a>Gérer les dépendances dans les applications .NET Core

Cet article explique comment ajouter et supprimer des dépendances en modifiant le fichier projet ou à l’aide de l’interface CLI.

## <a name="the-packagereference-element"></a>Élément \<PackageReference>

L' `<PackageReference>` élément du fichier projet a la structure suivante :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

L' `Include` attribut spécifie l’ID du package à ajouter au projet. L' `Version` attribut spécifie la version à récupérer. Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Si vous n’êtes pas familiarisé avec la syntaxe des fichiers projet, consultez la documentation de référence sur les [projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.

Utilisez des conditions pour ajouter une dépendance qui est disponible uniquement dans une cible spécifique, comme illustré dans l’exemple suivant :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

La dépendance dans l’exemple précédent sera valide uniquement si la génération se produit pour cette cible donnée. `$(TargetFramework)` Dans la condition, il s’agit d’une propriété MSBuild qui est définie dans le projet. Pour la plupart des applications .NET Core courantes, vous n’avez pas besoin de le faire.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Ajouter une dépendance en modifiant le fichier projet

Pour ajouter une dépendance, ajoutez un `<PackageReference>` élément à l' `<ItemGroup>` intérieur d’un élément. Vous pouvez ajouter à un existant `<ItemGroup>` ou en créer un nouveau. L’exemple suivant utilise le projet d’application console par défaut qui est `dotnet new console`créé par :

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

## <a name="add-a-dependency-by-using-the-cli"></a>Ajouter une dépendance à l’aide de l’interface CLI

Pour ajouter une dépendance, exécutez la [dotnet add package](dotnet-add-package.md) commande, comme indiqué dans l’exemple suivant :

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Supprimer une dépendance en modifiant le fichier projet

Pour supprimer une dépendance, supprimez `<PackageReference>` son élément du fichier projet.

## <a name="remove-a-dependency-by-using-the-cli"></a>Supprimer une dépendance à l’aide de l’interface CLI

Pour supprimer une dépendance, exécutez la [dotnet remove package](dotnet-remove-package.md) commande, comme indiqué dans l’exemple suivant :

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Voir aussi

* [Références de package dans les fichiers projet](../project-sdk/msbuild-props.md#reference-properties)
* [dotnet list packagecommande](dotnet-remove-package.md)
