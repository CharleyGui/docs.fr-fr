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
ms.openlocfilehash: 3611684a17d51fc4fdba31dd4049540039b43e8b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110517"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="25915-102">ICorDebugAppDomain::EnumerateBreakpoints, méthode</span><span class="sxs-lookup"><span data-stu-id="25915-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>
<span data-ttu-id="25915-103">Obtient un énumérateur pour tous les points d’arrêt actifs dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="25915-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25915-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25915-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25915-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="25915-105">Parameters</span></span>  
 `ppBreakpoints`  
 <span data-ttu-id="25915-106">à Pointeur vers l’adresse d’un objet ICorDebugBreakpointEnum qui est l’énumérateur de tous les points d’arrêt actifs dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="25915-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25915-107">Notes</span><span class="sxs-lookup"><span data-stu-id="25915-107">Remarks</span></span>  
 <span data-ttu-id="25915-108">L’énumérateur inclut tous les types de points d’arrêt, y compris les points d’arrêt sur fonction et les points d’arrêt de données.</span><span class="sxs-lookup"><span data-stu-id="25915-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25915-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="25915-109">Requirements</span></span>  
 <span data-ttu-id="25915-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25915-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25915-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25915-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25915-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25915-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25915-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25915-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
