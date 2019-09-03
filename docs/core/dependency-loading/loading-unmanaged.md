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
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="7732f-103">Algorithme de chargement de bibliothèque non managée (natif)</span><span class="sxs-lookup"><span data-stu-id="7732f-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="7732f-104">Les bibliothèques non managées sont localisées et chargées à l’aide d’un algorithme impliquant différentes étapes.</span><span class="sxs-lookup"><span data-stu-id="7732f-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="7732f-105">L’algorithme suivant décrit le chargement des bibliothèques natives via `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="7732f-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="7732f-106">`PInvoke`charger l’algorithme de la bibliothèque</span><span class="sxs-lookup"><span data-stu-id="7732f-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="7732f-107">`PInvoke`utilise l’algorithme suivant lors de la tentative de chargement d’un assembly non managé:</span><span class="sxs-lookup"><span data-stu-id="7732f-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="7732f-108">Déterminez `active` le <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="7732f-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="7732f-109">Pour une bibliothèque `PInvoke`de chargement non managée, `active` AssemblyLoadContext est l’appelant de.</span><span class="sxs-lookup"><span data-stu-id="7732f-109">For an unmanaged load library, the `active` AssemblyLoadContext is the caller of the `PInvoke`.</span></span>

2. <span data-ttu-id="7732f-110">Pour le `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, essayez de trouver l’assembly par ordre de priorité en procédant comme suit:</span><span class="sxs-lookup"><span data-stu-id="7732f-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="7732f-111">Vérification de son cache.</span><span class="sxs-lookup"><span data-stu-id="7732f-111">Checking its cache.</span></span>

    * <span data-ttu-id="7732f-112">Appel du délégué <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> actuel défini par la <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> fonction.</span><span class="sxs-lookup"><span data-stu-id="7732f-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="7732f-113">Appel de <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> la fonction.</span><span class="sxs-lookup"><span data-stu-id="7732f-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="7732f-114">Vérification du <xref:System.AppDomain> cache de l’instance et exécution de la logique de sondage de la [bibliothèque non managée (Native)](default-probing.md#unmanaged-native-library-probing) .</span><span class="sxs-lookup"><span data-stu-id="7732f-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="7732f-115">Déclenchement de <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> l’événement pour `active` le AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="7732f-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>

3. <span data-ttu-id="7732f-116">Si la bibliothèque non managée est récemment chargée, l' <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> événement est déclenché.</span><span class="sxs-lookup"><span data-stu-id="7732f-116">If the unmanaged library is newly loaded, the <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
