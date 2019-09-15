---
title: Commande dotnet build
description: La commande dotnet build permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 08/08/2019
ms.openlocfilehash: e92555dad2bc76d8c72eca9a30be1d3a8b5924f7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988526"
---
# <a name="dotnet-build"></a>dotnet build

**Cet article s’applique à : ✓** SDK .NET Core 1.x et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nom

`dotnet build` : Génère un projet et l’ensemble de ses dépendances.

## <a name="synopsis"></a>Résumé

```console
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet build` génère le projet et ses dépendances dans un ensemble de fichiers binaires. Les fichiers binaires incluent le code du projet dans des fichiers en langage intermédiaire (IL) avec une extension *.dll* et les fichiers de symboles utilisés pour le débogage avec une extension *.pdb*. Un fichier JSON de dépendances ( *.deps.json*) est généré. Il répertorie les dépendances de l’application. Un fichier *.runtimeconfig.json* est généré. Il spécifie le runtime partagé et sa version pour l’application.

Si le projet a des dépendances tierces, comme des bibliothèques NuGet, elles sont résolues à partir du cache NuGet et ne sont pas disponibles avec la sortie générée du projet. Par conséquent, le produit de `dotnet build` ne peut pas être transféré en l’état vers un autre ordinateur pour exécution. Ce comportement contraste avec celui du .NET Framework dans lequel la génération d’un projet exécutable (une application) produit une sortie exécutable sur n’importe quel ordinateur où le .NET Framework est installé. Pour obtenir un résultat similaire dans .NET Core, vous devez utiliser la commande [dotnet publish](dotnet-publish.md). Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

La génération requiert le fichier *project.assets.json* qui répertorie les dépendances de votre application. Le fichier est créé quand la commande [`dotnet restore`](dotnet-restore.md) est exécutée. Si le fichier de ressources est absent, les outils ne peuvent pas résoudre les assemblys de référence, ce qui entraîne des erreurs. Avec le SDK .NET Core 1.x, vous deviez explicitement exécuter `dotnet restore` avant d’exécuter `dotnet build`. À compter du SDK .NET Core 2.0, `dotnet restore` s’exécute implicitement quand vous exécutez `dotnet build`. Si vous souhaitez désactiver la restauration implicite au moment d’exécuter la commande de génération, vous pouvez passer l’option `--no-restore`.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

La possibilité d’exécuter le projet ou non est déterminée par la propriété `<OutputType>` dans le fichier projet. L’exemple suivant illustre un projet qui génère du code exécutable :

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Pour générer une bibliothèque, omettez la propriété `<OutputType>`. La principale différence dans la sortie générée est que la DLL de langage intermédiaire pour une bibliothèque ne contient pas de points d’entrée et ne peut pas être exécutée.

### <a name="msbuild"></a>MSBuild

La commande `dotnet build` utilise MSBuild pour générer le projet. Elle prend donc en charge les builds parallèles et les builds incrémentielles. Pour plus d’informations, consultez l’article [Incremental Builds (Générations incrémentielles)](/visualstudio/msbuild/incremental-builds) .

En plus de ses options, la commande `dotnet build` accepte des options MSBuild, comme `-p` pour définir des propriétés ou `-l` pour définir un enregistreur d’événements. Pour plus d’informations sur ces options, consultez [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Ou vous pouvez également utiliser la commande [dotnet msbuild](dotnet-msbuild.md).

L’exécution de `dotnet msbuild -restore -target:Build` équivaut à `dotnet build`.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Le fichier projet ou solution à générer. Si vous ne spécifiez pas de fichier projet ou solution, MSBuild recherche dans le répertoire de travail actif un fichier dont l’extension se termine par *proj* ou *sln* et l’utilise.

## <a name="options"></a>Options

* **`-c|--configuration {Debug|Release}`**

  Définit la configuration de build. La valeur par défaut est `Debug`.

* **`-f|--framework <FRAMEWORK>`**

  Compile pour un [framework](../../standard/frameworks.md) spécifique. Le framework doit être défini dans le [fichier projet](csproj.md).

* **`--force`**

  Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*. Disponible à partir du kit SDK .NET Core 2.0.

* **`-h|--help`**

  Affiche une aide brève pour la commande.

* **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. Disponible à partir du kit SDK .NET Core 3.0.

* **`--no-dependencies`**

  Ignore les références entre projets (P2P) et génère uniquement le projet racine spécifié.

* **`--no-incremental`**

  Marque la build comme unsafe pour la génération incrémentielle. Cet indicateur désactive la compilation incrémentielle et force une regénération du graphique de dépendance du projet.

* **`--no-restore`**

  N’exécute pas de restauration implicite pendant la génération. Disponible à partir du kit SDK .NET Core 2.0.

* **`--nologo`**

  N’affiche pas la bannière de démarrage ni le message de copyright. Option disponible à partir du kit SDK .NET Core 3.0.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Répertoire dans lequel placer les fichiers binaires générés. Vous devez également définir `--framework` lorsque vous spécifiez cette option. S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Spécifie le runtime cible. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).

* **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail MSBuild. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Par défaut, il s’agit de `minimal`.

* **`--version-suffix <VERSION_SUFFIX>`**

  Définit la valeur de la propriété `$(VersionSuffix)` à utiliser lors de la génération du projet. Cela fonctionne uniquement si la propriété `$(Version)` n’est pas définie. Ensuite, `$(Version)` est défini sur `$(VersionPrefix)` combiné avec `$(VersionSuffix)`, séparés par un tiret.

## <a name="examples"></a>Exemples

* Générer un projet et ses dépendances :

  ```console
  dotnet build
  ```

* Générer un projet et ses dépendances à l’aide de la configuration Release :

  ```console
  dotnet build --configuration Release
  ```

* Générer un projet et ses dépendances pour un runtime spécifique (dans cet exemple, Ubuntu 18.04) :

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* Générer le projet et utiliser la source de package NuGet spécifiée pendant l’opération de restauration (SDK .NET Core 2.0 et versions ultérieures) :

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* Générer le projet et définissez la version 1.2.3.4 comme un paramètre de build à l’aide de l’`-p` [option MSBuild](#msbuild) :

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
