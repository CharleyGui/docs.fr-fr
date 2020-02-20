---
title: Commande dotnet build
description: La commande dotnet build permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 02/14/2020
ms.openlocfilehash: 9f9a78ec0a6a25c54c8a727c05081ce6835514ee
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503763"
---
# <a name="dotnet-build"></a>dotnet build

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Name

`dotnet build` : Génère un projet et l’ensemble de ses dépendances.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet build` génère le projet et ses dépendances dans un ensemble de fichiers binaires. Les binaires incluent le code du projet dans des fichiers de langage intermédiaire (IL) avec une extension *. dll* .  En fonction du type de projet et des paramètres, d’autres fichiers peuvent être inclus, par exemple :

- Exécutable qui peut être utilisé pour exécuter l’application, si le type de projet est un exécutable ciblant .NET Core 3,0 ou une version ultérieure.
- Fichiers de symboles utilisés pour le débogage avec une extension *. pdb* .
- Un fichier *. DEPS. JSON* , qui répertorie les dépendances de l’application ou de la bibliothèque.
- Un fichier *. runtimeconfig. JSON* , qui spécifie le runtime partagé et sa version pour une application.
- Les autres bibliothèques dont le projet dépend (par le biais de références de projet ou de références de package NuGet).

Pour les projets exécutables ciblant des versions antérieures à .NET Core 3,0, les dépendances de bibliothèque de NuGet ne sont généralement pas copiées dans le dossier de sortie.  Ils sont résolus à partir du dossier des packages globaux NuGet au moment de l’exécution. Par conséquent, le produit de `dotnet build` ne peut pas être transféré en l’état vers un autre ordinateur pour exécution. Pour créer une version de l’application qui peut être déployée, vous devez la publier (par exemple, à l’aide de la commande [dotnet Publish](dotnet-publish.md) ). Pour plus d’informations, consultez la page [Déploiement d’applications .NET Core](../deploying/index.md).

Pour les projets exécutables ciblant .NET Core 3,0 et versions ultérieures, les dépendances de bibliothèque sont copiées dans le dossier de sortie. Cela signifie que s’il n’existe aucune autre logique spécifique à la publication (telle que les projets Web), la sortie de la génération doit être déployée.

La génération requiert le fichier *project.assets.json* qui répertorie les dépendances de votre application. Le fichier est créé quand la commande [`dotnet restore`](dotnet-restore.md) est exécutée. Si le fichier de ressources est absent, les outils ne peuvent pas résoudre les assemblys de référence, ce qui entraîne des erreurs. Avec le kit de développement logiciel (SDK) .NET Core 1. x, vous deviez exécuter explicitement `dotnet restore` avant d’exécuter `dotnet build`. À compter du SDK .NET Core 2.0, `dotnet restore` s’exécute implicitement quand vous exécutez `dotnet build`. Si vous souhaitez désactiver la restauration implicite au moment d’exécuter la commande de génération, vous pouvez passer l’option `--no-restore`.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

La possibilité d’exécuter le projet ou non est déterminée par la propriété `<OutputType>` dans le fichier projet. L’exemple suivant illustre un projet qui génère du code exécutable :

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Pour produire une bibliothèque, omettez la propriété `<OutputType>` ou remplacez sa valeur par `Library`. La DLL IL d’une bibliothèque ne contient pas de points d’entrée et ne peut pas être exécutée.

### <a name="msbuild"></a>MSBuild

La commande `dotnet build` utilise MSBuild pour générer le projet. Elle prend donc en charge les builds parallèles et les builds incrémentielles. Pour plus d’informations, consultez l’article [Incremental Builds (Générations incrémentielles)](/visualstudio/msbuild/incremental-builds) .

En plus de ses options, la commande `dotnet build` accepte des options MSBuild, comme `-p` pour définir des propriétés ou `-l` pour définir un enregistreur d’événements. Pour plus d’informations sur ces options, consultez [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Ou vous pouvez également utiliser la commande [dotnet msbuild](dotnet-msbuild.md).

L’exécution de `dotnet build` est équivalente à l’exécution de `dotnet msbuild -restore`; Toutefois, le niveau de détail par défaut de la sortie est différent.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Le fichier projet ou solution à générer. Si vous ne spécifiez pas de fichier projet ou solution, MSBuild recherche dans le répertoire de travail actif un fichier dont l’extension se termine par *proj* ou *sln* et l’utilise.

## <a name="options"></a>Options

- **`-c|--configuration <CONFIGURATION>`**

  Définit la configuration de build. La valeur par défaut pour la plupart des projets est `Debug`, mais vous pouvez remplacer les paramètres de configuration de build dans votre projet.

- **`-f|--framework <FRAMEWORK>`**

  Compile pour un [framework](../../standard/frameworks.md) spécifique. Le framework doit être défini dans le [fichier projet](csproj.md).

- **`--force`**

  Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. Disponible à partir du kit SDK .NET Core 3.0.

- **`--no-dependencies`**

  Ignore les références entre projets (P2P) et génère uniquement le projet racine spécifié.

- **`--no-incremental`**

  Marque la build comme unsafe pour la génération incrémentielle. Cet indicateur désactive la compilation incrémentielle et force une regénération du graphique de dépendance du projet.

- **`--no-restore`**

  N’exécute pas de restauration implicite pendant la génération.

- **`--nologo`**

  N’affiche pas la bannière de démarrage ni le message de copyright. Disponible à partir du kit SDK .NET Core 3.0.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Répertoire dans lequel placer les fichiers binaires générés. S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.  Pour les projets avec plusieurs frameworks cibles (via la propriété `TargetFrameworks`), vous devez également définir des `--framework` lorsque vous spécifiez cette option.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Spécifie le runtime cible. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail MSBuild. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Par défaut, il s’agit de `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Définit la valeur de la propriété `$(VersionSuffix)` à utiliser lors de la génération du projet. Cela fonctionne uniquement si la propriété `$(Version)` n’est pas définie. Ensuite, `$(Version)` est défini sur `$(VersionPrefix)` combiné avec `$(VersionSuffix)`, séparés par un tiret.

## <a name="examples"></a>Exemples

- Générer un projet et ses dépendances :

  ```dotnetcli
  dotnet build
  ```

- Générer un projet et ses dépendances à l’aide de la configuration Release :

  ```dotnetcli
  dotnet build --configuration Release
  ```

- Générer un projet et ses dépendances pour un runtime spécifique (dans cet exemple, Ubuntu 18.04) :

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- Générer le projet et utiliser la source de package NuGet spécifiée pendant l’opération de restauration (SDK .NET Core 2.0 et versions ultérieures) :

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- Générez le projet et définissez la version 1.2.3.4 comme paramètre de build à l’aide de l' [option `-p` MSBuild](#msbuild):

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
