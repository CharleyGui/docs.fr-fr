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
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="9146c-103">Algorithme de chargement de bibliothèque non gestion (indigène)</span><span class="sxs-lookup"><span data-stu-id="9146c-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="9146c-104">Les bibliothèques non gémanes sont situées et chargées d’un algorithme impliquant différentes étapes.</span><span class="sxs-lookup"><span data-stu-id="9146c-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="9146c-105">L’algorithme suivant décrit comment les `PInvoke`bibliothèques autochtones sont chargées à travers .</span><span class="sxs-lookup"><span data-stu-id="9146c-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="9146c-106">`PInvoke`algorithme de bibliothèque de chargement</span><span class="sxs-lookup"><span data-stu-id="9146c-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="9146c-107">`PInvoke`utilise l’algorithme suivant lorsque vous tentez de charger un assemblage non menté :</span><span class="sxs-lookup"><span data-stu-id="9146c-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="9146c-108">Déterminer `active` <xref:System.Runtime.Loader.AssemblyLoadContext>le .</span><span class="sxs-lookup"><span data-stu-id="9146c-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="9146c-109">Pour une bibliothèque de chargement `active` non gestion, le AssemblyLoadContext est `PInvoke`celui avec l’assemblage qui définit le .</span><span class="sxs-lookup"><span data-stu-id="9146c-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="9146c-110">Pour `active` <xref:System.Runtime.Loader.AssemblyLoadContext>le , essayez de trouver l’assemblée dans l’ordre de priorité par:</span><span class="sxs-lookup"><span data-stu-id="9146c-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="9146c-111">Vérification de son cache.</span><span class="sxs-lookup"><span data-stu-id="9146c-111">Checking its cache.</span></span>

    * <span data-ttu-id="9146c-112">Appel du <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> délégué actuel <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> fixé par la fonction.</span><span class="sxs-lookup"><span data-stu-id="9146c-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="9146c-113">Appel <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> de la `active` fonction sur le AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="9146c-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="9146c-114">Vérification <xref:System.AppDomain> du cache de l’instance et exécution de la [bibliothèque non gestion (native) probant](default-probing.md#unmanaged-native-library-probing) logique.</span><span class="sxs-lookup"><span data-stu-id="9146c-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="9146c-115">Relever <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> l’événement `active` pour le AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="9146c-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
