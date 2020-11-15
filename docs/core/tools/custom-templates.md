---
title: Modèles personnalisés pour dotnet new
description: Découvrez les modèles personnalisés pour tout type de projet ou de fichier .NET.
author: adegeo
ms.date: 05/20/2020
ms.openlocfilehash: 3995fad864b80d024209c723a0197281e1b0f523
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634179"
---
# <a name="custom-templates-for-dotnet-new"></a>Modèles personnalisés pour dotnet new

Le [Kit de développement logiciel (SDK) .net](https://dotnet.microsoft.com/download) est fourni avec de nombreux modèles déjà installés et prêts à être utilisés. La [ `dotnet new` commande](dotnet-new.md) n’est pas le seul moyen d’utiliser un modèle, mais également comment installer et désinstaller des modèles. Vous pouvez créer vos propres modèles personnalisés pour tout type de projet, tel qu’une application, un service, un outil ou une bibliothèque de classes. Vous pouvez même créer un modèle qui génère un ou plusieurs fichiers indépendants, comme un fichier de configuration.

Vous pouvez installer des modèles personnalisés à partir d’un package NuGet sur tout flux NuGet, en référençant directement un fichier NuGet *. nupkg* ou en spécifiant un répertoire de système de fichiers qui contient le modèle. Le moteur de modèle offre des fonctionnalités qui vous permettent de remplacer des valeurs, d’inclure et d’exclure des fichiers, ainsi que d’exécuter des opérations de traitement personnalisées quand votre modèle est utilisé.

Le moteur de modèle est open source et le dépôt de code en ligne se trouve à l’adresse [dotnet/templating](https://github.com/dotnet/templating/) sur GitHub. Vous trouverez d’autres modèles, y compris des modèles tiers, à partir de la page [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (modèles disponibles pour dotnet new) sur GitHub. Pour plus d’informations sur la création et l’utilisation de modèles personnalisés, consultez [Guide pratique pour créer vos propres modèles pour dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) et le [Wiki du dépôt GitHub dotnet/templating GitHub](https://github.com/dotnet/templating/wiki).

> [!NOTE]
> Des exemples de modèles sont disponibles dans le référentiel GitHub [dotnet/dotnet-template-Samples](https://github.com/dotnet/dotnet-template-samples) . Toutefois, bien que ces exemples soient une bonne ressource pour apprendre comment les modèles fonctionnent, le référentiel est archivé et n’est plus conservé. Les exemples peuvent être obsolètes et ne plus fonctionner.

Pour suivre une procédure pas à pas et créer un modèle, consultez le didacticiel [Créer un modèle personnalisé pour dotnet new](../tutorials/cli-templates-create-item-template.md).

### <a name="net-default-templates"></a>Modèles par défaut .NET

Lorsque vous installez le [Kit de développement logiciel (SDK) .net](https://dotnet.microsoft.com/download), vous recevez plus d’une douzaine de modèles intégrés pour la création de projets et de fichiers, notamment des applications console, des bibliothèques de classes, des projets de test unitaire, des applications ASP.net Core (y compris des projets [angulaires](https://angular.io/) et des projets de [réaction](https://reactjs.org/) ) et des fichiers de configuration. Pour lister les modèles intégrés, exécutez la commande `dotnet new` avec l’option `-l|--list` :

```dotnetcli
dotnet new --list
```

## <a name="configuration"></a>Configuration

Un modèle est constitué des éléments suivants :

- Dossiers et fichiers sources.
- Un fichier de configuration ( *template.jssur* ).

### <a name="source-files-and-folders"></a>Dossiers et fichiers sources

Les dossiers et fichiers sources incluent tous les fichiers et dossiers que le modèle doit utiliser quand la commande `dotnet new <TEMPLATE>` est exécutée. Le moteur de modèle est conçu pour utiliser des *projets exécutables* comme code source pour générer des projets. Cela a plusieurs avantages :

- Vous n’avez pas besoin d’injecter des jetons spéciaux dans le code source de votre projet.
- Les fichiers de code ne sont pas des fichiers spéciaux ou des fichiers modifiés de quelque manière pour fonctionner avec le moteur de modèle. Ainsi, les outils que vous utilisez normalement avec des projets fonctionnent également avec le contenu du modèle.
- Vous générez, exécutez et déboguez vos projets de modèle comme vous le feriez pour tout autre projet.
- Vous pouvez rapidement créer un modèle à partir d’un projet existant en ajoutant simplement un fichier de configuration *./.template.config/template.json* au projet.

Les fichiers et dossiers stockés dans le modèle ne sont pas limités aux types de projet .NET formels. Les dossiers et fichiers sources peuvent comporter tout contenu que vous souhaitez créer quand vous utilisez le modèle, même si le moteur de modèle produit un seul fichier en guise de sortie.

Les fichiers générés par le modèle peuvent être modifiés en fonction de la logique et des paramètres que vous avez fournis dans le fichier de configuration *template.json*. L’utilisateur peut remplacer ces paramètres en passant des options à la commande `dotnet new <TEMPLATE>`. Un exemple courant de logique personnalisée est la fourniture d’un nom pour une classe ou une variable dans le fichier de code qui est déployé par un modèle.

### <a name="templatejson"></a>template.json

Le fichier *template.json* est placé dans un dossier *.template.config* dans le répertoire racine du modèle. Le fichier fournit des informations de configuration au moteur de modèle. La configuration minimale requiert les membres affichés dans le tableau suivant, qui suffisent pour créer un modèle fonctionnel.

| Membre            | Type          | Description |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | Schéma JSON pour le fichier *template.json*. Les éditeurs qui prennent en charge les schémas JSON activent les fonctionnalités d’édition JSON quand le schéma est spécifié. Par exemple, [Visual Studio Code](https://code.visualstudio.com/) exige ce membre pour activer IntelliSense. Utilisez la valeur de `http://json.schemastore.org/template`. |
| `author`          | string        | Auteur du modèle. |
| `classifications` | tableau(chaîne) | Zéro ou plusieurs caractéristiques du modèle qu’un utilisateur peut utiliser pour rechercher le modèle. Les classifications apparaissent également dans la colonne *Balises* quand il apparaît dans une liste de modèles produite à l’aide de la commande `dotnet new -l|--list`. |
| `identity`        | string        | Nom unique pour ce modèle. |
| `name`            | string        | Nom de modèle que les utilisateurs doivent voir. |
| `shortName`       | string        | Nom de raccourci par défaut pour sélectionner le modèle qui s’applique aux environnements où le nom du modèle est spécifié par l’utilisateur (non sélectionné par le biais d’une interface graphique utilisateur). Par exemple, le nom court est utile si les modèles sont utilisés à partir d’une invite de commandes avec des commandes CLI. |
| `sourceName`       | string        | Nom de l’arborescence source à remplacer par le nom que l’utilisateur spécifie. Le moteur de modèle recherchera toutes les occurrences des `sourceName` éléments mentionnés dans le fichier de configuration et les remplacera dans les noms de fichiers et les fichiers. La valeur à remplacer par peut être donnée à l’aide `-n` des `--name` options ou lors de l’exécution d’un modèle. Si aucun nom n’est spécifié, le répertoire actif est utilisé.|
| `preferNameDirectory`       | boolean        | Indique s’il faut créer un répertoire pour le modèle si nom est spécifié, mais qu’aucun répertoire de sortie n’est défini (au lieu de créer le contenu directement dans le répertoire actif). La valeur par défaut est false.|

Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template). Pour plus d’informations sur le fichier *template.json* , consultez le [Wiki de création de modèles dotnet](https://github.com/dotnet/templating/wiki).

#### <a name="example"></a>Exemple

Par exemple, voici un dossier de modèle qui contient deux fichiers de contenu : *console.cs* et *readme.txt*. Notez que la présence du dossier requis nommé *.template.config* , qui contient le fichier *template.json*.

```text
└───mytemplate
    │   console.cs
    │   readme.txt
    │
    └───.template.config
            template.json
```

Le fichier *template.json* ressemble à ceci :

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Travis Chau",
  "classifications": [ "Common", "Console" ],
  "identity": "AdatumCorporation.ConsoleTemplate.CSharp",
  "name": "Adatum Corporation Console Application",
  "shortName": "adatumconsole"
}
```

Le dossier *mytemplate* est un pack de modèle installable. Une fois le pack installé, `shortName` peut être utilisé avec la commande `dotnet new`. Par exemple, `dotnet new adatumconsole` devrait produire les fichiers `console.cs` et `readme.txt` dans le dossier actuel.

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Empaquetage d’un modèle dans un package NuGet (fichier nupkg)

Un modèle personnalisé est empaqueté avec la commande [dotnet pack](dotnet-pack.md) et un fichier *.csproj*. Vous pouvez également utiliser [NuGet](/nuget/tools/nuget-exe-cli-reference) avec la commande [nuget pack](/nuget/tools/cli-ref-pack) et un fichier *.nuspec*. Toutefois, NuGet requiert la .NET Framework sur Windows et [mono](https://www.mono-project.com/) sur Linux et MacOS.

Le fichier *.csproj* est légèrement différent d’un fichier de projet de code *.csproj* traditionnel. Notez les points suivants :

01. Le paramètre `<PackageType>` est ajouté et défini sur `Template`.
01. Le paramètre `<PackageVersion>` est ajouté et défini sur un [numéro de version de NuGet](/nuget/reference/package-versioning) valide.
01. Le paramètre `<PackageId>` est ajouté et la valeur est définie sur un identificateur unique. Cet identificateur est utilisé pour désinstaller le pack de modèle et est utilisé par les flux NuGet pour inscrire votre pack de modèle.
01. Les paramètres de métadonnées génériques doivent être définis : `<Title>`, `<Authors>`, `<Description>` et `<PackageTags>`.
01. Le paramètre `<TargetFramework>` doit être défini, même si le fichier binaire généré par le processus de modèle n’est pas utilisé. Dans l’exemple ci-dessous, il est défini sur `netstandard2.0`.

Un pack de modèle, sous la forme d’un package NuGet *.nupkg* , requiert que tous les modèles soient stockés dans le dossier *content* du package. Il existe quelques paramètres supplémentaires à ajouter à un fichier *.csproj* pour vous assurer que le *.nupkg* généré peut être installé en tant que pack de modèle :

01. Le paramètre `<IncludeContentInPack>` est défini sur `true` pour inclure n’importe quel fichier que le projet définit comme **contenu** dans le package NuGet.
01. Le paramètre `<IncludeBuildOutput>` est défini sur `false` pour exclure tous les fichiers binaires générés par le compilateur à partir du package NuGet.
01. Le paramètre `<ContentTargetFolders>` est défini sur `content`. Cela permet de s’assurer que les fichiers définis comme **contenu** sont stockés dans le dossier *content* du package NuGet. Ce dossier dans le package NuGet est analysé par le système de modèle dotnet.

Un moyen simple d’empêcher tous les fichiers de code d’être compilés par votre projet de modèle est d’utiliser l’élément `<Compile Remove="**\*" />` dans votre fichier projet, dans un élément `<ItemGroup>`.

Un moyen simple de structurer votre pack de modèle consiste à placer tous les modèles dans des dossiers individuels, puis chaque dossier de modèle à l’intérieur d’un dossier *templates* qui se trouve dans le même répertoire que votre fichier *.csproj*. De cette façon, vous pouvez utiliser un élément de projet unique pour inclure tous les fichiers et dossiers dans les *modèles* en tant que **contenu**. À l’intérieur d’un élément `<ItemGroup>`, créez un élément `<Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />`.

Voici un exemple de fichier *.csproj* respectant toutes les instructions ci-dessus. Il compresse le dossier enfant *templates* dans le dossier de package *content* et exclut tout fichier de code en cours de compilation.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <PackageType>Template</PackageType>
    <PackageVersion>1.0</PackageVersion>
    <PackageId>AdatumCorporation.Utility.Templates</PackageId>
    <Title>AdatumCorporation Templates</Title>
    <Authors>Me</Authors>
    <Description>Templates to use when creating an application for Adatum Corporation.</Description>
    <PackageTags>dotnet-new;templates;contoso</PackageTags>
    <TargetFramework>netstandard2.0</TargetFramework>

    <IncludeContentInPack>true</IncludeContentInPack>
    <IncludeBuildOutput>false</IncludeBuildOutput>
    <ContentTargetFolders>content</ContentTargetFolders>
  </PropertyGroup>

  <ItemGroup>
    <Content Include="templates\**\*" Exclude="templates\**\bin\**;templates\**\obj\**" />
    <Compile Remove="**\*" />
  </ItemGroup>

</Project>
```

L’exemple ci-dessous illustre la structure de fichiers et de dossiers lors de l’utilisation d’un *.csproj* pour créer un pack de modèle. Le fichier *MyDotnetTemplates.csproj* et le dossier *templates* se trouvent à la racine d’un répertoire nommé *project_folder*. Le dossier *templates* contient deux modèles, *mytemplate1* et *mytemplate2*. Chaque modèle a des fichiers de contenu et un dossier *.template.config* avec un fichier de configuration *template.json*.

```text
project_folder
│   MyDotnetTemplates.csproj
│
└───templates
    ├───mytemplate1
    │   │   console.cs
    │   │   readme.txt
    │   │
    │   └───.template.config
    │           template.json
    │
    └───mytemplate2
        │   otherfile.cs
        │
        └───.template.config
                template.json
```

## <a name="installing-a-template"></a>Installation d’un modèle

Utilisez la commande [dotnet new -i|--install](dotnet-new.md) pour installer un package.

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Pour installer un modèle à partir d’un package NuGet stocké sur nuget.org

Utilisez l’identificateur de package NuGet pour installer un package de modèle.

```dotnetcli
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Pour installer un modèle à partir d’un fichier nupkg local

Fournissez le chemin d’accès à un fichier de package NuGet *.nupkg*.

```dotnetcli
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Pour installer un modèle à partir d’un répertoire de système de fichiers

Les modèles peuvent être installés à partir d’un dossier de modèles, comme le dossier *mytemplate1* , à partir de l’exemple ci-dessus. Spécifiez le chemin du dossier *.template.config*. Le chemin d’accès au répertoire du modèle n’a pas besoin d’être absolu. Toutefois, un chemin d’accès absolu est requis pour désinstaller un modèle qui est installé à partir d’un dossier.

```dotnetcli
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="get-a-list-of-installed-templates"></a>Obtenir la liste des modèles installés

La commande de désinstallation, sans autres paramètres, répertorie tous les modèles.

```dotnetcli
dotnet new -u
```

Cette commande renvoie quelque chose de similaire à la sortie suivante :

```console
Template Instantiation Commands for .NET CLI

Currently installed items:
  Microsoft.DotNet.Common.ItemTemplates
    Templates:
      global.json file (globaljson)
      NuGet Config (nugetconfig)
      Solution File (sln)
      Dotnet local tool manifest file (tool-manifest)
      Web Config (webconfig)
  Microsoft.DotNet.Common.ProjectTemplates.3.0
    Templates:
      Class library (classlib) C#
      Class library (classlib) F#
      Class library (classlib) VB
      Console Application (console) C#
      Console Application (console) F#
      Console Application (console) VB
...
```

Le premier niveau d’éléments après `Currently installed items:` est composé des identificateurs utilisés dans la désinstallation d’un modèle. Et dans l’exemple ci-dessus, `Microsoft.DotNet.Common.ItemTemplates` et `Microsoft.DotNet.Common.ProjectTemplates.3.0` sont répertoriés. Si le modèle a été installé à l’aide d’un chemin d’accès du système de fichiers, cet identificateur est le chemin du dossier *.template.config*.

## <a name="uninstalling-a-template"></a>Désinstallation d’un modèle

Utilisez la commande [dotnet new -u|--uninstall](dotnet-new.md) pour désinstaller un package.

Si le package a été installé par un flux NuGet ou par un fichier *.nupkg* directement, fournissez l’identificateur.

```dotnetcli
dotnet new -u <NUGET_PACKAGE_ID>
```

Si le package a été installé en spécifiant un chemin d’accès au dossier *.template.config* , utilisez ce chemin **absolu** pour désinstaller le package. Vous pouvez voir le chemin d’accès absolu du modèle dans la sortie fournie par la commande `dotnet new -u`. Pour plus d’informations, consultez la section [Obtenir la liste des modèles installés](#get-a-list-of-installed-templates) ci-dessus.

```dotnetcli
dotnet new -u <ABSOLUTE_FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Créer un projet à l’aide d’un modèle personnalisé

Une fois un modèle installé, utilisez-le en exécutant la commande `dotnet new <TEMPLATE>` comme vous le feriez avec tout autre modèle préinstallé. Vous pouvez également spécifier des [options](dotnet-new.md#options) dans la commande `dotnet new`, notamment des options de modèle que vous avez configurées dans les paramètres de modèle. Indiquez le nom court du modèle directement dans la commande :

```dotnetcli
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Voir aussi

- [Créer un modèle personnalisé pour dotnet new (didacticiel)](../tutorials/cli-templates-create-item-template.md)
- [Wiki du dépôt GitHub dotnet/templating](https://github.com/dotnet/templating/wiki)
- [Dépôt GitHub dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)
- [Guide pratique pour créer vos propres modèles pour dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [Schéma *template.json* dans le magasin de schémas JSON](http://json.schemastore.org/template)
