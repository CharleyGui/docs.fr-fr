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
ms.openlocfilehash: 7640f7fafd0bf52a302ac0da1e5df39b5da22d68
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091149"
---
# <a name="iclrdatatarget2allocvirtual-method"></a><span data-ttu-id="c0967-102">ICLRDataTarget2::AllocVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="c0967-102">ICLRDataTarget2::AllocVirtual Method</span></span>
<span data-ttu-id="c0967-103">Appelée par les services d’accès aux données common language runtime (CLR) pour allouer de la mémoire dans l’espace d’adressage de ce processus cible.</span><span class="sxs-lookup"><span data-stu-id="c0967-103">Called by the common language runtime (CLR) data access services to allocate memory in the address space of this target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0967-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0967-104">Syntax</span></span>  
  
```cpp  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0967-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0967-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="c0967-106">dans Valeur `CLRDATA_ADDRESS` qui spécifie l’adresse de départ demandée de la mémoire à allouer.</span><span class="sxs-lookup"><span data-stu-id="c0967-106">[in] A `CLRDATA_ADDRESS` value that specifies the requested starting address of the memory to be allocated.</span></span>  
  
 `size`  
 <span data-ttu-id="c0967-107">dans Taille, en octets, de la mémoire à allouer.</span><span class="sxs-lookup"><span data-stu-id="c0967-107">[in] The size, in bytes, of the memory to be allocated.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="c0967-108">dans Indicateurs qui contrôlent l’allocation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="c0967-108">[in] Flags that control the allocation of memory.</span></span> <span data-ttu-id="c0967-109">Consultez la fonction de `VirtualAlloc` Win32.</span><span class="sxs-lookup"><span data-stu-id="c0967-109">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `protectFlags`  
 <span data-ttu-id="c0967-110">dans Attributs de protection pour la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="c0967-110">[in] The protection attributes for the allocated memory.</span></span> <span data-ttu-id="c0967-111">Consultez la fonction de `VirtualAlloc` Win32.</span><span class="sxs-lookup"><span data-stu-id="c0967-111">See the Win32 `VirtualAlloc` function.</span></span>  
  
 `virt`  
 <span data-ttu-id="c0967-112">à Pointeur vers une valeur `CLRDATA_ADDRESS` qui spécifie l’adresse de départ réelle de la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="c0967-112">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the actual starting address of the allocated memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0967-113">Notes</span><span class="sxs-lookup"><span data-stu-id="c0967-113">Remarks</span></span>  
 <span data-ttu-id="c0967-114">La méthode `AllocVirtual` sert de wrapper logique pour la fonction `VirtualAlloc` Win32.</span><span class="sxs-lookup"><span data-stu-id="c0967-114">The `AllocVirtual` method serves as a logical wrapper for the Win32 `VirtualAlloc` function.</span></span>  
  
 <span data-ttu-id="c0967-115">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="c0967-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0967-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="c0967-116">Requirements</span></span>  
 <span data-ttu-id="c0967-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0967-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0967-118">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="c0967-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c0967-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0967-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0967-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0967-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0967-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0967-121">See also</span></span>

- [<span data-ttu-id="c0967-122">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="c0967-122">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="c0967-123">FreeVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="c0967-123">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
