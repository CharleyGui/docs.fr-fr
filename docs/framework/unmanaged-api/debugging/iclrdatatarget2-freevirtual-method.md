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
ms.openlocfilehash: 0a36af5b411673081e74aa243ec8e0f8f876f238
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860473"
---
# <a name="iclrdatatarget2freevirtual-method"></a><span data-ttu-id="273f9-102">ICLRDataTarget2::FreeVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="273f9-102">ICLRDataTarget2::FreeVirtual Method</span></span>
<span data-ttu-id="273f9-103">Appelée par les services d’accès aux données common language runtime (CLR) pour libérer de la mémoire qui a été précédemment allouée dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="273f9-103">Called by the common language runtime (CLR) data access services to free memory that was previously allocated in the address space of the target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="273f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="273f9-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="273f9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="273f9-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="273f9-106">dans `CLRDATA_ADDRESS` Valeur qui spécifie l’adresse de départ de la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="273f9-106">[in] A `CLRDATA_ADDRESS` value that specifies the starting address of the memory to be freed.</span></span>  
  
 `size`  
 <span data-ttu-id="273f9-107">dans Taille, en octets, de la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="273f9-107">[in] The size, in bytes, of the memory to be freed.</span></span>  
  
 `typeFlags`  
 <span data-ttu-id="273f9-108">dans Indicateurs qui contrôlent la libération de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="273f9-108">[in] Flags that control the freeing of memory.</span></span> <span data-ttu-id="273f9-109">Consultez la fonction `VirtualFree` Win32.</span><span class="sxs-lookup"><span data-stu-id="273f9-109">See the Win32 `VirtualFree` function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="273f9-110">Notes </span><span class="sxs-lookup"><span data-stu-id="273f9-110">Remarks</span></span>  
 <span data-ttu-id="273f9-111">La `FreeVirtual` méthode sert de wrapper logique pour la fonction Win32 `VirtualFree` .</span><span class="sxs-lookup"><span data-stu-id="273f9-111">The `FreeVirtual` method serves as a logical wrapper for the Win32 `VirtualFree` function.</span></span>  
  
 <span data-ttu-id="273f9-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="273f9-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="273f9-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="273f9-113">Requirements</span></span>  
 <span data-ttu-id="273f9-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="273f9-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="273f9-115">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="273f9-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="273f9-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="273f9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="273f9-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="273f9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="273f9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="273f9-118">See also</span></span>

- [<span data-ttu-id="273f9-119">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="273f9-119">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="273f9-120">AllocVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="273f9-120">AllocVirtual Method</span></span>](iclrdatatarget2-allocvirtual-method.md)
