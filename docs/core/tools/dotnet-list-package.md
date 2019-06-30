---
title: Commande dotnet list package
description: La commande 'dotnet list package' est pratique pour lister les références de packages à un projet ou à une solution.
ms.date: 06/26/2019
ms.openlocfilehash: 98cc456fff02364310cec98f0282700f7697f07e
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421949"
---
# <a name="dotnet-list-package"></a>dotnet list package

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a>Name

`dotnet list package` - Liste toutes les références de package d’un projet ou d’une solution.

## <a name="synopsis"></a>Résumé

```
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet list package` est pratique pour lister toutes les références de packages NuGet à un projet ou à une solution spécifique. Vous devez d’abord générer le projet afin d’obtenir les ressources nécessaires au traitement de cette commande. L’exemple suivant montre le résultat de la commande `dotnet list package` pour le projet [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) :

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

La colonne **Demandée** fait référence à la version du package spécifiée dans le fichier projet et peut représenter une plage. La colonne **Résolue** répertorie la version utilisée par le projet aide et représente toujours une valeur unique. Les packages affichant une lettre `(A)` en regard de leurs noms représentent des [références de package implicites](csproj.md#implicit-package-references) déduites de vos paramètres de projet (type `Sdk`, propriété `<TargetFramework>` ou `<TargetFrameworks>`, etc.)

Utilisez l’option `--outdated` pour savoir s’il existe des versions plus récentes des packages que vous utilisez dans vos projets. Par défaut, `--outdated` répertorie les derniers packages stables, sauf si la version résolue est également une version préliminaire. Pour inclure des versions préliminaires lors de l’énumération des versions plus récentes, spécifiez également l’option `--include-prerelease`. Les exemples suivants montrent le résultat de la commande `dotnet list package --outdated --include-prerelease` pour le même projet que l’exemple précédent :

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

Si vous avez besoin de savoir si votre projet comporte des dépendances transitives, utilisez l’option `--include-transitive`. Les dépendances transitives se produisent lorsque vous ajoutez un package à votre projet, qui à son tour s’appuie sur un autre package. L’exemple suivant montre le résultat de l’exécution de la commande `dotnet list package --include-transitive` pour le projet [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin), qui affiche les packages de niveau supérieur et ceux dont ils dépendent :

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

Le fichier projet ou solution à traiter. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel. Si la commande trouve plusieurs solutions ou projets, une erreur est générée.

## <a name="options"></a>Options

* **`--config <SOURCE>`**

  Sources NuGet à utiliser dans la recherche de packages plus récents. Nécessite l’option `--outdated`.

* **`--framework <FRAMEWORK>`**

  Affiche uniquement les packages applicables au [framework cible](../../standard/frameworks.md) spécifié. Pour spécifier plusieurs frameworks, exécutez l’option plusieurs fois. Par exemple : `--framework netcoreapp2.2 --framework netstandard2.0`.

* **`-h|--help`**

  Affiche une aide brève pour la commande.

* **`--highest-minor`**

  Prend en compte uniquement les packages avec un numéro de version majeure correspondant quand vous recherchez des packages plus récents. Nécessite l’option `--outdated`.

* **`--highest-patch`**

  Prend en compte uniquement les packages avec des numéros de version majeure et mineure correspondants quand vous recherchez des packages plus récents. Nécessite l’option `--outdated`.

* **`--include-prerelease`**

  Prend en compte les packages avec des préversions quand vous recherchez des packages plus récents. Nécessite l’option `--outdated`.

* **`--include-transitive`**

  Liste les packages transitifs, en plus des packages de niveau supérieur. Si vous spécifiez cette option, vous obtenez une liste des packages dont dépendent les packages de niveau supérieur.

* **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur. Par exemple, pour effectuer une authentification. Option disponible à partir du kit SDK .NET Core 3.0.

* **`--outdated`**

  Répertorie les packages avec des versions plus récentes.

* **`-s|--source <SOURCE>`**

  Sources NuGet à utiliser dans la recherche de packages plus récents. Nécessite l’option `--outdated`.

## <a name="examples"></a>Exemples

* Répertorier les références de packages d’un projet spécifique :

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* Répertorier les références de packages avec des versions plus récentes, y compris des versions préliminaires :

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* Répertorier les références de packages pour un framework cible spécifique :

  ```console
  dotnet list package --framework netcoreapp3.0
  ```
