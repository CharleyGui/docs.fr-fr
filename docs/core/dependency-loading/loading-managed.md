---
title: Algorithme de chargement d’assembly managé-.NET Core
description: Description des détails de l’algorithme de chargement d’assembly managé dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: bf95cbd0eebed064f0198ae9b0f7a4288a938f8a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70234639"
---
# <a name="managed-assembly-loading-algorithm"></a>Algorithme de chargement d’assembly managé

Les assemblys managés sont localisés et chargés à l’aide d’un algorithme impliquant différentes étapes.

Tous les assemblys managés, à `WinRT` l’exception des assemblys satellites et des assemblys, utilisent le même algorithme.

## <a name="when-are-managed-assemblies-loaded"></a>Quand les assemblys gérés sont-ils chargés?

Le mécanisme le plus courant pour déclencher un chargement d’assembly managé est une référence d’assembly statique. Ces références sont insérées par le compilateur chaque fois que le code utilise un type défini dans un autre assembly. Ces assemblys sont chargés (`load-by-name`) en fonction des besoins du Runtime.

L’utilisation directe d’API spécifiques déclenche également des charges:

|API  |Description  |`Active` <xref:System.Runtime.Loader.AssemblyLoadContext> |
|---------|---------|---------|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyName%2A?displayProperty=nameWithType>|`Load-by-name`|Instance [This](../../csharp/language-reference/keywords/this.md) .|
|<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType><p><xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromNativeImagePath%2A?displayProperty=nameWithType>|Charger à partir du chemin d’accès.|Instance [This](../../csharp/language-reference/keywords/this.md) .|
<xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromStream%2A?displayProperty=nameWithType>|Charger à partir de l’objet.|Instance [This](../../csharp/language-reference/keywords/this.md) .|
|<xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType>|Charger à partir d’un chemin <xref:System.Runtime.Loader.AssemblyLoadContext> d’accès dans une nouvelle instance|Nouvelle instance <xref:System.Runtime.Loader.AssemblyLoadContext>.|
<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>|Charge à partir du chemin <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> d’accès dans l’instance.<p>Ajoute un <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving> gestionnaire à <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>. Le gestionnaire chargera les dépendances de l’assembly à partir de son répertoire.|Instance <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.|
|<xref:System.Reflection.Assembly.Load(System.Reflection.AssemblyName)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.String)?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>|`Load-by-name`.|Déduit de l’appelant.<p>Méthodes <xref:System.Runtime.Loader.AssemblyLoadContext> conseillées.|
|<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType><p><xref:System.Reflection.Assembly.Load(System.Byte[],System.Byte[])?displayProperty=nameWithType>|Charger à partir de l’objet.|Déduit de l’appelant.<p>Méthodes <xref:System.Runtime.Loader.AssemblyLoadContext> conseillées.|
<xref:System.Type.GetType(System.String)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean)?displayProperty=nameWithType><p><xref:System.Type.GetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType>|`Load-by-name`.|Déduit de l’appelant.<p>Préférer <xref:System.Type.GetType%2A?displayProperty=nameWithType> les méthodes à `assemblyResolver` un argument.|
<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>|Si le `name` `Load-by-name`type décrit un type générique qualifié d’assembly, déclenchez.|Déduit de l’appelant.<p>Préférer <xref:System.Type.GetType%2A?displayProperty=nameWithType> lorsque vous utilisez des noms de types qualifiés d’assembly.|
<xref:System.Activator.CreateInstance(System.String,System.String)?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Object[])?displayProperty=nameWithType><p><xref:System.Activator.CreateInstance(System.String,System.String,System.Boolean,System.Reflection.BindingFlags,System.Reflection.Binder,System.Object[],System.Globalization.CultureInfo,System.Object[])?displayProperty=nameWithType>|`Load-by-name`.|Déduit de l’appelant.<p>Préférer <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> les méthodes qui <xref:System.Type> prennent un argument.|

## <a name="algorithm"></a>Algorithme

L’algorithme suivant décrit comment le runtime charge un assembly managé.

1. Déterminez `active` le <xref:System.Runtime.Loader.AssemblyLoadContext>.

    - Pour une référence d’assembly statique `active` , <xref:System.Runtime.Loader.AssemblyLoadContext> est l’instance qui a chargé l’assembly de référence.
    - `active` Les<xref:System.Runtime.Loader.AssemblyLoadContext> API préférées rendent explicite.
    - D’autres API déduisent le `active`. <xref:System.Runtime.Loader.AssemblyLoadContext> Pour ces API, la <xref:System.Runtime.Loader.AssemblyLoadContext.CurrentContextualReflectionContext?displayProperty=nameWithType> propriété est utilisée. Si sa valeur est `null`, l' <xref:System.Runtime.Loader.AssemblyLoadContext> instance déduite est utilisée.
    - Consultez le tableau ci-dessus.

2. Pour les `Load-by-name` méthodes, le actif <xref:System.Runtime.Loader.AssemblyLoadContext> charge l’assembly. Par ordre de priorité, procédez comme suit:
    - Vérification de `cache-by-name`son.

    - Appel de <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> la fonction.

    - Vérification du <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> cache des instances et exécution de la logique de [sondage par défaut](default-probing.md#managed-assembly-default-probing) de l’assembly managé.

    - Déclenchement de <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> l’événement pour le AssemblyLoadContext actif.

    - Déclenchement de <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> l’événement.

3. Pour les autres types de charges, le `active` <xref:System.Runtime.Loader.AssemblyLoadContext> charge l’assembly. Par ordre de priorité, procédez comme suit:
    - Vérification de `cache-by-name`son.

    - Chargement à partir du chemin d’accès ou de l’objet d’assembly brut spécifié.

4. Dans les deux cas, si un assembly est nouvellement chargé, alors:
   - L'événement <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> est déclenché.
   - Une référence est ajoutée au de <xref:System.Runtime.Loader.AssemblyLoadContext> `cache-by-name`l’instance de l’assembly.

5. Si l’assembly est trouvé, une référence est ajoutée si nécessaire au `active` de `cache-by-name`l' <xref:System.Runtime.Loader.AssemblyLoadContext> instance.
