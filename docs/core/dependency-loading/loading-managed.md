---
title: Algorithme de chargement d’assembly managé-.NET Core
description: Description des détails de l’algorithme de chargement d’assembly managé dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 312a320676be6eb453697e0704ab771a6707618b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973501"
---
# <a name="managed-assembly-loading-algorithm"></a>Algorithme de chargement d’assembly managé

Les assemblys managés sont localisés et chargés à l’aide d’un algorithme impliquant différentes étapes.

Tous les assemblys managés, à l’exception des assemblys satellites et des assemblys `WinRT`, utilisent le même algorithme.

## <a name="when-are-managed-assemblies-loaded"></a>Quand les assemblys gérés sont-ils chargés ?

Le mécanisme le plus courant pour déclencher un chargement d’assembly managé est une référence d’assembly statique. Ces références sont insérées par le compilateur chaque fois que le code utilise un type défini dans un autre assembly. Ces assemblys sont chargés (`load-by-name`) en fonction des besoins du Runtime.

L’utilisation directe d’API spécifiques déclenche également des charges :

|API  |Description  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|Instance [This](../../csharp/language-reference/keywords/this.md) .|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Charger à partir du chemin d’accès.|Instance [This](../../csharp/language-reference/keywords/this.md) .|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Charger à partir de l’objet.|Instance [This](../../csharp/language-reference/keywords/this.md) .|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Charger à partir du chemin d’accès dans une nouvelle instance de <xref:System.Runtime.Loader.AssemblyLoadContext>|Nouvelle instance <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Charge à partir du chemin d’accès dans l’instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.<p>Ajoute un gestionnaire de <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> à <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>. Le gestionnaire chargera les dépendances de l’assembly à partir de son répertoire.|Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.,|Déduit de l’appelant.<p>Préférer les méthodes <xref:System.Runtime.Loader.AssemblyLoadContext>.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Charger à partir d’un objet dans une nouvelle instance de <xref:System.Runtime.Loader.AssemblyLoadContext>.|Nouvelle instance <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.,|Déduit de l’appelant.<p>Préférez <xref:System.Type.GetType%2A?displayProperty=nameWithType> méthodes avec un argument `assemblyResolver`.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Si le type `name` décrit un type générique qualifié d’assembly, déclenchez une `Load-by-name`.|Déduit de l’appelant.<p>Préférer <xref:System.Type.GetType%2A?displayProperty=nameWithType> lors de l’utilisation de noms de types qualifiés d’assembly.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.,|Déduit de l’appelant.<p>Préférez <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> méthodes qui prennent un argument <xref:System.Type>.|

## <a name="algorithm"></a>Algorithme

L’algorithme suivant décrit comment le runtime charge un assembly managé.

1. Déterminez le <xref:System.Runtime.Loader.AssemblyLoadContext>de `active`.

    - Pour une référence d’assembly statique, le `active` <xref:System.Runtime.Loader.AssemblyLoadContext> est l’instance qui a chargé l’assembly de référence.
    - Les API préférées rendent les `active` <xref:System.Runtime.Loader.AssemblyLoadContext> explicites.
    - D’autres API déduisent le <xref:System.Runtime.Loader.AssemblyLoadContext>`active`. Pour ces API, la propriété <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> est utilisée. Si sa valeur est `null`, l’instance de <xref:System.Runtime.Loader.AssemblyLoadContext> déduite est utilisée.
    - Consultez le tableau ci-dessus.

2. Pour les méthodes de `Load-by-name`, la <xref:System.Runtime.Loader.AssemblyLoadContext> active charge l’assembly. Par ordre de priorité, procédez comme suit :
    - Vérification de son `cache-by-name`.

    - Appel de la fonction <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>.

    - Vérification du cache des instances de <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> et de l’exécution de la logique de [sondage par défaut de l’assembly managé](default-probing.md#managed-assembly-default-probing) .

    - Déclenchement de l’événement <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> pour le AssemblyLoadContext actif.

    - Déclenchement de l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>.

3. Pour les autres types de charges, le `active` <xref:System.Runtime.Loader.AssemblyLoadContext> charge l’assembly. Par ordre de priorité, procédez comme suit :
    - Vérification de son `cache-by-name`.

    - Chargement à partir du chemin d’accès ou de l’objet d’assembly brut spécifié.

4. Dans les deux cas, si un assembly est nouvellement chargé, alors :
   - L'événement <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> est déclenché.
   - Une référence est ajoutée à la `cache-by-name`de l’instance de <xref:System.Runtime.Loader.AssemblyLoadContext> de l’assembly.

5. Si l’assembly est trouvé, une référence est ajoutée en fonction des besoins au `active` de l' `cache-by-name`de <xref:System.Runtime.Loader.AssemblyLoadContext> de l’instance.
