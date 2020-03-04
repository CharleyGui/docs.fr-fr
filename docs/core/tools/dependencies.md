---
title: Gérer les dépendances dans .NET Core
description: Explique comment gérer les dépendances de projet pour une application .NET Core.
no-loc:
- dotnet add package
- dotnet remove package
- dotnet list package
ms.date: 02/25/2020
ms.openlocfilehash: 367be7eb04d58bffc0846de1d035a5801e8d9376
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157243"
---
# <a name="manage-dependencies-in-net-core-applications"></a>Gérer les dépendances dans les applications .NET Core

Cet article explique comment ajouter et supprimer des dépendances en modifiant le fichier projet ou à l’aide de l’interface CLI.

## <a name="the-packagereference-element"></a>Élément \<PackageReference >

L’élément du fichier de projet `<PackageReference>` a la structure suivante :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

L’attribut `Include` spécifie l’ID du package à ajouter au projet. L’attribut `Version` spécifie la version à récupérer. Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Si vous n’êtes pas familiarisé avec la syntaxe des fichiers projet, consultez la documentation de référence sur les [projets MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.

Utilisez des conditions pour ajouter une dépendance qui est disponible uniquement dans une cible spécifique, comme illustré dans l’exemple suivant :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

La dépendance dans l’exemple précédent sera valide uniquement si la génération se produit pour cette cible donnée. La `$(TargetFramework)` dans la condition est une propriété MSBuild qui est définie dans le projet. Pour la plupart des applications .NET Core courantes, vous n’avez pas besoin de le faire.

## <a name="add-a-dependency-by-editing-the-project-file"></a>Ajouter une dépendance en modifiant le fichier projet

Pour ajouter une dépendance, ajoutez un élément `<PackageReference>` à l’intérieur d’un élément `<ItemGroup>`. Vous pouvez ajouter à un `<ItemGroup>` existant ou en créer un nouveau. L’exemple suivant utilise le projet d’application console par défaut qui est créé par `dotnet new console`:

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

Pour ajouter une dépendance, exécutez la commande [dotnet add package](dotnet-add-package.md) , comme indiqué dans l’exemple suivant :

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore
```

## <a name="remove-a-dependency-by-editing-the-project-file"></a>Supprimer une dépendance en modifiant le fichier projet

Pour supprimer une dépendance, supprimez son élément `<PackageReference>` du fichier projet.

## <a name="remove-a-dependency-by-using-the-cli"></a>Supprimer une dépendance à l’aide de l’interface CLI

Pour supprimer une dépendance, exécutez la commande [dotnet remove package](dotnet-remove-package.md) , comme indiqué dans l’exemple suivant :

```dotnetcli
dotnet remove package Microsoft.EntityFrameworkCore
```

## <a name="see-also"></a>Voir aussi

* [Packages NuGet dans les fichiers projet](../project-sdk/msbuild-props.md#nuget-packages)
* [commande dotnet list package](dotnet-remove-package.md)
