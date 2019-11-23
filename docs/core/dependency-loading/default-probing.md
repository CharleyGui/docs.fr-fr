---
title: Détection par défaut-.NET Core
description: Vue d’ensemble de la logique de sonde System. Runtime. Loader. AssemblyLoadContext. default de .NET Core pour localiser les dépendances.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031830"
---
# <a name="default-probing"></a>Détection par défaut

L’instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> est chargée de localiser les dépendances d’un assembly. Cet article décrit la logique de sondage de l’instance de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.

## <a name="host-configured-probing-properties"></a>Propriétés de détection de l’hôte configurées

Lorsque le runtime est démarré, l’hôte de Runtime fournit un ensemble de propriétés de détection nommées qui configurent des chemins d’accès de sonde <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.

Chaque propriété de détection est facultative. Si elle est présente, chaque propriété est une valeur de chaîne qui contient une liste délimitée de chemins absolus. Le délimiteur est « ; » sur Windows et «  : » sur toutes les autres plateformes.

|Nom de propriété                 |Description  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Liste des chemins d’accès aux fichiers d’assembly de plateforme et d’application. |
|`PLATFORM_RESOURCE_ROOTS`       | Liste des chemins d’accès aux répertoires dans lesquels rechercher les assemblys de ressources satellites. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Liste des chemins d’accès aux répertoires dans lesquels rechercher les bibliothèques non managées (natives).        |
|`APP_PATHS`                     | Liste des chemins d’accès aux répertoires dans lesquels rechercher des assemblys managés. |
|`APP_NI_PATHS`                  | Liste des chemins d’accès aux répertoires dans lesquels rechercher les images natives des assemblys managés. |

### <a name="how-are-the-properties-populated"></a>Comment les propriétés sont-elles renseignées ?

Il existe deux principaux scénarios pour remplir les propriétés selon que le *\<myapp >. DEPS. JSON* existe.

- Quand le fichier *\*. DEPS. JSON* est présent, il est analysé pour renseigner les propriétés de détection.
- Lorsque le fichier *\*. DEPS. JSON* n’est pas présent, le répertoire de l’application est supposé contenir toutes les dépendances. Le contenu du répertoire est utilisé pour remplir les propriétés de détection.

En outre, les fichiers *\*. DEPS. JSON* pour tous les frameworks référencés sont analysés de la même façon.

Enfin, la variable d’environnement `ADDITIONAL_DEPS` peut être utilisée pour ajouter des dépendances supplémentaires.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Comment faire consultez les propriétés de détection à partir du code managé ?

Chaque propriété est disponible en appelant la fonction <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> avec le nom de la propriété à partir du tableau ci-dessus.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Comment faire déboguer la construction des propriétés de détection ?

L’hôte du Runtime .NET Core génère des messages de trace utiles lorsque certaines variables d’environnement sont activées :

|Variable d’environnement        |Description  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Active le suivi.|
|`COREHOST_TRACEFILE=<path>` |Effectue le suivi vers un chemin d’accès de fichier au lieu du `stderr`par défaut.|
|`COREHOST_TRACE_VERBOSITY`  |Définit les commentaires de 1 (le plus bas) à 4 (le plus élevé).|

## <a name="managed-assembly-default-probing"></a>Détection par défaut de l’assembly managé

Lors de la détection de la localisation d’un assembly managé, le <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> recherche dans l’ordre suivant :

- Fichiers correspondant à la <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dans `TRUSTED_PLATFORM_ASSEMBLIES` (après la suppression des extensions de fichier).
- Fichiers d’assembly d’images natives dans `APP_NI_PATHS` avec des extensions de fichier courantes.
- Fichiers d’assembly dans `APP_PATHS` avec des extensions de fichier courantes.

## <a name="satellite-resource-assembly-probing"></a>Détection d’assembly satellite (ressource)

Pour rechercher un assembly satellite pour une culture spécifique, construisez un jeu de chemins d’accès aux fichiers.

Pour chaque chemin d’accès dans `PLATFORM_RESOURCE_ROOTS` puis `APP_PATHS`, ajoutez la chaîne de <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>, un séparateur de répertoires, la chaîne de <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> et l’extension'. dll'.

Si un fichier correspondant existe, essayez de le charger et de le retourner.

## <a name="unmanaged-native-library-probing"></a>Détection de bibliothèque non managée (Native)

Lors de la détection de la localisation d’une bibliothèque non managée, les `NATIVE_DLL_SEARCH_DIRECTORIES` sont recherchés dans la recherche d’une bibliothèque correspondante.
