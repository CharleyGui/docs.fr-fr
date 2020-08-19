---
title: Détection par défaut-.NET Core
description: Vue d’ensemble de la logique de sonde System. Runtime. Loader. AssemblyLoadContext. default de .NET Core pour localiser les dépendances.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 13ce4c7de5f6ce1b76b2e61db810c0f19717540f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608416"
---
# <a name="default-probing"></a>Détection par défaut

L' <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> instance est chargée de localiser les dépendances d’un assembly. Cet article décrit la <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> logique de sondage de l’instance.

## <a name="host-configured-probing-properties"></a>Propriétés de détection de l’hôte configurées

Lorsque le runtime est démarré, l’hôte de Runtime fournit un ensemble de propriétés de détection nommées qui configurent les <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> chemins d’accès des sondes.

Chaque propriété de détection est facultative. Si elle est présente, chaque propriété est une valeur de chaîne qui contient une liste délimitée de chemins absolus. Le délimiteur est « ; » sur Windows et «  : » sur toutes les autres plateformes.

|Nom de la propriété                 |Description  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Liste des chemins d’accès aux fichiers d’assembly de plateforme et d’application. |
|`PLATFORM_RESOURCE_ROOTS`       | Liste des chemins d’accès aux répertoires dans lesquels rechercher les assemblys de ressources satellites. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Liste des chemins d’accès aux répertoires dans lesquels rechercher les bibliothèques non managées (natives).        |
|`APP_PATHS`                     | Liste des chemins d’accès aux répertoires dans lesquels rechercher des assemblys managés. |
|`APP_NI_PATHS`                  | Liste des chemins d’accès aux répertoires dans lesquels rechercher les images natives des assemblys managés. |

### <a name="how-are-the-properties-populated"></a>Comment les propriétés sont-elles renseignées ?

Il existe deux principaux scénarios pour remplir les propriétés selon que l' * \<myapp>.deps.jssur* le fichier existe.

- Lorsque le * \*.deps.jssur* le fichier est présent, il est analysé pour renseigner les propriétés de détection.
- Lorsque le * \*.deps.jssur* le fichier n’est pas présent, le répertoire de l’application est supposé contenir toutes les dépendances. Le contenu du répertoire est utilisé pour remplir les propriétés de détection.

En outre, les * \*.deps.js* des fichiers pour les infrastructures référencées sont analysées de la même façon.

Enfin, la variable `ADDITIONAL_DEPS` d’environnement peut être utilisée pour ajouter des dépendances supplémentaires.  `dotnet.exe` contient également un `--additional-deps` paramètre facultatif permettant de définir cette valeur au démarrage de l’application.

Les `APP_PATHS` Propriétés et ne `APP_NI_PATHS` sont pas remplies par défaut et sont omises pour la plupart des applications.

La liste de tous les * \*.deps.jssur* les fichiers utilisés par l’application est accessible via `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")` .

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Comment faire consultez les propriétés de détection à partir du code managé ?

Chaque propriété est disponible en appelant la <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> fonction avec le nom de la propriété à partir du tableau ci-dessus.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Comment faire déboguer la construction des propriétés de détection ?

L’hôte du Runtime .NET Core génère des messages de trace utiles lorsque certaines variables d’environnement sont activées :

|Variable d’environnement        |Description  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Active le suivi.|
|`COREHOST_TRACEFILE=<path>` |Effectue le suivi vers un chemin d’accès de fichier au lieu de la valeur par défaut `stderr` .|
|`COREHOST_TRACE_VERBOSITY`  |Définit les commentaires de 1 (le plus bas) à 4 (le plus élevé).|

## <a name="managed-assembly-default-probing"></a>Détection par défaut de l’assembly managé

Lors de la détection pour localiser un assembly managé, le se <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> présente dans l’ordre suivant :

- Fichiers correspondant <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> à la dans `TRUSTED_PLATFORM_ASSEMBLIES` (après la suppression des extensions de fichier).
- Fichiers d’assembly d’images natives dans `APP_NI_PATHS` avec des extensions de fichier courantes.
- Fichiers d’assembly dans `APP_PATHS` avec des extensions de fichier courantes.

## <a name="satellite-resource-assembly-probing"></a>Détection d’assembly satellite (ressource)

Pour rechercher un assembly satellite pour une culture spécifique, construisez un jeu de chemins d’accès aux fichiers.

Pour chaque chemin d’accès dans `PLATFORM_RESOURCE_ROOTS` `APP_PATHS` , puis, ajoutez la <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> chaîne, un séparateur de répertoires, la <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> chaîne et l’extension'. dll'.

Si un fichier correspondant existe, essayez de le charger et de le retourner.

## <a name="unmanaged-native-library-probing"></a>Détection de bibliothèque non managée (Native)

Lors de la détection de la localisation d’une bibliothèque non managée, la recherche `NATIVE_DLL_SEARCH_DIRECTORIES` d’une bibliothèque correspondante est effectuée.
