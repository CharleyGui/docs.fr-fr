---
title: ICorDebugAppDomain::IsAttached, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.IsAttached
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type:
- apiref
ms.openlocfilehash: 898398b731832e698a43eb270bbdc63bb3867bb8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702171"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="12115-102">ICorDebugAppDomain::IsAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="12115-102">ICorDebugAppDomain::IsAttached Method</span></span>

<span data-ttu-id="12115-103">Obtient une valeur qui indique si le débogueur est attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="12115-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12115-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12115-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12115-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12115-105">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="12115-106">[out] `true` Si le débogueur est attaché au domaine d’application ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="12115-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12115-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="12115-107">Remarks</span></span>  

 <span data-ttu-id="12115-108">Les méthodes ICorDebugController ne peuvent pas être utilisées tant que le débogueur n’est pas attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="12115-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12115-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="12115-109">Requirements</span></span>  

 <span data-ttu-id="12115-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12115-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12115-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12115-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12115-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12115-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12115-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12115-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
