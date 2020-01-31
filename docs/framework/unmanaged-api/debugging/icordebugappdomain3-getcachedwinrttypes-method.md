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
ms.openlocfilehash: 55d0b40bbdb5628f60090d9d70f7dccbebe9d58f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784997"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a><span data-ttu-id="8d5d7-102">ICorDebugAppDomain3::GetCachedWinRTTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="8d5d7-102">ICorDebugAppDomain3::GetCachedWinRTTypes Method</span></span>
<span data-ttu-id="8d5d7-103">Obtient un énumérateur pour tous les types de Windows Runtime mis en cache.</span><span class="sxs-lookup"><span data-stu-id="8d5d7-103">Gets an enumerator for all cached Windows Runtime types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d5d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d5d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d5d7-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="8d5d7-105">Parameters</span></span>  
 `ppGuidToTypeEnum`  
 <span data-ttu-id="8d5d7-106">à Pointeur vers un objet d’interface [icordebugguidtotypeenum,](icordebugguidtotypeenum-interface.md) qui peut énumérer les représentations managées des types de Windows Runtime actuellement chargés dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="8d5d7-106">[out] A pointer to an [ICorDebugGuidToTypeEnum](icordebugguidtotypeenum-interface.md) interface object that can enumerate the managed representations of Windows Runtime types currently loaded in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d5d7-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="8d5d7-107">Requirements</span></span>  
 <span data-ttu-id="8d5d7-108">**Plateformes :** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="8d5d7-108">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="8d5d7-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d5d7-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d5d7-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d5d7-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d5d7-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d5d7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d5d7-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d5d7-112">See also</span></span>

- [<span data-ttu-id="8d5d7-113">ICorDebugAppDomain3, interface</span><span class="sxs-lookup"><span data-stu-id="8d5d7-113">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
