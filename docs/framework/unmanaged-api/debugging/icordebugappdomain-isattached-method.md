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
ms.openlocfilehash: 30e0b0c4ed9bac4abd1dc185031e41c1e3ed014a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134673"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="778bf-102">ICorDebugAppDomain::IsAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="778bf-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="778bf-103">Obtient une valeur qui indique si le débogueur est attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="778bf-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="778bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="778bf-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="778bf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="778bf-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="778bf-106">[out] `true` si le débogueur est attaché au domaine d’application ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="778bf-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="778bf-107">Notes</span><span class="sxs-lookup"><span data-stu-id="778bf-107">Remarks</span></span>  
 <span data-ttu-id="778bf-108">Les méthodes ICorDebugController ne peuvent pas être utilisées tant que le débogueur n’est pas attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="778bf-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="778bf-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="778bf-109">Requirements</span></span>  
 <span data-ttu-id="778bf-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="778bf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="778bf-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="778bf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="778bf-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="778bf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="778bf-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="778bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
