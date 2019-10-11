---
title: Algorithme de chargement de bibliothèque non managée-.NET Core
description: Description des détails de l’algorithme de chargement d’assembly non managé dans .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250036"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>Algorithme de chargement de bibliothèque non managée (natif)

Les bibliothèques non managées sont localisées et chargées à l’aide d’un algorithme impliquant différentes étapes.

L’algorithme suivant décrit le chargement des bibliothèques natives par le biais de `PInvoke`.

## <a name="pinvoke-load-library-algorithm"></a>algorithme de la bibliothèque de chargement `PInvoke`

`PInvoke` utilise l’algorithme suivant lors de la tentative de chargement d’un assembly non managé :

1. Déterminez le `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Pour une bibliothèque de chargement non managée, le `active` AssemblyLoadContext est celui avec l’assembly qui définit la `PInvoke`.

2. Pour le `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, essayez de trouver l’assembly par ordre de priorité en procédant comme suit :
    * Vérification de son cache.

    * Appel du délégué <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> actuel défini par la fonction <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>.

    * Appel de la fonction <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> sur le AssemblyLoadContext `active`.

    * Vérification du cache de l’instance <xref:System.AppDomain> et exécution de la logique de sondage de la [bibliothèque non managée (Native)](default-probing.md#unmanaged-native-library-probing) .

    * Déclenchement de l’événement <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> pour le AssemblyLoadContext `active`.
