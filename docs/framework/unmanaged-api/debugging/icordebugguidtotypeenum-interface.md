---
title: ICorDebugGuidToTypeEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22cd08154268bdf1e819a0ec0067b05a81d60b22
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025826"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="afc0d-102">ICorDebugGuidToTypeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="afc0d-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="afc0d-103">Fournit un énumérateur qui définit le mappage entre un ensemble de GUID et leurs types correspondants, qui sont représentés par des instances de ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="afc0d-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="afc0d-104">Cette interface hérite des méthodes de l’interface de ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="afc0d-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afc0d-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="afc0d-105">Methods</span></span>  
  
|<span data-ttu-id="afc0d-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="afc0d-106">Method</span></span>|<span data-ttu-id="afc0d-107">Description</span><span class="sxs-lookup"><span data-stu-id="afc0d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="afc0d-108">ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="afc0d-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="afc0d-109">Obtient le nombre spécifié de [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances qui mappent des GUID vers le type d’informations.</span><span class="sxs-lookup"><span data-stu-id="afc0d-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afc0d-110">Notes</span><span class="sxs-lookup"><span data-stu-id="afc0d-110">Remarks</span></span>  
 <span data-ttu-id="afc0d-111">Un `ICorDebugGuidToTypeEnum` objet d’interface peut être récupérée en appelant le [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="afc0d-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="afc0d-112">Un débogueur peut appeler de cette interface [suivant](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) méthode pour récupérer [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) les objets qui représentent les mappages des représentations managées des types Windows Runtime chargement dans le domaine d’application utilisé pour l’appel à la [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="afc0d-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afc0d-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="afc0d-113">Requirements</span></span>  
 <span data-ttu-id="afc0d-114">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="afc0d-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="afc0d-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afc0d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afc0d-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afc0d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afc0d-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afc0d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc0d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afc0d-118">See also</span></span>

- [<span data-ttu-id="afc0d-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="afc0d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
