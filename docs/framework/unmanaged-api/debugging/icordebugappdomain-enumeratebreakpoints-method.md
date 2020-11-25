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
ms.openlocfilehash: 20c8a1987e48a88a3b8c92cf9f36fb58166cda9e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715977"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="9234b-102">ICorDebugAppDomain::EnumerateBreakpoints, méthode</span><span class="sxs-lookup"><span data-stu-id="9234b-102">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>

<span data-ttu-id="9234b-103">Obtient un énumérateur pour tous les points d’arrêt actifs dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="9234b-103">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9234b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9234b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9234b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9234b-105">Parameters</span></span>  

 `ppBreakpoints`  
 <span data-ttu-id="9234b-106">à Pointeur vers l’adresse d’un objet ICorDebugBreakpointEnum qui est l’énumérateur de tous les points d’arrêt actifs dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="9234b-106">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9234b-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="9234b-107">Remarks</span></span>  

 <span data-ttu-id="9234b-108">L’énumérateur inclut tous les types de points d’arrêt, y compris les points d’arrêt sur fonction et les points d’arrêt de données.</span><span class="sxs-lookup"><span data-stu-id="9234b-108">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9234b-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9234b-109">Requirements</span></span>  

 <span data-ttu-id="9234b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9234b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9234b-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9234b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9234b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9234b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9234b-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9234b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
