---
title: ICorDebugFunction::GetLocalVarSigToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetLocalVarSigToken
helpviewer_keywords:
- ICorDebugFunction::GetLocalVarSigToken method [.NET Framework debugging]
- GetLocalVarSigToken method [.NET Framework debugging]
ms.assetid: 31e53494-bcc9-4981-91a4-f7e0f02cad48
topic_type:
- apiref
ms.openlocfilehash: c159a175ddd380015cc2dc21637c8b63fd3caea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137896"
---
# <a name="icordebugfunctiongetlocalvarsigtoken-method"></a><span data-ttu-id="82d9f-102">ICorDebugFunction::GetLocalVarSigToken, méthode</span><span class="sxs-lookup"><span data-stu-id="82d9f-102">ICorDebugFunction::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="82d9f-103">Obtient le jeton de métadonnées pour la signature de variable locale de la fonction qui est représentée par cette instance ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="82d9f-103">Gets the metadata token for the local variable signature of the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82d9f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVarSigToken (  
    [out] mdSignature *pmdSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82d9f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82d9f-105">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="82d9f-106">à Pointeur vers le jeton de `mdSignature` pour la signature de variable locale de cette fonction, ou `mdSignatureNil`, si cette fonction n’a pas de variables locales.</span><span class="sxs-lookup"><span data-stu-id="82d9f-106">[out] A pointer to the `mdSignature` token for the local variable signature of this function, or `mdSignatureNil`, if this function has no local variables.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82d9f-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="82d9f-107">Requirements</span></span>  
 <span data-ttu-id="82d9f-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82d9f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82d9f-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82d9f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82d9f-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82d9f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82d9f-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82d9f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
