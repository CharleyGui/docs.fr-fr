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
ms.openlocfilehash: a2f6df7647ffe9f2adff963b6629ed29ece053c0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895165"
---
# <a name="icordebugappdomainisattached-method"></a><span data-ttu-id="d101e-102">ICorDebugAppDomain::IsAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="d101e-102">ICorDebugAppDomain::IsAttached Method</span></span>
<span data-ttu-id="d101e-103">Obtient une valeur qui indique si le débogueur est attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="d101e-103">Gets a value that indicates whether the debugger is attached to the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d101e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d101e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d101e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d101e-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="d101e-106">à `true` si le débogueur est attaché au domaine d’application ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="d101e-106">[out] `true` if the debugger is attached to the application domain; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d101e-107">Notes </span><span class="sxs-lookup"><span data-stu-id="d101e-107">Remarks</span></span>  
 <span data-ttu-id="d101e-108">Les méthodes ICorDebugController ne peuvent pas être utilisées tant que le débogueur n’est pas attaché au domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="d101e-108">The ICorDebugController methods cannot be used until the debugger attaches to the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d101e-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d101e-109">Requirements</span></span>  
 <span data-ttu-id="d101e-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d101e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d101e-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d101e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d101e-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d101e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d101e-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d101e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
