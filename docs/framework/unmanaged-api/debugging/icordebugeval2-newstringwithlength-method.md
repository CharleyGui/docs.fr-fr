---
title: ICorDebugEval2::NewStringWithLength, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a90f0a0319d88654d0310530749ef35b7095e0fb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754427"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="9d0f9-102">ICorDebugEval2::NewStringWithLength, méthode</span><span class="sxs-lookup"><span data-stu-id="9d0f9-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="9d0f9-103">Crée une chaîne de la longueur spécifiée, avec le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="9d0f9-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d0f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d0f9-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d0f9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d0f9-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="9d0f9-106">[in] Pointeur vers la valeur de chaîne.</span><span class="sxs-lookup"><span data-stu-id="9d0f9-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="9d0f9-107">[in] Longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="9d0f9-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d0f9-108">Notes</span><span class="sxs-lookup"><span data-stu-id="9d0f9-108">Remarks</span></span>  
 <span data-ttu-id="9d0f9-109">Si à la fin de la chaîne de caractère null est censé être dans la chaîne managée, l’appelant de la `NewStringWithLength` méthode doit vérifier que la longueur de chaîne inclut le caractère null de fin.</span><span class="sxs-lookup"><span data-stu-id="9d0f9-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="9d0f9-110">La chaîne est toujours créée dans le domaine d’application dans lequel le thread est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9d0f9-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d0f9-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9d0f9-111">Requirements</span></span>  
 <span data-ttu-id="9d0f9-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d0f9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d0f9-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d0f9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d0f9-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d0f9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d0f9-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d0f9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
