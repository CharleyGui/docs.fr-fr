---
title: Algorithme de chargement d’assemblage géré - .NET Core
description: Description des détails de l’algorithme de chargement d’assemblage géré dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973501"
---
# <a name="managed-assembly-loading-algorithm"></a>Algorithme de chargement d’assemblage géré

Les assemblages gérés sont situés et chargés d’un algorithme impliquant différentes étapes.

Tous les assemblages gérés, `WinRT` à l’exception des assemblages et assemblages satellites, utilisent le même algorithme.

## <a name="when-are-managed-assemblies-loaded"></a>Quand les assemblages gérés sont-ils chargés?

Le mécanisme le plus commun pour déclencher une charge d’assemblage gérée est une référence d’assemblage statique. Ces références sont insérées par le compilateur chaque fois que le code utilise un type défini dans un autre assemblage. Ces assemblages sont`load-by-name`chargés ( ) comme nécessaire par le temps d’exécution.

L’utilisation directe d’API spécifiques déclenchera également des charges :

|API  |Description  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|La [présente](../../csharp/language-reference/keywords/this.md) instance.|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Chargez du chemin.|La [présente](../../csharp/language-reference/keywords/this.md) instance.|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Chargez de l’objet.|La [présente](../../csharp/language-reference/keywords/this.md) instance.|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Chargement du chemin <xref:System.Runtime.Loader.AssemblyLoadContext> dans une nouvelle instance|Nouvelle instance <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Chargez du <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> chemin dans l’instance.<p>Ajoute <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> un <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>gestionnaire à . Le gestionnaire chargera les dépendances de l’assemblage à partir de son répertoire.|Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Inféré de l’appelant.<p>Préférez <xref:System.Runtime.Loader.AssemblyLoadContext> les méthodes.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Chargez de l’objet dans un nouveau <xref:System.Runtime.Loader.AssemblyLoadContext> cas.|Nouvelle instance <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Inféré de l’appelant.<p>Préférez <xref:System.Type.GetType%2A?displayProperty=nameWithType> les `assemblyResolver` méthodes avec un argument.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Si `name` le type décrit un type `Load-by-name`générique qualifié d’assemblage, déclenchez un .|Inféré de l’appelant.<p>Préférez <xref:System.Type.GetType%2A?displayProperty=nameWithType> lorsque vous utilisez des noms de type qualifié d’assemblage.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Inféré de l’appelant.<p>Préférez <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> les <xref:System.Type> méthodes qui prennent un argument.|

## <a name="algorithm"></a>Algorithm

L’algorithme suivant décrit comment le temps d’exécution charge un assemblage géré.

1. Déterminer `active` <xref:System.Runtime.Loader.AssemblyLoadContext>le .

    - Pour une référence d’assemblage statique, c’est `active` <xref:System.Runtime.Loader.AssemblyLoadContext> l’instance qui a chargé l’assemblage de référence.
    - Les API `active` <xref:System.Runtime.Loader.AssemblyLoadContext> préférées rendent explicites.
    - D’autres API `active` <xref:System.Runtime.Loader.AssemblyLoadContext>inférer le . Pour ces API, la <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> propriété est utilisée. Si sa `null`valeur est, alors <xref:System.Runtime.Loader.AssemblyLoadContext> l’instance déduite est utilisée.
    - Voir la table ci-dessus.

2. Pour `Load-by-name` les méthodes, <xref:System.Runtime.Loader.AssemblyLoadContext> l’actif charge l’assemblage. Dans l’ordre de priorité par :
    - Vérification `cache-by-name`de son .

    - Appel <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> de la fonction.

    - Vérification <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> du cache des instances et exécution de la logique [de sondage par défaut d’assemblage géré.](default-probing.md#managed-assembly-default-probing)

    - Élever <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> l’événement pour l’AssembléeLoadContexte active.

    - Élever <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> l’événement.

3. Pour les autres types de `active` <xref:System.Runtime.Loader.AssemblyLoadContext> charges, les charges de l’assemblage. Dans l’ordre de priorité par :
    - Vérification `cache-by-name`de son .

    - Chargement à partir du chemin spécifié ou de l’objet d’assemblage brut.

4. Dans les deux cas, si un assemblage est nouvellement chargé, alors :
   - L'événement <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> est déclenché.
   - Une référence est ajoutée à <xref:System.Runtime.Loader.AssemblyLoadContext> l’instance de l’assemblée `cache-by-name`.

5. Si l’assemblage est trouvé, une référence `active` <xref:System.Runtime.Loader.AssemblyLoadContext> est `cache-by-name`ajoutée au besoin à l’instance .
