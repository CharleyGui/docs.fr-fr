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
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="31c99-103">Algorithme de chargement de bibliothèque non managée (natif)</span><span class="sxs-lookup"><span data-stu-id="31c99-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="31c99-104">Les bibliothèques non managées sont localisées et chargées à l’aide d’un algorithme impliquant différentes étapes.</span><span class="sxs-lookup"><span data-stu-id="31c99-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="31c99-105">L’algorithme suivant décrit le chargement des bibliothèques natives par le biais de `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="31c99-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="31c99-106">algorithme de la bibliothèque de chargement `PInvoke`</span><span class="sxs-lookup"><span data-stu-id="31c99-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="31c99-107">`PInvoke` utilise l’algorithme suivant lors de la tentative de chargement d’un assembly non managé :</span><span class="sxs-lookup"><span data-stu-id="31c99-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="31c99-108">Déterminez le `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="31c99-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="31c99-109">Pour une bibliothèque de chargement non managée, le `active` AssemblyLoadContext est celui avec l’assembly qui définit la `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="31c99-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="31c99-110">Pour le `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, essayez de trouver l’assembly par ordre de priorité en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="31c99-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="31c99-111">Vérification de son cache.</span><span class="sxs-lookup"><span data-stu-id="31c99-111">Checking its cache.</span></span>

    * <span data-ttu-id="31c99-112">Appel du délégué <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> actuel défini par la fonction <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="31c99-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="31c99-113">Appel de la fonction <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> sur le AssemblyLoadContext `active`.</span><span class="sxs-lookup"><span data-stu-id="31c99-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="31c99-114">Vérification du cache de l’instance <xref:System.AppDomain> et exécution de la logique de sondage de la [bibliothèque non managée (Native)](default-probing.md#unmanaged-native-library-probing) .</span><span class="sxs-lookup"><span data-stu-id="31c99-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="31c99-115">Déclenchement de l’événement <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> pour le AssemblyLoadContext `active`.</span><span class="sxs-lookup"><span data-stu-id="31c99-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
