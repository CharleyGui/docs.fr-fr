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
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795387"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="259be-102">CreateAssemblyEnum, fonction</span><span class="sxs-lookup"><span data-stu-id="259be-102">CreateAssemblyEnum Function</span></span>
<span data-ttu-id="259be-103">Obtient un pointeur vers une instance de [IAssemblyEnum](iassemblyenum-interface.md) qui peut énumérer les objets de l’assembly avec l' [IAssemblyName](iassemblyname-interface.md)spécifié.</span><span class="sxs-lookup"><span data-stu-id="259be-103">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="259be-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="259be-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="259be-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="259be-105">Parameters</span></span>  
 `pEnum`  
 <span data-ttu-id="259be-106">à Pointeur vers un emplacement de mémoire qui contient le `IAssemblyEnum` pointeur demandé.</span><span class="sxs-lookup"><span data-stu-id="259be-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="259be-107">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="259be-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="259be-108">`pUnkReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="259be-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="259be-109">dans `IAssemblyName` De l’assembly demandé.</span><span class="sxs-lookup"><span data-stu-id="259be-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="259be-110">Ce nom est utilisé pour filtrer l’énumération.</span><span class="sxs-lookup"><span data-stu-id="259be-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="259be-111">Elle peut avoir la valeur null pour énumérer tous les assemblys du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="259be-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="259be-112">dans Indicateurs permettant de modifier le comportement de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="259be-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="259be-113">Ce paramètre contient exactement un bit de l’énumération [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="259be-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="259be-114">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="259be-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="259be-115">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="259be-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="259be-116">Notes</span><span class="sxs-lookup"><span data-stu-id="259be-116">Remarks</span></span>  
 <span data-ttu-id="259be-117">Le `dwFlags` paramètre contient exactement un bit de l' `ASM_CACHE_FLAGS` énumération.</span><span class="sxs-lookup"><span data-stu-id="259be-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="259be-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="259be-118">Requirements</span></span>  
 <span data-ttu-id="259be-119">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="259be-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="259be-120">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="259be-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="259be-121">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="259be-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="259be-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="259be-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="259be-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="259be-123">See also</span></span>

- [<span data-ttu-id="259be-124">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="259be-124">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="259be-125">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="259be-125">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="259be-126">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="259be-126">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
