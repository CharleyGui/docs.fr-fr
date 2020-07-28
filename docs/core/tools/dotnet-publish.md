---
title: Commande dotnet publish
description: La commande dotnet publish publie un projet ou une solution .NET Core dans un répertoire.
ms.date: 02/24/2020
ms.openlocfilehash: 59fdbfa875dad13963ae198acc6a31b537279dfe
ms.sourcegitcommit: c8c3e1c63a00b7d27f76f5e50ee6469e6bdc8987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251177"
---
# <a name="dotnet-publish"></a>dotnet publish

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Nom

`dotnet publish`-Publie l’application et ses dépendances dans un dossier pour le déploiement sur un système d’hébergement.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a>Description

`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire. La sortie inclut les ressources suivantes :

- Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.
- *.deps.jssur* un fichier qui comprend toutes les dépendances du projet.
- *.runtimeconfig.jssur* un fichier qui spécifie le runtime partagé attendu par l’application, ainsi que d’autres options de configuration pour le runtime (par exemple, garbage collection type).
- Les dépendances de l’application, qui sont copiées à partir du cache NuGet dans le dossier de sortie.

La sortie de la commande `dotnet publish` est prête pour le déploiement sur un système d’hébergement (par exemple, un serveur, PC, Mac, ordinateur portable) à des fins d’exécution. Il s’agit de la seule façon officiellement prise en charge pour préparer l’application au déploiement. En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement. Pour plus d’informations, consultez [publier des applications .net core avec le CLI .net Core](../deploying/deploy-with-cli.md).

### <a name="implicit-restore"></a>Restauration implicite

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a>MSBuild

La commande `dotnet publish` appelle MSBuild, qui appelle la cible de `Publish`. Les paramètres passés à `dotnet publish` sont passés à MSBuild. Les paramètres `-c` et `-o` correspondent aux propriétés `Configuration` et `PublishDir` de MSBuild, respectivement.

La `dotnet publish` commande accepte les options MSBuild, comme `-p` pour définir des propriétés et `-l` pour définir un enregistreur d’événements. Par exemple, vous pouvez définir une propriété MSBuild en utilisant le format : `-p:<NAME>=<VALUE>` . Vous pouvez également définir des propriétés relatives à la publication en faisant référence à un fichier *. pubxml* , par exemple :

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

L’exemple précédent utilise le fichier *FolderProfile. pubxml* qui se trouve dans le dossier * \<project_folder> /Properties/PublishProfiles* . Si vous spécifiez un chemin d’accès et une extension de fichier lors de la définition de la `PublishProfile` propriété, ils sont ignorés. MSBuild par défaut examine le dossier *Properties/PublishProfiles* et suppose l’extension de fichier *pubxml* . Pour spécifier le chemin d’accès et le nom de fichier, y compris l’extension, définissez la propriété à la `PublishProfileFullPath` place de la `PublishProfile` propriété.

Pour plus d’informations, consultez les ressources suivantes :

- [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Profils de publication Visual Studio (. pubxml) pour le déploiement d’applications ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>Arguments

- **`PROJECT|SOLUTION`**

  Projet ou solution à publier.
  
  * `PROJECT`est le chemin d’accès et le nom de fichier d’un fichier projet [c#](csproj.md), f # ou Visual Basic, ou le chemin d’accès à un répertoire qui contient un fichier projet C#, f # ou Visual Basic. Si le répertoire n’est pas spécifié, le répertoire actif est utilisé par défaut.

  * `SOLUTION`est le chemin d’accès et le nom de fichier d’un fichier solution (extension *. sln* ), ou le chemin d’accès à un répertoire qui contient un fichier solution. Si le répertoire n’est pas spécifié, le répertoire actif est utilisé par défaut. Option disponible à partir du kit SDK .NET Core 3.0.

## <a name="options"></a>Options

- **`-c|--configuration <CONFIGURATION>`**

  Définit la configuration de build. La valeur par défaut pour la plupart des projets est `Debug` , mais vous pouvez remplacer les paramètres de configuration de build dans votre projet.

- **`-f|--framework <FRAMEWORK>`**

  Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié. Le framework cible doit être spécifié dans le fichier projet.

- **`--force`**

  Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. Option disponible à partir du kit SDK .NET Core 3.0.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application. Le fichier manifeste fait partie de la sortie de la [ `dotnet store` commande](dotnet-store.md). Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.

- **`--no-build`**

  Ne génère pas le projet avant la publication. L’indicateur `--no-restore` est également défini implicitement.

- **`--no-dependencies`**

  Ignore les références entre projets et restaure uniquement le projet racine.

- **`--nologo`**

  N’affiche pas la bannière de démarrage ni le message de copyright. Option disponible à partir du kit SDK .NET Core 3.0.

- **`--no-restore`**

  N’effectue pas de restauration implicite à l’exécution de la commande.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Spécifie le chemin d’accès du répertoire de sortie.
  
  S’il n’est pas spécifié, la valeur par défaut est *[project_file_folder]./bin/[Configuration]/[Framework]/Publish/* pour un exécutable dépendant du runtime et des binaires multiplateforme. La valeur par défaut est *[project_file_folder]/bin/[Configuration]/[Framework]/[Runtime]/Publish/* pour un exécutable autonome.

  Dans un projet Web, si le dossier de sortie se trouve dans le dossier du projet, les commandes successives `dotnet publish` génèrent des dossiers de sortie imbriqués. Par exemple, si le dossier du projet est *MyProject*et que le dossier de sortie de publication est *MyProject/Publish*, et que vous exécutez `dotnet publish` deux fois, la deuxième exécution place les fichiers de contenu, tels que les fichiers *. config* et *. JSON* dans *MyProject/Publish/Publish*. Pour éviter d’imbriquer des dossiers de publication, spécifiez un dossier de publication qui ne se trouve pas **directement** sous le dossier du projet, ou excluez le dossier de publication du projet. Pour exclure un dossier de publication nommé *publishoutput*, ajoutez l’élément suivant à un `PropertyGroup` élément dans le fichier *. csproj* :

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - Kit de développement logiciel (SDK) .NET Core 3. x et versions ultérieures
  
    Si un chemin d’accès relatif est spécifié lors de la publication d’un projet, le répertoire de sortie généré est relatif au répertoire de travail actuel, et non à l’emplacement du fichier projet.

    Si un chemin d’accès relatif est spécifié lors de la publication d’une solution, toutes les sorties de tous les projets sont placées dans le dossier spécifié par rapport au répertoire de travail actuel. Pour que la sortie de publication passe à des dossiers distincts pour chaque projet, spécifiez un chemin d’accès relatif à l’aide `PublishDir` de la propriété MSBuild au lieu de l' `--output` option. Par exemple, `dotnet publish -p:PublishDir=.\publish` envoie la sortie de publication pour chaque projet dans un `publish` dossier sous le dossier qui contient le fichier projet.

  - Kit de développement logiciel (SDK) .NET Core 2. x
  
    Si un chemin d’accès relatif est spécifié lors de la publication d’un projet, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.

    Si un chemin d’accès relatif est spécifié lors de la publication d’une solution, la sortie de chaque projet passe dans un dossier distinct relatif à l’emplacement du fichier projet. Si un chemin d’accès absolu est spécifié lors de la publication d’une solution, toutes les sorties de publication de tous les projets sont placées dans le dossier spécifié.

- **`-p:PublishReadyToRun=true`**

  Compile les assemblys d’application au format ReadyToRun (R2R). R2R est une forme de compilation ahead-of-time (AOT). Pour plus d’informations, consultez [images ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images). Option disponible à partir du kit SDK .NET Core 3.0.

  Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande. Pour plus d’informations, consultez [MSBuild](#msbuild).

- **`-p:PublishSingleFile=true`**

  Empaquette l’application dans un exécutable à fichier unique spécifique à la plateforme. L’exécutable est auto-extractible et contient toutes les dépendances (y compris native) requises pour exécuter l’application. Lors de la première exécution de l’application, celle-ci est extraite d’un répertoire basé sur le nom de l’application et l’identificateur de la build. Le démarrage est plus rapide quand l’application est réexécutée. L’application n’a pas besoin de s’extraire elle-même une deuxième fois, sauf si une nouvelle version est utilisée. Option disponible à partir du kit SDK .NET Core 3.0.

  Pour plus d’informations sur la publication monofichier, consultez le [document conceptuel sur l’outil de regroupement monofichier](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).

  Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande. Pour plus d’informations, consultez [MSBuild](#msbuild).

- **`-p:PublishTrimmed=true`**

  Supprime les bibliothèques inutilisées pour réduire la taille du déploiement d’une application lors de la publication d’un fichier exécutable autonome. Pour plus d’informations, consultez [Trim self-contained Deployments and executed](../deploying/trim-self-contained.md). Option disponible à partir du kit SDK .NET Core 3.0.

  Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande. Pour plus d’informations, consultez [MSBuild](#msbuild).

- **`--self-contained [true|false]`**

  Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible. La valeur par défaut est `true` si un identificateur de Runtime est spécifié et que le projet est un projet exécutable (pas un projet de bibliothèque). Pour plus d’informations, consultez [publication d’applications .net Core](../deploying/index.md) et [publication d’applications .net core avec le CLI .net Core](../deploying/deploy-with-cli.md).

  Si cette option est utilisée sans spécifier `true` ou `false` , la valeur par défaut est `true` . Dans ce cas, ne placez pas l’argument solution ou Project immédiatement après `--self-contained` , car `true` ou `false` est attendu dans cette position.

- **`--no-self-contained`**

  Équivaut à `--self-contained false`. Option disponible à partir du kit SDK .NET Core 3.0.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publie l’application pour un runtime donné. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Pour plus d’informations, consultez [publication d’applications .net Core](../deploying/index.md) et [publication d’applications .net core avec le CLI .net Core](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `minimal`.

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
- [Catalogue des identificateurs de Runtime (RID)](../rid-catalog.md)
- [Utilisation de la notaire Catalina macOS](../install/macos-notarization-issues.md)
- [Structure de répertoires d’une application publiée](/aspnet/core/hosting/directory-structure)
- [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Profils de publication Visual Studio (. pubxml) pour le déploiement d’applications ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
- [ILLInk. Tasks](https://aka.ms/dotnet-illink)
