---
title: Algorithme de chargement de bibliothèque non menté - .NET Core
description: Description des détails de l’algorithme de chargement d’assemblage non menté dans .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72250036"
---
# <a name="unmanaged-native-library-loading-algorithm"></a>Algorithme de chargement de bibliothèque non gestion (indigène)

Les bibliothèques non gémanes sont situées et chargées d’un algorithme impliquant différentes étapes.

L’algorithme suivant décrit comment les `PInvoke`bibliothèques autochtones sont chargées à travers .

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`algorithme de bibliothèque de chargement

`PInvoke`utilise l’algorithme suivant lorsque vous tentez de charger un assemblage non menté :

1. Déterminer `active` <xref:System.Runtime.Loader.AssemblyLoadContext>le . Pour une bibliothèque de chargement `active` non gestion, le AssemblyLoadContext est `PInvoke`celui avec l’assemblage qui définit le .

2. Pour `active` <xref:System.Runtime.Loader.AssemblyLoadContext>le , essayez de trouver l’assemblée dans l’ordre de priorité par:
    * Vérification de son cache.

    * Appel du <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> délégué actuel <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> fixé par la fonction.

    * Appel <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> de la `active` fonction sur le AssemblyLoadContext.

    * Vérification <xref:System.AppDomain> du cache de l’instance et exécution de la [bibliothèque non gestion (native) probant](default-probing.md#unmanaged-native-library-probing) logique.

    * Relever <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> l’événement `active` pour le AssemblyLoadContext.
