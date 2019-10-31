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
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138531"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="28554-102">ICorDebugGuidToTypeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="28554-102">ICorDebugGuidToTypeEnum Interface</span></span>
<span data-ttu-id="28554-103">Fournit un énumérateur qui définit le mappage entre un jeu de GUID et leurs types correspondants, représentés par les instances ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="28554-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="28554-104">Cette interface hérite des méthodes de l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="28554-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28554-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="28554-105">Methods</span></span>  
  
|<span data-ttu-id="28554-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="28554-106">Method</span></span>|<span data-ttu-id="28554-107">Description</span><span class="sxs-lookup"><span data-stu-id="28554-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28554-108">Icordebugguidtotypeenum, :: suivant</span><span class="sxs-lookup"><span data-stu-id="28554-108">ICorDebugGuidToTypeEnum::Next</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="28554-109">Obtient le nombre spécifié d’instances [cordebugguidtotypemapping,](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) qui mappent les GUID aux informations de type.</span><span class="sxs-lookup"><span data-stu-id="28554-109">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28554-110">Notes</span><span class="sxs-lookup"><span data-stu-id="28554-110">Remarks</span></span>  
 <span data-ttu-id="28554-111">Un objet d’interface `ICorDebugGuidToTypeEnum` peut être récupéré en appelant la méthode [ICorDebugAppDomain3 :: getcachedwinrttypes,](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="28554-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="28554-112">Un débogueur peut appeler la méthode [suivante](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) de cette interface pour récupérer des objets [cordebugguidtotypemapping,](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) qui représentent des mappages de représentations managées de Windows Runtime types chargés dans le domaine d’application utilisé pour l’appel à l' [objet Méthode ICorDebugAppDomain3 :: Getcachedwinrttypes,](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="28554-112">A debugger can call this interface's [Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28554-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="28554-113">Requirements</span></span>  
 <span data-ttu-id="28554-114">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="28554-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="28554-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28554-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28554-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28554-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28554-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28554-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28554-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28554-118">See also</span></span>

- [<span data-ttu-id="28554-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="28554-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
