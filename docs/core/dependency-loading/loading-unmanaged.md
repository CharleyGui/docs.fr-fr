---
title: Algorithme de chargement de bibliothèque non managée-.NET Core
description: Description des détails de l’algorithme de chargement d’assembly non managé dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8240cb730180637393e2545f8013d3f1439be719
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70234651"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>Algorithme de chargement de bibliothèque non managée (natif)

Les bibliothèques non managées sont localisées et chargées à l’aide d’un algorithme impliquant différentes étapes.

L’algorithme suivant décrit le chargement des bibliothèques natives via `PInvoke`.

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`charger l’algorithme de la bibliothèque

`PInvoke`utilise l’algorithme suivant lors de la tentative de chargement d’un assembly non managé:

1. Déterminez `active` le <xref:System.Runtime.Loader.AssemblyLoadContext>. Pour une bibliothèque `PInvoke`de chargement non managée, `active` AssemblyLoadContext est l’appelant de.

2. Pour le `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, essayez de trouver l’assembly par ordre de priorité en procédant comme suit:
    * Vérification de son cache.

    * Appel du délégué <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> actuel défini par la <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> fonction.

    * Appel de <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> la fonction.

    * Vérification du <xref:System.AppDomain> cache de l’instance et exécution de la logique de sondage de la [bibliothèque non managée (Native)](default-probing.md#unmanaged-native-library-probing) .

    * Déclenchement de <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> l’événement pour `active` le AssemblyLoadContext.

3. Si la bibliothèque non managée est récemment chargée, l' <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> événement est déclenché.
