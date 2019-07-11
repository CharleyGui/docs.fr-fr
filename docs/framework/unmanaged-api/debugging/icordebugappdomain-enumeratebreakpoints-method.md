---
title: ICorDebugAppDomain::EnumerateBreakpoints, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a683f1531ed28fbd8ef085414bb7cb365762ffde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738045"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="b9689-102">ICorDebugAppDomain::EnumerateBreakpoints, méthode</span><span class="sxs-lookup"><span data-stu-id="b9689-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="b9689-103">Obtient un énumérateur pour tous les points d’arrêt actifs dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b9689-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9689-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9689-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9689-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9689-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="b9689-106">[out] Pointeur vers l’adresse d’un objet ICorDebugBreakpointEnum qui est l’énumérateur pour tous les points d’arrêt actifs dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="b9689-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9689-107">Notes</span><span class="sxs-lookup"><span data-stu-id="b9689-107">Remarks</span></span>  
 <span data-ttu-id="b9689-108">L’énumérateur inclut tous les types de points d’arrêt, y compris les points d’arrêt de la fonction et les points d’arrêt de données.</span><span class="sxs-lookup"><span data-stu-id="b9689-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9689-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b9689-109">Requirements</span></span>  
 <span data-ttu-id="b9689-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9689-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9689-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9689-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9689-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9689-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9689-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9689-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
