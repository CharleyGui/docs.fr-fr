---
title: ICorDebugDataTarget2, interface
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: aa1db39b564b987fb8d0f79d529f5af59b7e4c02
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713746"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="9f9f2-102">ICorDebugDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="9f9f2-102">ICorDebugDataTarget2 Interface</span></span>

<span data-ttu-id="9f9f2-103">Étend logiquement l’interface [ICorDebugDataTarget](icordebugdatatarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9f9f2-103">Logically extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9f9f2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9f9f2-104">Methods</span></span>  
  
|<span data-ttu-id="9f9f2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9f9f2-105">Method</span></span>|<span data-ttu-id="9f9f2-106">Description</span><span class="sxs-lookup"><span data-stu-id="9f9f2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9f9f2-107">CreateVirtualUnwinder, méthode</span><span class="sxs-lookup"><span data-stu-id="9f9f2-107">CreateVirtualUnwinder Method</span></span>](icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="9f9f2-108">Crée un dérouleur de pile qui commence le déroulement à partir d'un contexte initial (qui n'est pas forcément la feuille d'un thread).</span><span class="sxs-lookup"><span data-stu-id="9f9f2-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="9f9f2-109">EnumerateThreadIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="9f9f2-109">EnumerateThreadIDs Method</span></span>](icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="9f9f2-110">Retourne une liste des ID de threads actifs.</span><span class="sxs-lookup"><span data-stu-id="9f9f2-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="9f9f2-111">GetImageFromPointer, méthode</span><span class="sxs-lookup"><span data-stu-id="9f9f2-111">GetImageFromPointer Method</span></span>](icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="9f9f2-112">Retourne l'adresse de base et la taille d'un module à partir d'une adresse présente dans ce module.</span><span class="sxs-lookup"><span data-stu-id="9f9f2-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="9f9f2-113">GetImageLocation, méthode</span><span class="sxs-lookup"><span data-stu-id="9f9f2-113">GetImageLocation Method</span></span>](icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="9f9f2-114">Retourne le chemin d’accès d’un module à partir de l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="9f9f2-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="9f9f2-115">GetSymbolProviderForImage, méthode</span><span class="sxs-lookup"><span data-stu-id="9f9f2-115">GetSymbolProviderForImage Method</span></span>](icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="9f9f2-116">Retourne le fournisseur de symboles d'un module à partir de l'adresse de base de ce module.</span><span class="sxs-lookup"><span data-stu-id="9f9f2-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f9f2-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="9f9f2-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f9f2-118">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9f9f2-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9f9f2-119">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="9f9f2-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f9f2-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9f9f2-120">Requirements</span></span>  

 <span data-ttu-id="9f9f2-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f9f2-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f9f2-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9f9f2-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f9f2-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f9f2-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f9f2-124">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f9f2-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f9f2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f9f2-125">See also</span></span>

- [<span data-ttu-id="9f9f2-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9f9f2-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9f9f2-127">Débogage</span><span class="sxs-lookup"><span data-stu-id="9f9f2-127">Debugging</span></span>](index.md)
