---
title: Modèles personnalisés pour dotnet new
description: Découvrez les modèles personnalisés pour tout type de projet ou de fichier .NET.
author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: 6ce53cab308ed404974e4d736e735bc82ac04fe6
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299921"
---
# <a name="custom-templates-for-dotnet-new"></a>Modèles personnalisés pour dotnet new

Le [SDK .NET Core](https://www.microsoft.com/net/download/core) est fourni avec de nombreux modèles préinstallés à utiliser avec la [commande `dotnet new`](dotnet-new.md). À compter de .NET Core 2.0, vous pouvez créer vos propres modèles personnalisés pour tout type de projet, tel qu’une application, un service, un outil ou une bibliothèque de classes. Vous pouvez même créer un modèle qui génère un ou plusieurs fichiers indépendants, comme un fichier de configuration.

Vous pouvez installer des modèles personnalisés à partir d’un package NuGet sur tout flux NuGet, en référençant un fichier *nupkg* NuGet directement ou en spécifiant un répertoire de système de fichiers qui contient le modèle. Le moteur de modèle offre des fonctionnalités qui vous permettent de remplacer des valeurs, d’inclure et d’exclure des fichiers et des régions de fichiers, ainsi que d’exécuter des opérations de traitement personnalisées quand votre modèle est utilisé.

Le moteur de modèle est open source et le dépôt de code en ligne se trouve à l’adresse [dotnet/templating](https://github.com/dotnet/templating/) sur GitHub. Visitez le dépôt [dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) pour obtenir des exemples de modèles. Vous trouverez d’autres modèles, y compris des modèles tiers, à partir de la page [Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new) (modèles disponibles pour dotnet new) sur GitHub. Pour plus d’informations sur la création et l’utilisation de modèles personnalisés, consultez [Guide pratique pour créer vos propres modèles pour dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/) et le [Wiki du dépôt GitHub dotnet/templating GitHub](https://github.com/dotnet/templating/wiki).

Pour suivre une procédure pas à pas et créer un modèle, consultez le didacticiel [Créer un modèle personnalisé pour dotnet new](~/docs/core/tutorials/create-custom-template.md).

## <a name="configuration"></a>Configuration

Un modèle est constitué des composants suivants :

- Dossiers et fichiers sources
- Un fichier de configuration (*template.json*)

### <a name="source-files-and-folders"></a>Dossiers et fichiers sources

Les dossiers et fichiers sources incluent tous les fichiers et dossiers que le modèle doit utiliser quand la commande `dotnet new <TEMPLATE>` est exécutée. Le moteur de modèle est conçu pour utiliser des *projets exécutables* comme code source pour générer des projets. Cela a plusieurs avantages :

- Vous n’avez pas besoin d’injecter des jetons spéciaux dans le code source de votre projet.
- Les fichiers de code ne sont pas des fichiers spéciaux ou des fichiers modifiés de quelque manière pour fonctionner avec le moteur de modèle. Ainsi, les outils que vous utilisez normalement avec des projets fonctionnent également avec le contenu du modèle.
- Vous générez, exécutez et déboguez vos projets de modèle comme vous le feriez pour tout autre projet.
- Vous pouvez rapidement créer un modèle à partir d’un projet existant en ajoutant simplement un fichier de configuration *template.json* au projet.

Les fichiers et dossiers stockés dans le modèle ne sont pas limités aux types de projet .NET formels, tels que les solutions .NET Core ou .NET Framework. Les dossiers et fichiers sources peuvent comporter tout contenu que vous souhaitez créer quand vous utilisez le modèle, même si le moteur de modèle produit un seul fichier en guise de sortie, comme un fichier de configuration ou un fichier solution. Par exemple, vous pouvez créer un modèle qui contient un fichier source *web.config* et crée un fichier *web.config* modifié pour les projets où le modèle est utilisé. Les modifications apportées aux fichiers sources sont basées sur la logique et les paramètres que vous avez fournis dans le fichier de configuration *template.json*, ainsi que sur les valeurs fournies par l’utilisateur en tant qu’options de la commande `dotnet new <TEMPLATE>`.

### <a name="templatejson"></a>template.json

Le fichier *template.json* est placé dans un dossier *.template.config* dans le répertoire racine du modèle. Le fichier fournit des informations de configuration au moteur de modèle. La configuration minimale requiert les membres affichés dans le tableau suivant, qui suffisent pour créer un modèle fonctionnel.

| Membre            | Type          | Description |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | Schéma JSON pour le fichier *template.json*. Les éditeurs qui prennent en charge les schémas JSON activent les fonctionnalités d’édition JSON quand le schéma est spécifié. Par exemple, [Visual Studio Code](https://code.visualstudio.com/) exige ce membre pour activer IntelliSense. Utilisez la valeur de `http://json.schemastore.org/template`. |
| `author`          | string        | Auteur du modèle. |
| `classifications` | tableau(chaîne) | Zéro ou plusieurs caractéristiques du modèle qu’un utilisateur peut utiliser pour rechercher le modèle. Les classifications apparaissent également dans la colonne *Balises* quand il apparaît dans une liste de modèles produite à l’aide de la commande <code>dotnet new -l&#124;--list</code>. |
| `identity`        | string        | Nom unique pour ce modèle. |
| `name`            | string        | Nom de modèle que les utilisateurs doivent voir. |
| `shortName`       | string        | Raccourci par défaut pour sélectionner le modèle qui s’applique aux environnements où le nom du modèle est spécifié par l’utilisateur (non sélectionné par le biais d’une interface graphique utilisateur). Par exemple, le nom court est utile si les modèles sont utilisés à partir d’une invite de commandes avec des commandes CLI. |

#### <a name="example"></a>Exemple :

```json
{
  "$schema": "http://json.schemastore.org/template",
  "author": "Catalina Garcia",
  "classifications": [ "Common", "Console" ],
  "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
  "name": "Garcia Software Console Application",
  "shortName": "garciaconsole"
}
```

Le schéma complet pour le fichier *template.json* se trouve dans le [magasin de schémas JSON](http://json.schemastore.org/template).

## <a name="net-default-templates"></a>Modèles par défaut .NET

Quand vous installez le [SDK .NET Core](https://www.microsoft.com/net/download/core), vous obtenez plus d’une dizaine de modèles intégrés pour la création de projets et de fichiers, notamment des applications de console, des bibliothèques de classes, des projets de test unitaire, des applications ASP.NET Core (dont les projets [Angular](https://angular.io/) et [React](https://facebook.github.io/react/)) et des fichiers de configuration. Pour lister les modèles intégrés, exécutez la commande `dotnet new` avec l’option `-l|--list` :

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>Empaquetage d’un modèle dans un package NuGet (fichier nupkg)

Un modèle personnalisé est empaqueté sur Windows avec [nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) (pas avec [dotnet pack](dotnet-pack.md)). Pour un empaquetage multiplateforme, envisagez d’utiliser [NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000).

Le contenu du dossier de projet, avec son fichier *.template.config/template.json*, est placé dans un dossier nommé *content*. À côté du dossier *content*, ajoutez un [fichier *nuspec*](/nuget/create-packages/creating-a-package), fichier manifeste XML qui décrit le contenu d’un package et pilote le processus de création du package NuGet. À l’intérieur d’un élément **\<packageTypes>** dans le fichier *nuspec*, ajoutez un élément **\<packageType>** avec une valeur d’attribut `name` de `Template`. Le dossier *content* et le fichier *nuspec* doivent être tous les deux dans le même répertoire. Le tableau indique les éléments du fichier *nuspec* indispensables pour produire un modèle sous forme de package NuGet.

| Élément            | Type   | Description |
| ------------------ | ------ | ----------- |
| **\<authors>**     | string | Liste séparée par des virgules des auteurs de packages, qui correspondent aux noms de profil sur nuget.org. Les auteurs sont affichés dans la galerie NuGet sur nuget.org et servent à croiser les références des packages de mêmes auteurs. |
| **\<description>** | string | Description longue du package pour l’affichage de l’interface utilisateur. |
| **\<id>**          | string | Identificateur de package respectant la casse, qui doit être unique dans nuget.org ou dans toute autre galerie susceptible de l’héberger. Les ID ne peuvent pas contenir d’espaces ou de caractères qui ne sont pas valides pour une URL et suivent généralement les règles d’espace de noms .NET. Pour obtenir des conseils, consultez [Choix d’un identificateur de package unique et définition du numéro de version](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number). |
| **\<packageType>** | string | Placez cet élément à l’intérieur d’un élément **\<packageTypes>** parmi les éléments **\<metadata>** . Affectez à l’attribut `name` de l’élément **\<packageType>** la valeur `Template`. |
| **\<version>**     | string | Version du package, selon le format version_principale.version_secondaire.version_corrective. Les numéros de version peuvent inclure un suffixe de préversion comme décrit dans la rubrique [Préversions](/nuget/create-packages/prerelease-packages#semantic-versioning). |

Consultez les [informations de référence sur .nuspec](/nuget/schema/nuspec) pour connaître le schéma du fichier *nuspec*. Un exemple de fichier *nuspec* pour un modèle est disponible dans le didacticiel [Créer un modèle personnalisé pour dotnet new](~/docs/core/tutorials/create-custom-template.md).

[Créez un package](/nuget/create-packages/creating-a-package#creating-the-package) à l’aide de la commande `nuget pack <PATH_TO_NUSPEC_FILE>`.

## <a name="installing-a-template"></a>Installation d’un modèle

Installez un modèle personnalisé à partir d’un package NuGet sur tout flux NuGet en référençant un fichier *nupkg* directement ou en spécifiant un répertoire de système de fichiers qui contient une configuration de création de modèles. Utilisez l’option `-i|--install` avec la commande [dotnet new](dotnet-new.md).

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Pour installer un modèle à partir d’un package NuGet stocké sur nuget.org

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>Pour installer un modèle à partir d’un fichier nupkg local

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>Pour installer un modèle à partir d’un répertoire de système de fichiers

`FILE_SYSTEM_DIRECTORY` est le dossier de projet contenant le projet et le dossier *.template.config* :

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>Désinstallation d’un modèle

Désinstallez un modèle personnalisé en référençant un package NuGet par son `id` ou en spécifiant un répertoire de système de fichiers qui contient une configuration de création de modèles. Utilisez l’option d’installation `-u|--uninstall` avec la commande [dotnet new](dotnet-new.md).

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>Pour désinstaller un modèle à partir d’un package NuGet stocké sur nuget.org

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>Pour désinstaller un modèle à partir d’un fichier nupkg local

Pour désinstaller le modèle, n’essayez pas d’utiliser le chemin du fichier *nupkg*. La tentative de désinstaller un modèle à l’aide de `dotnet new -u <PATH_TO_NUPKG_FILE>` est vouée à l’échec. Référencez le package par son `id` :

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>Pour désinstaller un modèle à partir d’un répertoire de système de fichiers

`FILE_SYSTEM_DIRECTORY` est le dossier de projet contenant le projet et le dossier *.template.config*. Le chemin d’accès fourni doit être le chemin d’accès absolu. La tentative de désinstallation d’un modèle à l’aide d’un chemin d'accès relatif est vouée à l’échec. Pour plus d’informations, consultez l’article [dotnet new](dotnet-new.md).

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>Créer un projet à l’aide d’un modèle personnalisé

Une fois un modèle installé, utilisez-le en exécutant la commande `dotnet new <TEMPLATE>` comme vous le feriez avec tout autre modèle préinstallé. Vous pouvez également spécifier des [options](dotnet-new.md#options) dans la commande `dotnet new`, notamment des options de modèle que vous avez configurées dans les paramètres de modèle. Indiquez le nom court du modèle directement dans la commande :

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>Voir aussi

- [Créer un modèle personnalisé pour dotnet new (didacticiel)](../tutorials/create-custom-template.md)
- [Wiki du dépôt GitHub dotnet/templating](https://github.com/dotnet/templating/wiki)
- [Dépôt GitHub dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples)
- [Guide pratique pour créer vos propres modèles pour dotnet new](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [Schéma *template.json* dans le magasin de schémas JSON](http://json.schemastore.org/template)
