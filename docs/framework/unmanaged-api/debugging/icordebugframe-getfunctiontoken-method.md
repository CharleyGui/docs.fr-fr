---
title: ICorDebugFrame::GetFunctionToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
ms.openlocfilehash: e7821022e6966dbdea90d57b6899f09b2ed1964e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090524"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="74805-102">ICorDebugFrame::GetFunctionToken, méthode</span><span class="sxs-lookup"><span data-stu-id="74805-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="74805-103">Obtient le jeton de métadonnées pour la fonction qui contient le code associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="74805-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74805-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74805-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74805-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="74805-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="74805-106">à Pointeur vers un `mdMethodDef` jeton qui référence les métadonnées de la fonction.</span><span class="sxs-lookup"><span data-stu-id="74805-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74805-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="74805-107">Requirements</span></span>  
 <span data-ttu-id="74805-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74805-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74805-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74805-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74805-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74805-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74805-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74805-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
