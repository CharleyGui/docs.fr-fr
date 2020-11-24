---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: 386f975ab0bbbe804fda2bd7567acf24f69e77fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676073"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="b0e9b-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions, méthode</span><span class="sxs-lookup"><span data-stu-id="b0e9b-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>

<span data-ttu-id="b0e9b-103">Énumère les zones de mémoire spécifiées.</span><span class="sxs-lookup"><span data-stu-id="b0e9b-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0e9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0e9b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0e9b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b0e9b-105">Parameters</span></span>  

 `callback`  
 <span data-ttu-id="b0e9b-106">dans Pointeur vers une instance [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) qui est appelée par cette méthode pour chaque région de mémoire qui est énumérée pour notifier le débogueur du résultat.</span><span class="sxs-lookup"><span data-stu-id="b0e9b-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="b0e9b-107">L’énumération des régions de la mémoire se poursuit même si le rappel indique un échec.</span><span class="sxs-lookup"><span data-stu-id="b0e9b-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="b0e9b-108">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="b0e9b-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="b0e9b-109">dans Valeur de l’énumération [CLRDataEnumMemoryFlags,](clrdataenummemoryflags-enumeration.md) qui spécifie les régions de mémoire à énumérer.</span><span class="sxs-lookup"><span data-stu-id="b0e9b-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0e9b-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="b0e9b-110">Remarks</span></span>  

 <span data-ttu-id="b0e9b-111">Cette méthode utilise l’instance [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) spécifiée pour notifier les résultats à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="b0e9b-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0e9b-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b0e9b-112">Requirements</span></span>  

 <span data-ttu-id="b0e9b-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0e9b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0e9b-114">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="b0e9b-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b0e9b-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0e9b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0e9b-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0e9b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e9b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0e9b-117">See also</span></span>

- [<span data-ttu-id="b0e9b-118">ICLRDataEnumMemoryRegions, interface</span><span class="sxs-lookup"><span data-stu-id="b0e9b-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
