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
ms.openlocfilehash: b7e3696121475885f5061bd96eb6905d7ccae734
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683171"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="e0825-102">CreateAssemblyEnum, fonction</span><span class="sxs-lookup"><span data-stu-id="e0825-102">CreateAssemblyEnum Function</span></span>

<span data-ttu-id="e0825-103">Obtient un pointeur vers une instance de [IAssemblyEnum](iassemblyenum-interface.md) qui peut énumérer les objets de l’assembly avec l' [IAssemblyName](iassemblyname-interface.md)spécifié.</span><span class="sxs-lookup"><span data-stu-id="e0825-103">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0825-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0825-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0825-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e0825-105">Parameters</span></span>  

 `pEnum`  
 <span data-ttu-id="e0825-106">à Pointeur vers un emplacement de mémoire qui contient le `IAssemblyEnum` pointeur demandé.</span><span class="sxs-lookup"><span data-stu-id="e0825-106">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="e0825-107">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="e0825-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e0825-108">`pUnkReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="e0825-108">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="e0825-109">dans `IAssemblyName` De l’assembly demandé.</span><span class="sxs-lookup"><span data-stu-id="e0825-109">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="e0825-110">Ce nom est utilisé pour filtrer l’énumération.</span><span class="sxs-lookup"><span data-stu-id="e0825-110">This name is used to filter the enumeration.</span></span> <span data-ttu-id="e0825-111">Elle peut avoir la valeur null pour énumérer tous les assemblys du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="e0825-111">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e0825-112">dans Indicateurs permettant de modifier le comportement de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e0825-112">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="e0825-113">Ce paramètre contient exactement un bit de l’énumération [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="e0825-113">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="e0825-114">dans Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="e0825-114">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="e0825-115">`pvReserved` doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="e0825-115">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0825-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="e0825-116">Remarks</span></span>  

 <span data-ttu-id="e0825-117">Le `dwFlags` paramètre contient exactement un bit de l' `ASM_CACHE_FLAGS` énumération.</span><span class="sxs-lookup"><span data-stu-id="e0825-117">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0825-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e0825-118">Requirements</span></span>  

 <span data-ttu-id="e0825-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0825-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0825-120">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e0825-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e0825-121">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0825-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0825-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0825-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0825-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0825-123">See also</span></span>

- [<span data-ttu-id="e0825-124">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="e0825-124">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="e0825-125">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="e0825-125">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="e0825-126">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="e0825-126">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
