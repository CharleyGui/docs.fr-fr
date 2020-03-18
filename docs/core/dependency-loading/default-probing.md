---
title: Sondage par défaut - .NET Core
description: Aperçu de la logique de sondage .NET Core’s System.Runtime.Loader.AssemblyLoadContext.Default pour localiser les dépendances.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399090"
---
# <a name="default-probing"></a>Sondage par défaut

L’exemple <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> est responsable de la localisation des dépendances d’une assemblée. Cet article décrit <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> la logique de sonder de l’instance.

## <a name="host-configured-probing-properties"></a>Propriétés de sondage configurées par l’hôte

Lorsque le temps d’exécution est commencé, l’hôte de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> temps d’exécution fournit un ensemble de propriétés de sondage nommées qui configurent les trajectoires de sonde.

Chaque propriété de sondage est facultative. Si elle est présente, chaque propriété est une valeur de chaîne qui contient une liste délimitée de chemins absolus. Le délimitant est ';' sur Windows et ':' sur toutes les autres plates-formes.

|Nom de la propriété                 |Description  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Liste des trajectoires de fichiers de plate-forme et d’assemblage d’applications. |
|`PLATFORM_RESOURCE_ROOTS`       | Liste des parcours d’annuaires pour rechercher des assemblages de ressources par satellite. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Liste des parcours d’annuaires à la recherche de bibliothèques (autochtones) non gérantes.        |
|`APP_PATHS`                     | Liste des parcours d’annuaires pour rechercher des assemblages gérés. |
|`APP_NI_PATHS`                  | Liste des parcours de répertoire pour rechercher des images natives d’assemblages gérés. |

### <a name="how-are-the-properties-populated"></a>Comment les propriétés sont-elles peuplées?

Il existe deux scénarios principaux pour peupler les propriétés selon que le * \<fichier myapp>.deps.json* existe.

- Lorsque le * \*fichier .deps.json* est présent, il est analysé pour remplir les propriétés de sondage.
- Lorsque le * \*fichier .deps.json* n’est pas présent, l’annuaire de l’application est supposé contenir toutes les dépendances. Le contenu du répertoire est utilisé pour peupler les propriétés de sondage.

En outre, les * \*fichiers .deps.json* pour tous les cadres référencés sont analysés de la même façon.

Enfin, la `ADDITIONAL_DEPS` variable de l’environnement peut être utilisée pour ajouter des dépendances supplémentaires.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Comment puis-je voir les propriétés de sondage à partir de code géré?

Chaque propriété est disponible <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> en appelant la fonction avec le nom de propriété de la table ci-dessus.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Comment puis-je déboiser la construction des propriétés de sondage?

L’hôte de temps d’exécution .NET Core produira des messages de trace utiles lorsque certaines variables de l’environnement sont activées :

|Variable d’environnement        |Description  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Permet le traçage.|
|`COREHOST_TRACEFILE=<path>` |Traces à un chemin de `stderr`fichier au lieu de la valeur par défaut .|
|`COREHOST_TRACE_VERBOSITY`  |Définit la verbosité de 1 (plus bas) à 4 (le plus élevé).|

## <a name="managed-assembly-default-probing"></a>Sondage par défaut d’assemblage géré

Lorsque vous sonder pour <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> localiser un assemblage géré, les regards dans l’ordre à:

- Fichiers correspondant <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` à l’in (après la suppression des extensions de fichiers).
- Fichiers d’assemblage `APP_NI_PATHS` d’images autochtones avec des extensions de fichiers communes.
- Fichiers d’assemblage `APP_PATHS` avec extensions de fichiers communes.

## <a name="satellite-resource-assembly-probing"></a>Sondage d’assemblage par satellite (ressources)

Pour trouver un assemblage satellite pour une culture spécifique, construisez un ensemble de pistes de fichiers.

Pour chaque `PLATFORM_RESOURCE_ROOTS` chemin `APP_PATHS`dans et <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> puis , ajouter la chaîne, un séparateur de répertoire, la <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> chaîne, et l’extension '.dll'.

S’il existe un fichier correspondant, essayez de le charger et de le retourner.

## <a name="unmanaged-native-library-probing"></a>Une bibliothèque non gestion (indigène) sondage

Lorsque vous sondez pour localiser une `NATIVE_DLL_SEARCH_DIRECTORIES` bibliothèque non gémanie, les personnes sont recherchées à la recherche d’une bibliothèque assortie.
