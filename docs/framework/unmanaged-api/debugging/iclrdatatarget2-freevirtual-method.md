---
title: ICLRDataTarget2::FreeVirtual, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2.FreeVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2::FreeVirtual
helpviewer_keywords:
- ICLRDataTarget::FreeVirtual method [.NET Framework debugging]
- FreeVirtual method [.NET Framework debugging]
ms.assetid: 26fb69f8-1467-4711-bd24-cb117c63938f
topic_type:
- apiref
ms.openlocfilehash: 7eda9bfff6de6b386c16ad0a188931d9d3adcb93
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793657"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="8208a-102">ICLRDataTarget2::FreeVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="8208a-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="8208a-103">Appelée par les services d’accès aux données common language runtime (CLR) pour libérer de la mémoire qui a été précédemment allouée dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="8208a-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8208a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8208a-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8208a-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="8208a-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="8208a-106">dans Valeur `CLRDATA_ADDRESS` qui spécifie l’adresse de départ de la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="8208a-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="8208a-107">dans Taille, en octets, de la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="8208a-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="8208a-108">dans Indicateurs qui contrôlent la libération de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="8208a-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="8208a-109">Consultez la fonction de `VirtualFree` Win32.</span><span class="sxs-lookup"><span data-stu-id="8208a-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8208a-110">Notes</span><span class="sxs-lookup"><span data-stu-id="8208a-110">Remarks</span></span>  
 <span data-ttu-id="8208a-111">La méthode `FreeVirtual` sert de wrapper logique pour la fonction `VirtualFree` Win32.</span><span class="sxs-lookup"><span data-stu-id="8208a-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="8208a-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="8208a-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8208a-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="8208a-113">Requirements</span></span>  
 <span data-ttu-id="8208a-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8208a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8208a-115">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="8208a-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8208a-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8208a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8208a-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8208a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8208a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8208a-118">See also</span></span>

- [<span data-ttu-id="8208a-119">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="8208a-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="8208a-120">AllocVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="8208a-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
