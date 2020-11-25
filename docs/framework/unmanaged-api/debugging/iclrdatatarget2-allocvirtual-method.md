---
title: ICLRDataTarget2::AllocVirtual, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.AllocVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type:
- apiref
ms.openlocfilehash: 6d3985919ea7e766db7d07e4ed81484851156ca5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723662"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="8a130-102">ICLRDataTarget2::AllocVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="8a130-102">ICLRDataTarget2::AllocVirtual Method</span></span>

<span data-ttu-id="8a130-103">Appelée par les services d’accès aux données common language runtime (CLR) pour allouer de la mémoire dans l’espace d’adressage de ce processus cible.</span><span class="sxs-lookup"><span data-stu-id="8a130-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a130-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a130-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a130-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a130-105">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="8a130-106">dans `CLRDATA_ADDRESS` Valeur qui spécifie l’adresse de départ demandée de la mémoire à allouer.</span><span class="sxs-lookup"><span data-stu-id="8a130-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="8a130-107">dans Taille, en octets, de la mémoire à allouer.</span><span class="sxs-lookup"><span data-stu-id="8a130-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="8a130-108">dans Indicateurs qui contrôlent l’allocation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="8a130-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="8a130-109">Consultez la `VirtualAlloc` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="8a130-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="8a130-110">dans Attributs de protection pour la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="8a130-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="8a130-111">Consultez la `VirtualAlloc` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="8a130-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="8a130-112">à Pointeur vers une `CLRDATA_ADDRESS` valeur qui spécifie l’adresse de départ réelle de la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="8a130-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a130-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="8a130-113">Remarks</span></span>  

 <span data-ttu-id="8a130-114">La `AllocVirtual` méthode sert de wrapper logique pour la fonction Win32 `VirtualAlloc` .</span><span class="sxs-lookup"><span data-stu-id="8a130-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="8a130-115">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="8a130-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a130-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a130-116">Requirements</span></span>  

 <span data-ttu-id="8a130-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a130-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a130-118">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="8a130-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8a130-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a130-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a130-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a130-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a130-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a130-121">See also</span></span>

- [<span data-ttu-id="8a130-122">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="8a130-122">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="8a130-123">FreeVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="8a130-123">FreeVirtual Method</span></span>](iclrdatatarget2-freevirtual-method.md)
