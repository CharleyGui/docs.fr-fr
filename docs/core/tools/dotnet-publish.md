---
title: Commande dotnet publish
description: La commande dotnet publish publie un projet ou une solution .NET Core dans un répertoire.
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156996"
---
# <a name="dotnet-publish"></a>dotnet publish

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Nom

`dotnet publish`-publie l’application et ses dépendances dans un dossier pour le déploiement sur un système d’hébergement.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration] 
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>Description

`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire. La sortie inclut les ressources suivantes :

- Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.
- Un fichier *. DEPS. JSON* qui contient toutes les dépendances du projet.
- Un fichier *. runtimeconfig. JSON* qui spécifie le runtime partagé attendu par l’application, ainsi que d’autres options de configuration pour le runtime (par exemple, garbage collection type).
- Les dépendances de l’application, qui sont copiées à partir du cache NuGet dans le dossier de sortie.

La sortie de la commande `dotnet publish` est prête pour le déploiement sur un système d’hébergement (par exemple, un serveur, PC, Mac, ordinateur portable) à des fins d’exécution. Il s’agit de la seule façon officiellement prise en charge pour préparer l’application au déploiement. En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement.

## <a name="arguments"></a>Arguments

- **`PROJECT|SOLUTION`**

  Projet ou solution à publier.
  
  * `PROJECT` est le chemin d’accès et le [C#](csproj.md)nom F#de fichier d’un fichier projet, ou Visual Basic, ou le chemin d’accès C#à F#un répertoire qui contient un fichier projet, ou Visual Basic. Si le répertoire n’est pas spécifié, le répertoire actif est utilisé par défaut.

  * `SOLUTION` est le chemin d’accès et le nom de fichier d’un fichier solution (extension *. sln* ), ou le chemin d’accès à un répertoire qui contient un fichier solution. Si le répertoire n’est pas spécifié, le répertoire actif est utilisé par défaut. **Disponible à partir du kit de développement logiciel (SDK) .NET Core 3,0.** 

## <a name="options"></a>Options

- **`-c|--configuration <CONFIGURATION>`**

  Définit la configuration de build. La valeur par défaut pour la plupart des projets est `Debug`, mais vous pouvez remplacer les paramètres de configuration de build dans votre projet.

- **`-f|--framework <FRAMEWORK>`**

  Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié. Le framework cible doit être spécifié dans le fichier projet.

- **`--force`**

  Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`** **disponibles à partir du kit de développement logiciel (SDK) .net Core 3,0.**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application. Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md). Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.

- **`--no-build`**

  Ne génère pas le projet avant la publication. L’indicateur `--no-restore` est également défini implicitement.

- **`--no-dependencies`**

  Ignore les références entre projets et restaure uniquement le projet racine.

- **`--nologo`** **disponibles à partir du kit de développement logiciel (SDK) .net Core 3,0.**

  N’affiche pas la bannière de démarrage ni le message de copyright. 

- **`--no-restore`**

  N’effectue pas de restauration implicite à l’exécution de la commande.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Spécifie le chemin d’accès du répertoire de sortie. S’il n’est pas spécifié, la valeur par défaut est *./bin/[Configuration]/[Framework]/Publish/* pour un exécutable dépendant du runtime et des binaires multiplateforme. La valeur par défaut est *./bin/[Configuration]/[Framework]/[Runtime]/Publish/* pour un exécutable autonome.

  Si le chemin est relatif, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.

- **`--self-contained [true|false]`**

  Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible. La valeur par défaut est `true` si un identificateur de Runtime est spécifié. Pour plus d’informations, consultez [publication d’applications .net Core](../deploying/index.md) et [publication d’applications .net core avec le CLI .net Core](../deploying/deploy-with-cli.md).

- **`--no-self-contained`** **disponibles à partir du kit de développement logiciel (SDK) .net Core 3,0.**  

  Équivaut à `--self-contained false`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publie l’application pour un runtime donné. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Pour plus d’informations, consultez [publication d’applications .net Core](../deploying/index.md) et [publication d’applications .net core avec le CLI .net Core](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.

## <a name="examples"></a>Exemples

- Créez un [binaire multiplateforme dépendant du runtime](../deploying/index.md#produce-a-cross-platform-binary) pour le projet dans le répertoire actif :

  ```dotnetcli
  dotnet publish
  ```

  À compter du kit de développement logiciel (SDK) .NET Core 3,0, cet exemple crée également un [exécutable dépendant du runtime](../deploying/index.md#publish-runtime-dependent) pour la plateforme actuelle.

- Créer un [exécutable autonome](../deploying/index.md#publish-self-contained) pour le projet dans le répertoire actif, pour un Runtime spécifique :

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  Le RID doit se trouver dans le fichier projet.

- Créez un [exécutable dépendant du runtime](../deploying/index.md#publish-runtime-dependent) pour le projet dans le répertoire actif, pour une plateforme spécifique :

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  Le RID doit se trouver dans le fichier projet. Cet exemple s’applique au kit de développement logiciel (SDK) .NET Core 3,0 et versions ultérieures.

- Publiez le projet dans le répertoire actif, pour un Runtime spécifique et une version cible du .NET Framework :

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Publier le fichier projet spécifié :

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Publier l’application actuelle, mais ne pas restaurer les références entre projets (P2P), uniquement le projet racine pendant l’opération de restauration :

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la publication d’applications .NET Core](../deploying/index.md)
- [Publier des applications .NET Core avec le CLI .NET Core](../deploying/deploy-with-cli.md)
- [Frameworks cibles](../../standard/frameworks.md)
- [Catalogue d’identificateurs de runtime (RID)](../rid-catalog.md)
- [Utilisation de la notaire Catalina MacOS](../install/macos-notarization-issues.md) Pour plus d’informations, consultez les ressources suivantes :
- [Structure de répertoires d’une application publiée](/aspnet/core/hosting/directory-structure)
