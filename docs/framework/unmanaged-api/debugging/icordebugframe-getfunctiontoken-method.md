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
ms.openlocfilehash: 6e214131aeb2d6d17ea4b0a730b5fc77428a7ca8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213684"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="1aa06-102">ICorDebugFrame::GetFunctionToken, méthode</span><span class="sxs-lookup"><span data-stu-id="1aa06-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="1aa06-103">Obtient le jeton de métadonnées pour la fonction qui contient le code associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="1aa06-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aa06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1aa06-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aa06-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1aa06-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="1aa06-106">à Pointeur vers un `mdMethodDef` jeton qui référence les métadonnées de la fonction.</span><span class="sxs-lookup"><span data-stu-id="1aa06-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aa06-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1aa06-107">Requirements</span></span>  
 <span data-ttu-id="1aa06-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aa06-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aa06-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1aa06-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aa06-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aa06-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aa06-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aa06-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
