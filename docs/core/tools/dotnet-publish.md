---
title: Commande dotnet publish
description: La commande de publication dotnet publie un projet ou une solution .NET Core à un répertoire.
ms.date: 02/24/2020
ms.openlocfilehash: 78ed8098be1b6887fc6a2a647fd169e2bf7f7fd1
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102799"
---
# <a name="dotnet-publish"></a>dotnet publish

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet publish`- Publie l’application et ses dépendances à un dossier pour le déploiement dans un système d’hébergement.

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
- Un fichier *.deps.json* qui comprend toutes les dépendances du projet.
- Un fichier *.runtimeconfig.json* qui spécifie le temps d’exécution partagé que l’application attend, ainsi que d’autres options de configuration pour le temps d’exécution (par exemple, type de collecte des ordures).
- Les dépendances de l’application, qui sont copiées à partir du cache NuGet dans le dossier de sortie.

La sortie de la commande `dotnet publish` est prête pour le déploiement sur un système d’hébergement (par exemple, un serveur, PC, Mac, ordinateur portable) à des fins d’exécution. Il s’agit de la seule façon officiellement prise en charge pour préparer l’application au déploiement. En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement. Pour plus d’informations, voir [Publier .NET Apps Core avec le CLI .NET Core](../deploying/deploy-with-cli.md).

### <a name="implicit-restore"></a>Restauration implicite

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a>MSBuild

La commande `dotnet publish` appelle MSBuild, qui appelle la cible de `Publish`. Les paramètres passés à `dotnet publish` sont passés à MSBuild. Les paramètres `-c` et `-o` correspondent aux propriétés `Configuration` et `OutputPath` de MSBuild, respectivement.

La `dotnet publish` commande accepte les options MSBuild, telles que `-p` pour définir les propriétés et `-l` définir un bûcheron. Par exemple, vous pouvez définir une propriété MSBuild en utilisant le format : `-p:<NAME>=<VALUE>`. Vous pouvez également définir des propriétés liées à la publication en vous référant à un fichier *.pubxml,* par exemple :

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

Pour plus d’informations, consultez les ressources suivantes :

- [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Visual Studio publie des profils (.pubxml) pour ASP.NET déploiement de l’application Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>Arguments

- **`PROJECT|SOLUTION`**

  Le projet ou la solution à publier.
  
  * `PROJECT`est le nom de voie et de fichier [d’un](csproj.md)fichier de projet de C, de F, ou de base visuelle, ou le chemin vers un répertoire qui contient un fichier de projet de C, de F, ou de base visuelle. Si l’annuaire n’est pas spécifié, il est par défaut à l’annuaire actuel.

  * `SOLUTION`est le chemin et le nom de fichier d’un fichier de solution *(extension .sln),* ou le chemin vers un répertoire qui contient un fichier de solution. Si l’annuaire n’est pas spécifié, il est par défaut à l’annuaire actuel. Option disponible à partir du kit SDK .NET Core 3.0.

## <a name="options"></a>Options

- **`-c|--configuration <CONFIGURATION>`**

  Définit la configuration de build. La valeur par `Debug`défaut pour la plupart des projets est, mais vous pouvez remplacer les paramètres de configuration de construction dans votre projet.

- **`-f|--framework <FRAMEWORK>`**

  Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié. Le framework cible doit être spécifié dans le fichier projet.

- **`--force`**

  Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. Option disponible à partir du kit SDK .NET Core 3.0.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application. Le fichier manifeste fait partie [ `dotnet store` ](dotnet-store.md)de la sortie de la commande . Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.

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
  
  S’il n’est pas précisé, il ne fait pas défaut à *[project_file_folder]./bin/[configuration]/[cadre]/publier/* pour un délai exécutable et multiplateforme. Il est par défaut à *[project_file_folder]/bin/[configuration]/[cadre]/[runtime]/publish/* pour un exécutable autonome.

  Dans un projet Web, si le dossier de sortie `dotnet publish` se trouve dans le dossier du projet, les commandes successives entraînent des dossiers de sortie imbriqués. Par exemple, si le dossier de projet est *monproject*, et le dossier `dotnet publish` de sortie de publication est *monproject/publier*, et vous exécutez deux fois, la deuxième exécution met des fichiers de contenu tels que *.config* et *.json* fichiers dans *monproject/ publier / publier*. Pour éviter de nichant les dossiers de publication, spécifiez un dossier de publication qui n’est pas directement sous le dossier du projet, ou excluez le dossier de publication du projet. Pour exclure un dossier de publication nommé *publieurputput*, ajoutez l’élément suivant à un `PropertyGroup` élément dans le fichier *.csproj:*

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - .NET Core 3.x SDK et plus tard
  
    Si un chemin relatif est spécifié lors de la publication d’un projet, l’annuaire de sortie généré est relatif à l’annuaire de travail actuel, et non à l’emplacement du fichier du projet.

    Si un chemin relatif est spécifié lors de la publication d’une solution, toutes les sorties pour tous les projets entrent dans le dossier spécifié par rapport à l’annuaire de travail actuel. Pour faire publier la sortie aller à des dossiers séparés pour chaque `PublishDir` projet, `--output` spécifier un chemin relatif en utilisant la propriété de msbuild au lieu de l’option. Par exemple, `dotnet publish -p:PublishDir=.\publish` envoie la sortie `publish` de publication pour chaque projet à un dossier sous le dossier qui contient le fichier de projet.

  - .NET Core 2.x SDK
  
    Si un chemin relatif est spécifié lors de la publication d’un projet, l’annuaire de sortie généré est relatif à l’emplacement du fichier du projet, et non à l’annuaire de travail actuel.

    Si un chemin relatif est spécifié lors de la publication d’une solution, la sortie de chaque projet est dans un dossier distinct par rapport à l’emplacement du fichier du projet. Si un chemin absolu est spécifié lors de la publication d’une solution, tous les documents de publication pour tous les projets entrent dans le dossier spécifié.

- **`-p:PublishReadyToRun=true`**

  Compile les assemblages d’applications sous forme de format ReadyToRun (R2R). R2R est une forme de compilation ahead-of-time (AOT). Pour plus d’informations, voir [les images ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images). Option disponible à partir du kit SDK .NET Core 3.0.

  Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande. Pour plus d’informations, consultez [MSBuild](#msbuild).

- **`-p:PublishSingleFile=true`**

  Emballe l’application dans un fichier unique spécifique à une plate-forme exécutable. L’exécutable est auto-extraction et contient toutes les dépendances (y compris indigène) qui sont nécessaires pour exécuter l’application. Lors de la première exécution de l’application, celle-ci est extraite d’un répertoire basé sur le nom de l’application et l’identificateur de la build. Le démarrage est plus rapide quand l’application est réexécutée. L’application n’a pas besoin de s’extraire une deuxième fois à moins qu’une nouvelle version ne soit utilisée. Option disponible à partir du kit SDK .NET Core 3.0.

  Pour plus d’informations sur la publication monofichier, consultez le [document conceptuel sur l’outil de regroupement monofichier](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).

  Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande. Pour plus d’informations, consultez [MSBuild](#msbuild).

- **`-p:PublishTrimmed=true`**

  Coupe les bibliothèques inutilisées pour réduire la taille du déploiement d’une application lors de la publication d’un exécutable autonome. Pour plus d’informations, voir [Trim déploiements autonomes et exécutables](../deploying/trim-self-contained.md). Option disponible à partir du kit SDK .NET Core 3.0.

  Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande. Pour plus d’informations, consultez [MSBuild](#msbuild).

- **`--self-contained [true|false]`**

  Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible. La `true` valeur par défaut est si un identifiant de temps d’exécution est spécifié et que le projet est un projet exécutable (pas un projet de bibliothèque). Pour plus d’informations, voir [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).

  Si cette option est `true` utilisée `false`sans spécifier ou , la valeur par défaut est `true`. Dans ce cas, ne mettez pas la `--self-contained`solution `true` ou `false` l’argument du projet immédiatement après , parce que ou est attendu dans cette position.

- **`--no-self-contained`**

  Équivaut à `--self-contained false`. Option disponible à partir du kit SDK .NET Core 3.0.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publie l’application pour un runtime donné. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Pour plus d’informations, voir [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.

## <a name="examples"></a>Exemples

- Créez un [binaire multiplateforme dépendant du temps d’exécution](../deploying/index.md#produce-a-cross-platform-binary) pour le projet dans l’annuaire actuel :

  ```dotnetcli
  dotnet publish
  ```

  En commençant par .NET Core 3.0 SDK, cet exemple crée également un [runtime-dépendant exécutable](../deploying/index.md#publish-runtime-dependent) pour la plate-forme actuelle.

- Créez un [exécutable autonome](../deploying/index.md#publish-self-contained) pour le projet dans l’annuaire actuel, pour une durée de course spécifique :

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  Le RID doit être dans le dossier du projet.

- Créez un [runtime-dépendant exécutable](../deploying/index.md#publish-runtime-dependent) pour le projet dans l’annuaire actuel, pour une plate-forme spécifique :

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  Le RID doit être dans le dossier du projet. Cet exemple s’applique à .NET Core 3.0 SDK et aux versions ultérieures.

- Publier le projet dans l’annuaire actuel, pour un cadre spécifique de temps d’exécution et de cible :

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Publier le fichier de projet spécifié :

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Publiez l’application actuelle mais ne restaurez pas les références du projet au projet (P2P), juste le projet racine pendant l’opération de restauration :

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Voir aussi

- [.NET Aperçu de publication d’applications de base](../deploying/index.md)
- [Publier des applications .NET Core avec le CLI core .NET](../deploying/deploy-with-cli.md)
- [Versions cibles de .NET Framework](../../standard/frameworks.md)
- [Catalogue Runtime IDentifier (RID)](../rid-catalog.md)
- [Travailler avec macOS Catalina Notarization](../install/macos-notarization-issues.md)
- [Structure d’annuaire d’une application publiée](/aspnet/core/hosting/directory-structure)
- [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Visual Studio publie des profils (.pubxml) pour ASP.NET déploiement de l’application Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
- [ILLInk.Tâches](https://aka.ms/dotnet-illink)
