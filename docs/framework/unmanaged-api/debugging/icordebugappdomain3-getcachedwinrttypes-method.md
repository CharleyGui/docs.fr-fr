---
title: ICorDebugAppDomain3::GetCachedWinRTTypes, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7e2685d17f3dd32db295f926fc19121d29e1752
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025912"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="7f506-102">ICorDebugAppDomain3::GetCachedWinRTTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="7f506-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="7f506-103">Obtient un énumérateur pour tous les types Windows Runtime mis en cache.</span><span class="sxs-lookup"><span data-stu-id="7f506-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f506-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f506-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f506-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7f506-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="7f506-106">[out] Un pointeur vers un [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) objet d’interface qui peut énumérer les représentations sous forme managées des types Windows Runtime actuellement chargé dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="7f506-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f506-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7f506-107">Requirements</span></span>  
 <span data-ttu-id="7f506-108">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="7f506-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="7f506-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f506-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f506-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f506-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f506-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f506-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f506-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f506-112">See also</span></span>

- [<span data-ttu-id="7f506-113">ICorDebugAppDomain3, interface</span><span class="sxs-lookup"><span data-stu-id="7f506-113">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
