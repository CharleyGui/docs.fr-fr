---
title: Commande dotnet publish
description: La commande dotnet publish publie votre projet .NET Core dans un répertoire.
ms.date: 05/29/2018
ms.openlocfilehash: 0653a7b1e1abd6d7ffd3d21a0410279235b43a28
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451290"
---
# <a name="dotnet-publish"></a>dotnet publish

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet publish` - Empaquette l’application et ses dépendances dans un dossier en vue d’un déploiement sur un système d’hébergement.

## <a name="synopsis"></a>Synopsis

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>Description

`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire. La sortie inclut les ressources suivantes :

- Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.
- Le fichier *.deps.json* qui inclut toutes les dépendances du projet.
- Le fichier *.runtimeconfig.json* qui spécifie le runtime partagé attendu par l’application, ainsi que d’autres options de configuration pour le runtime (par exemple, le type de garbage collection).
- Les dépendances de l’application, qui sont copiées à partir du cache NuGet dans le dossier de sortie.

La sortie de la commande `dotnet publish` est prête pour le déploiement sur un système d’hébergement (par exemple, un serveur, PC, Mac, ordinateur portable) à des fins d’exécution. Il s’agit de la seule façon officiellement prise en charge pour préparer l’application au déploiement. En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement. Pour plus d’informations, consultez la page [Déploiement d’applications .NET Core](../deploying/index.md). Pour connaître la structure des répertoires d’une application publiée, consultez la page [Structure de répertoires](/aspnet/core/hosting/directory-structure).

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

`PROJECT`

Projet à publier. Chemin et nom de fichier d’un fichier projet [C#](csproj.md), F# ou Visual Basic, ou chemin vers un répertoire qui contient un fichier projet C#, F# ou Visual Basic. Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

## <a name="options"></a>Options

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`.

`-f|--framework <FRAMEWORK>`

Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié. Le framework cible doit être spécifié dans le fichier projet.

`--force`

Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

`-h|--help`

Affiche une aide brève pour la commande.

`--manifest <PATH_TO_MANIFEST_FILE>`

Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application. Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md). Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste. Cette option est disponible à partir du SDK .NET Core 2.0.

`--no-build`

Ne génère pas le projet avant la publication. L’indicateur `--no-restore` est également défini implicitement.

`--no-dependencies`

Ignore les références entre projets et restaure uniquement le projet racine.

`--no-restore`

N’effectue pas de restauration implicite à l’exécution de la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Spécifie le chemin d’accès du répertoire de sortie. Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/publish/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]/publish/* pour un déploiement autonome.
Si le chemin est relatif, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.

`--self-contained`

Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible. Si un identificateur de runtime est spécifié, sa valeur par défaut est `true`. Pour plus d’informations sur les différents types de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publie l’application pour un runtime donné. Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#publish-self-contained). Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#publish-runtime-dependent).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`.

`-f|--framework <FRAMEWORK>`

Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié. Le framework cible doit être spécifié dans le fichier projet.

`--force`

Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

`-h|--help`

Affiche une aide brève pour la commande.

`--manifest <PATH_TO_MANIFEST_FILE>`

Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application. Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md). Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste. Cette option est disponible à partir du SDK .NET Core 2.0.

`--no-dependencies`

Ignore les références entre projets et restaure uniquement le projet racine.

`--no-restore`

N’effectue pas de restauration implicite à l’exécution de la commande.

`-o|--output <OUTPUT_DIRECTORY>`

Spécifie le chemin d’accès du répertoire de sortie. Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/publish/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]/publish/* pour un déploiement autonome.
Si le chemin est relatif, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.

`--self-contained`

Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible. Si un identificateur de runtime est spécifié, sa valeur par défaut est `true`. Pour plus d’informations sur les différents types de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publie l’application pour un runtime donné. Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#publish-self-contained). Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#publish-runtime-dependent).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut est `Debug`.

`-f|--framework <FRAMEWORK>`

Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié. Le framework cible doit être spécifié dans le fichier projet.

`-h|--help`

Affiche une aide brève pour la commande.

`--manifest <PATH_TO_MANIFEST_FILE>`

Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application. Le fichier manifeste fait partie de la sortie de la [commande `dotnet store`](dotnet-store.md). Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste. Cette option est disponible à partir du SDK .NET Core 2.0.

`-o|--output <OUTPUT_DIRECTORY>`

Spécifie le chemin d’accès du répertoire de sortie. Si aucune valeur n’est spécifiée, il s’agit par défaut de *./bin/[configuration]/[framework]/publish/* pour un déploiement dépendant du framework ou de *./bin/[configuration]/[framework]/[runtime]/publish/* pour un déploiement autonome.
Si le chemin est relatif, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publie l’application pour un runtime donné. Cette option est utilisée pour créer un [déploiement autonome (SCD)](../deploying/index.md#publish-self-contained). Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). Par défaut, vous publiez un [déploiement dépendant du framework (FDD)](../deploying/index.md#publish-runtime-dependent).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.

---

## <a name="examples"></a>Exemples

Publier le projet dans le répertoire actif :

`dotnet publish`

Publier l’application à l’aide du fichier projet spécifié :

`dotnet publish ~/projects/app1/app1.csproj`

Publier le projet dans le répertoire actif à l’aide du framework `netcoreapp1.1` :

`dotnet publish --framework netcoreapp1.1`

Publier l’application actuelle à l’aide du framework `netcoreapp1.1` et du runtime pour `OS X 10.10` (vous devez lister cet identificateur de runtime dans le fichier projet) :

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

Publier l’application actuelle, mais ne pas restaurer les références de projet à projet (P2P), seulement le projet racine durant l’opération de restauration (SDK .NET Core 2.0 et ultérieur) :

`dotnet publish --no-dependencies`

## <a name="see-also"></a>Voir aussi

- [Frameworks cibles](../../standard/frameworks.md)
- [Catalogue d’identificateurs de runtime (RID)](../rid-catalog.md)
