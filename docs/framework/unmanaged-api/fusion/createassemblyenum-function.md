---
title: CreateAssemblyEnum, fonction
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c56b0168df6e4aee69b5d3e5fbbe027ca2c8974a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778440"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="7cf57-102">CreateAssemblyEnum, fonction</span><span class="sxs-lookup"><span data-stu-id="7cf57-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="7cf57-103">Obtient un pointeur vers un [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance qui peut énumérer les objets dans l’assembly avec la valeur [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7cf57-103">Gets a pointer to an [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cf57-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cf57-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7cf57-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="7cf57-106">[out] Pointeur vers un emplacement de mémoire qui contient le texte demandé `IAssemblyEnum` pointeur.</span><span class="sxs-lookup"><span data-stu-id="7cf57-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="7cf57-107">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="7cf57-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="7cf57-108">`pUnkReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="7cf57-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="7cf57-109">[in] Le `IAssemblyName` de l’assembly demandé.</span><span class="sxs-lookup"><span data-stu-id="7cf57-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="7cf57-110">Ce nom est utilisé pour filtrer l’énumération.</span><span class="sxs-lookup"><span data-stu-id="7cf57-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="7cf57-111">Il peut être null pour énumérer tous les assemblys dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="7cf57-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7cf57-112">[in] Indicateurs pour modifier le comportement de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="7cf57-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="7cf57-113">Ce paramètre contient exactement un bit en partant de la [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="7cf57-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="7cf57-114">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="7cf57-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="7cf57-115">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="7cf57-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cf57-116">Notes</span><span class="sxs-lookup"><span data-stu-id="7cf57-116">Remarks</span></span>  
 <span data-ttu-id="7cf57-117">Le `dwFlags` paramètre contient exactement un bit en partant de la `ASM_CACHE_FLAGS` énumération.</span><span class="sxs-lookup"><span data-stu-id="7cf57-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cf57-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7cf57-118">Requirements</span></span>  
 <span data-ttu-id="7cf57-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cf57-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf57-120">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7cf57-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7cf57-121">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7cf57-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7cf57-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cf57-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf57-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cf57-123">See also</span></span>

- [<span data-ttu-id="7cf57-124">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="7cf57-124">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
- [<span data-ttu-id="7cf57-125">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="7cf57-125">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="7cf57-126">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="7cf57-126">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
