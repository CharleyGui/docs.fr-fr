---
title: Gérer les dépendances dans les outils .NET Core
description: Explique comment gérer les dépendances avec les outils .NET Core.
ms.date: 03/06/2017
ms.openlocfilehash: 916daca0240c10dc63ca96048590a426bc51d450
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965618"
---
# <a name="manage-dependencies-with-net-core-sdk-10"></a>Gérer les dépendances avec kit SDK .NET Core 1,0

Le passage des projets .NET Core de project.json vers csproj et MSBuild s’est accompagné d’une unification du fichier projet et des ressources permettant le suivi des dépendances. Pour les projets .NET Core, cela est similaire à ce que fait Project. JSON. Il n’existe aucun fichier JSON ou XML distinct qui assure le suivi des dépendances NuGet. Avec ce changement, nous avons également introduit un autre type de *référence* dans la syntaxe csproj, appelé `<PackageReference>`.

Ce document décrit le nouveau type de référence. Il montre également comment ajouter à votre projet une dépendance de package à l’aide de ce nouveau type de référence.

## <a name="the-new-packagereference-element"></a>Nouvel élément \<PackageReference>

`<PackageReference>` présente la structure de base suivante :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" />
```

Si vous êtes familiarisé avec MSBuild, il est similaire aux autres types de référence existants. La clé est l’instruction `Include`, qui spécifie l’ID de package que vous souhaitez ajouter au projet. L’élément enfant `<Version>` spécifie la version à obtenir. Les versions sont spécifiées en fonction des [règles de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges).

> [!NOTE]
> Si vous n’êtes pas familiarisé avec la syntaxe de fichier projet, consultez la documentation de [Référence du projet MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) pour plus d’informations.

Utilisez des conditions pour ajouter une dépendance qui est disponible uniquement dans une cible spécifique, comme illustré dans l’exemple suivant :

```xml
<PackageReference Include="PACKAGE_ID" Version="PACKAGE_VERSION" Condition="'$(TargetFramework)' == 'netcoreapp2.1'" />
```

La dépendance n’est valide que si la génération se produit pour cette cible donnée. La `$(TargetFramework)` dans la condition est une propriété MSBuild qui est définie dans le projet. Pour la plupart des applications .NET Core courantes, cela n’est pas nécessaire.

## <a name="add-a-dependency-to-the-project"></a>Ajouter une dépendance au projet

Ajouter une dépendance à votre projet est une opération simple. Voici un exemple montrant comment ajouter la version `9.0.1` de Json.NET à votre projet. Bien entendu, cela vaut également pour toute autre dépendance NuGet.

Votre fichier projet contient au moins deux nœuds `<ItemGroup>`. L’un des nœuds contient déjà `<PackageReference>` éléments. Vous pouvez ajouter votre nouvelle dépendance à ce nœud ou en créer un nouveau. le résultat sera le même.

L’exemple suivant utilise le modèle par défaut qui est supprimé par `dotnet new console`. Il s’agit d’une application console simple. Lorsque vous ouvrez le projet, vous trouverez le `<ItemGroup>` avec des `<PackageReference>` déjà existants. Ajoutez ce qui suit :

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

Après cela, enregistrez le projet et exécutez la commande `dotnet restore` pour installer la dépendance.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Le projet complet ressemble à ceci :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
</Project>
```

## <a name="remove-a-dependency-from-the-project"></a>Supprimer une dépendance du projet

Pour supprimer une dépendance du fichier projet, il suffit de supprimer `<PackageReference>` de ce fichier.
