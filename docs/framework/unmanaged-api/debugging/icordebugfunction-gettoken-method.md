---
title: ICorDebugFunction::GetToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: 9aee95c554afad5b2ea3cf157fc9e62c9b7e40e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696113"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="258c0-102">ICorDebugFunction::GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="258c0-102">ICorDebugFunction::GetToken Method</span></span>

<span data-ttu-id="258c0-103">Obtient le jeton de métadonnées pour cette fonction.</span><span class="sxs-lookup"><span data-stu-id="258c0-103">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="258c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="258c0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="258c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="258c0-105">Parameters</span></span>  

 `pMethodDef`  
 <span data-ttu-id="258c0-106">à Pointeur vers un `mdMethodDef` jeton qui référence les métadonnées de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="258c0-106">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="258c0-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="258c0-107">Requirements</span></span>  

 <span data-ttu-id="258c0-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="258c0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="258c0-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="258c0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="258c0-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="258c0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="258c0-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="258c0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
