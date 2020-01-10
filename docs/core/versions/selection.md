---
title: Sélectionner la version .NET Core à utiliser
description: Découvrez comment .NET Core recherche et choisit automatiquement les versions du runtime pour votre programme. En outre, cet article vous apprend à forcer l’utiliser d’une version spécifique.
author: thraka
ms.author: adegeo
ms.date: 06/26/2019
ms.openlocfilehash: 546725db907937dea6fe0739656fb585a8855644
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713971"
---
# <a name="select-the-net-core-version-to-use"></a>Sélectionner la version .NET Core à utiliser

Cet article explique les stratégies utilisées par les outils .NET Core, le kit SDK et le runtime pour sélectionner les versions. Ces stratégies concilient l’exécution des applications avec les versions spécifiées et la facilité de mise à niveau des machines des développeurs et des utilisateurs finaux. Voici les actions effectuées par ces stratégies :

- Déploiement facile et efficace de .NET Core, notamment des mises à jour de sécurité et de fiabilité.
- Utilisation des outils et des commandes les plus récents, indépendamment du runtime cible.

La sélection de version s’opère dans les cas suivants :

- Quand vous exécutez une commande du Kit SDK, [celui-ci utilise la dernière version installée](#the-sdk-uses-the-latest-installed-version).
- Quand vous générez un assembly, [les monikers de framework cible définissent les API au moment de la génération](#target-framework-monikers-define-build-time-apis).
- Quand vous exécutez une application .NET Core, [les applications dépendantes de la version cible de .Net Framework font l’objet d’une restauration par progression](#framework-dependent-apps-roll-forward).
- Quand vous publiez une application autonome, [les déploiements autonomes incluent le runtime sélectionné](#self-contained-deployments-include-the-selected-runtime).

Le reste de ce document examine ces quatre scénarios.

## <a name="the-sdk-uses-the-latest-installed-version"></a>Le kit SDK utilise la dernière version installée

Les commandes du kit SDK incluent `dotnet new` et `dotnet run`. L’interface CLI .NET Core doit choisir une version du Kit SDK pour chaque commande `dotnet`. Par défaut, elle utilise le dernier Kit SDK installé sur la machine, même si :

- Le projet cible une version antérieure du runtime .NET Core.
- La dernière version du Kit SDK .NET Core est une préversion.

Vous pouvez tirer parti des fonctionnalités et des améliorations du dernier kit SDK tout en ciblant des versions antérieures du runtime .NET Core. Vous pouvez cibler plusieurs versions du runtime de .NET Core dans différents projets en utilisant les mêmes outils du kit SDK pour tous les projets.

À de rares occasions, vous pouvez être amené à utiliser une version antérieure du kit SDK. Vous devez dans ce cas spécifier cette version dans un [ fichier *global.json*](../tools/global-json.md). La stratégie « utiliser la dernière version » signifie que vous utilisez uniquement *global.json* pour spécifier une version du kit SDK .NET Core antérieure à la dernière version installée.

*global.json* peut être placé n’importe où dans la hiérarchie des fichiers. L’interface CLI effectue une recherche vers le haut dans le répertoire du projet et s’arrête au premier fichier *global.json* trouvé. Vous pouvez contrôler les projets auxquels un fichier *global.json* donné s’applique par son emplacement dans le système de fichiers. L’interface CLI .NET recherche un fichier *global.json* de manière itérative en parcourant le chemin de bas en haut dans le répertoire de travail actif. Le premier fichier *global.json* trouvé spécifie la version utilisée. Si cette version du kit de développement logiciel (SDK) est installée, cette version est utilisée. Si le kit de développement logiciel (SDK) spécifié dans *global. JSON* est introuvable, l’interface CLI .NET utilise des [règles de correspondance](../tools/global-json.md#matching-rules) pour sélectionner un kit de développement logiciel (SDK) compatible, ou échoue si aucune n’est trouvée.

L’exemple suivant présente la syntaxe du fichier *global.json* :

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

Le processus de sélection d’une version du kit SDK est le suivant :

1. `dotnet` recherche un fichier *global.json* en remontant de manière itérative le chemin dans le répertoire de travail actif.
1. `dotnet` utilise le kit SDK spécifié dans le premier fichier *global.json* trouvé.
1. `dotnet` utilise la dernière version du kit SDK installé si aucun fichier *global.json* n’est trouvé.

Pour plus d’informations sur la sélection d’une version du kit SDK, consultez la section [Règles de correspondance](../tools/global-json.md#matching-rules) dans l’article sur *global.json*.

## <a name="target-framework-monikers-define-build-time-apis"></a>Les monikers de framework cible définissent les API au moment de la génération

Vous générez votre projet par rapport aux API définies dans un **moniker de framework cible** (TFM). Vous devez spécifier la [version cible de .Net Framework](../../standard/frameworks.md) dans le fichier projet. Définissez l’élément `TargetFramework` dans votre fichier projet comme indiqué dans l’exemple suivant :

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

Vous pouvez générer votre projet par rapport à plusieurs TFM. S’il est plus courant de définir plusieurs versions cibles de .Net Framework pour les bibliothèques, cela est également possible dans le cas des applications. Pour cela, vous devez spécifier une propriété `TargetFrameworks` (pluriel de `TargetFramework`). Les versions cibles de .Net Framework sont séparées par un point-virgule, comme le montre l’exemple suivant :

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

Un kit SDK donné prend en charge un ensemble fixe de versions de .Net Framework, plafonné à la version cible de .Net Framework du runtime qu’il intègre. Par exemple, le kit SDK .NET Core 2.0 comprend le runtime .NET Core 2.0, qui est une implémentation de la version cible de .Net Framework `netcoreapp2.0`. Le kit SDK .NET Core 2.0 prend en charge `netcoreapp1.0`, `netcoreapp1.1`, et `netcoreapp2.0`, mais pas `netcoreapp2.1` (ou version ultérieure). L’installation du kit SDK .NET Core 2.1 vise à générer pour `netcoreapp2.1`.

Les versions cibles de .Net Framework Standard sont également plafonnées à la version cible de .Net Framework du runtime intégré au kit SDK. Le kit SDK .NET Core 2.0 est plafonné à `netstandard2.0`.

## <a name="framework-dependent-apps-roll-forward"></a>Les applications dépendantes du framework font l’objet d’une restauration par progression

Lorsque vous exécutez une application à partir d’une source avec [`dotnet run`](../tools/dotnet-run.md), à partir d’un [**déploiement dépendant du framework**](../deploying/index.md#framework-dependent-deployments-fdd) avec [`dotnet myapp.dll`](../tools/dotnet.md#description), ou à partir d’un [**exécutable dépendant du framework**](../deploying/index.md#framework-dependent-executables-fde) avec `myapp.exe`, l’exécutable `dotnet` est l’**hôte** de l’application.

L’hôte choisit la dernière version de correctif installée sur la machine. Par exemple, si vous avez spécifié `netcoreapp2.0` dans votre fichier projet et que `2.0.4` est le dernier runtime .NET installé, le runtime `2.0.4` est utilisé.

Si aucune version acceptable de `2.0.*` n’est trouvée, une nouvelle version `2.*` est utilisée. Par exemple, si vous avez spécifié `netcoreapp2.0` et que seule la version `2.1.0` est installée, l’application s’exécute en utilisant le runtime `2.1.0`. Ce comportement est appelé « restauration par progression d’une version mineure ». Les versions antérieures ne sont pas non plus prises en considération. Quand aucun runtime acceptable n’est installé, l’application ne s’exécute pas.

Voici quelques exemples d’utilisation pour illustrer le comportement, si vous ciblez la version 2.0 :

- 2.0 est spécifié. La version 2.0.5 est la version de correctif installée la plus élevée. La version 2.0.5 est utilisée.
- 2.0 est spécifié. Aucune version 2.0.* n’est installée. La version 1.1.1 correspond à la version de runtime installée la plus élevée. Un message d’erreur s’affiche.
- 2.0 est spécifié. Aucune version 2.0.* n’est installée. La version 2.2.2 correspond à la version de runtime 2.x installée la plus élevée. La version 2.2.2 est utilisée.
- 2.0 est spécifié. Aucune version 2.x n’est installée. La version 3.0.0 est installée. Un message d’erreur s’affiche.

La restauration par progression de la version mineure présente un effet secondaire qui peut toucher les utilisateurs finaux. Considérez le scénario suivant :

1. L’application spécifie que 2.0 est obligatoire.
2. En cas d’exécution, la version 2.0.* n’est pas installée, mais la version 2.2.2 l’est. La version 2.2.2 sera utilisée.
3. Plus tard, l’utilisateur installe la version 2.0.5 et réexécute l’application. La version 2.0.5 sera maintenant utilisée.

Il est possible que les versions 2.0.5 et 2.2.2 se comportent différemment, en particulier dans certains scénarios comme la sérialisation de données binaires.

## <a name="self-contained-deployments-include-the-selected-runtime"></a>Les déploiements autonomes incluent le runtime sélectionné

Vous pouvez publier une application en tant que [**distribution autonome**](../deploying/index.md#self-contained-deployments-scd). Cette approche regroupe le runtime et les bibliothèques .NET Core avec votre application. Les déploiements autonomes ne dépendent pas des environnements d’exécution. La sélection de la version du runtime se produit au moment de la publication, et non au moment de l’exécution.

Le processus de publication sélectionne la dernière version de correctif de la famille de runtime donnée. Par exemple, `dotnet publish` sélectionne .NET Core 2.0.4 s’il s’agit de la dernière version de correctif de la famille du runtime .NET Core 2.0. La version cible de .Net Framework (y compris les derniers correctifs de sécurité installés) est empaquetée avec l’application.

Si la version minimale spécifiée pour une application n’est pas satisfaire, il s’agit d’une erreur. `dotnet publish` se lie à la dernière version de correctif de runtime (au sein d’une famille de version principale.secondaire donnée). `dotnet publish` ne prend pas en charge la sémantique de restauration par progression de `dotnet run`. Pour plus d’informations sur les correctifs et les déploiements autonomes, consultez l’article relatif à la [sélection de correctif de runtime](../deploying/runtime-patch-selection.md) dans le déploiement d’applications .NET Core.

Les déploiements autonomes peuvent nécessiter une version de correctif spécifique. Vous pouvez remplacer la version de correctif de runtime minimale (par une version supérieure ou inférieure) dans le fichier projet, comme indiqué dans l’exemple suivant :

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

L’élément `RuntimeFrameworkVersion` remplace la stratégie de version par défaut. Pour les déploiements autonomes, `RuntimeFrameworkVersion` spécifie la version *exacte* du framework du runtime. Pour les applications dépendantes du framework, `RuntimeFrameworkVersion` spécifie la version *minimale* requise pour le framework du runtime.
