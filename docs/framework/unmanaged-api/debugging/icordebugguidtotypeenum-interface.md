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
ms.openlocfilehash: 149c5b09639c8809e736ade09566e7b1b530e3eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705707"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="ff8e2-102">ICorDebugGuidToTypeEnum, interface</span><span class="sxs-lookup"><span data-stu-id="ff8e2-102">ICorDebugGuidToTypeEnum Interface</span></span>

<span data-ttu-id="ff8e2-103">Fournit un énumérateur qui définit le mappage entre un jeu de GUID et leurs types correspondants, représentés par les instances ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="ff8e2-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="ff8e2-104">Cette interface hérite des méthodes de l’interface ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="ff8e2-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ff8e2-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ff8e2-105">Methods</span></span>  
  
|<span data-ttu-id="ff8e2-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="ff8e2-106">Method</span></span>|<span data-ttu-id="ff8e2-107">Description</span><span class="sxs-lookup"><span data-stu-id="ff8e2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ff8e2-108">Icordebugguidtotypeenum, :: suivant</span><span class="sxs-lookup"><span data-stu-id="ff8e2-108">ICorDebugGuidToTypeEnum::Next</span></span>](icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="ff8e2-109">Obtient le nombre spécifié d’instances [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) qui mappent les GUID aux informations de type.</span><span class="sxs-lookup"><span data-stu-id="ff8e2-109">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff8e2-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="ff8e2-110">Remarks</span></span>  

 <span data-ttu-id="ff8e2-111">Un `ICorDebugGuidToTypeEnum` objet d’interface peut être récupéré en appelant la méthode [ICorDebugAppDomain3 :: getcachedwinrttypes,](icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ff8e2-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="ff8e2-112">Un débogueur peut appeler la méthode [suivante](icordebugguidtotypeenum-next-method.md) de cette interface pour récupérer des objets [cordebugguidtotypemapping,](cordebugguidtotypemapping-structure.md) qui représentent des mappages de représentations managées de Windows Runtime types chargés dans le domaine d’application utilisé pour l’appel à la méthode [ICorDebugAppDomain3 :: getcachedwinrttypes,](icordebugappdomain3-getcachedwinrttypes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ff8e2-112">A debugger can call this interface's [Next](icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff8e2-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ff8e2-113">Requirements</span></span>  

 <span data-ttu-id="ff8e2-114">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="ff8e2-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="ff8e2-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ff8e2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff8e2-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff8e2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff8e2-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff8e2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8e2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff8e2-118">See also</span></span>

- [<span data-ttu-id="ff8e2-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ff8e2-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
