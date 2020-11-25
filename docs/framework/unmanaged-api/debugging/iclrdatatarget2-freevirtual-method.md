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
ms.openlocfilehash: 1fb701a40abe2dc6e51443837c07ee5ba05ddfbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723647"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="a5f22-102">ICLRDataTarget2::FreeVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="a5f22-102">ICLRDataTarget2::FreeVirtual Method</span></span>

<span data-ttu-id="a5f22-103">Appelée par les services d’accès aux données common language runtime (CLR) pour libérer de la mémoire qui a été précédemment allouée dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="a5f22-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5f22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5f22-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5f22-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5f22-105">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="a5f22-106">dans `CLRDATA_ADDRESS` Valeur qui spécifie l’adresse de départ de la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="a5f22-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="a5f22-107">dans Taille, en octets, de la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="a5f22-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="a5f22-108">dans Indicateurs qui contrôlent la libération de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="a5f22-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="a5f22-109">Consultez la `VirtualFree` fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="a5f22-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5f22-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="a5f22-110">Remarks</span></span>  

 <span data-ttu-id="a5f22-111">La `FreeVirtual` méthode sert de wrapper logique pour la fonction Win32 `VirtualFree` .</span><span class="sxs-lookup"><span data-stu-id="a5f22-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="a5f22-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="a5f22-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5f22-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a5f22-113">Requirements</span></span>  

 <span data-ttu-id="a5f22-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5f22-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5f22-115">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="a5f22-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a5f22-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5f22-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5f22-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5f22-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f22-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5f22-118">See also</span></span>

- [<span data-ttu-id="a5f22-119">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="a5f22-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="a5f22-120">AllocVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="a5f22-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
