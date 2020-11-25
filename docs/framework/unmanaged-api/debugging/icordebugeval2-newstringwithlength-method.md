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
ms.openlocfilehash: e5bab32f6d18c87b030f484a47bc3f1d525d2338
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729627"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="0b2c4-102">ICorDebugEval2::NewStringWithLength, méthode</span><span class="sxs-lookup"><span data-stu-id="0b2c4-102">ICorDebugEval2::NewStringWithLength Method</span></span>

<span data-ttu-id="0b2c4-103">Crée une chaîne de la longueur spécifiée, avec le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b2c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b2c4-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b2c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b2c4-105">Parameters</span></span>  

 `string`  
 <span data-ttu-id="0b2c4-106">dans Pointeur vers la valeur de chaîne.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="0b2c4-107">dans Longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b2c4-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="0b2c4-108">Remarks</span></span>  

 <span data-ttu-id="0b2c4-109">Si le caractère null de fin de la chaîne est supposé être dans la chaîne managée, l’appelant de la `NewStringWithLength` méthode doit s’assurer que la longueur de la chaîne comprend le caractère null de fin.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="0b2c4-110">La chaîne est toujours créée dans le domaine d’application dans lequel le thread est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0b2c4-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b2c4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0b2c4-111">Requirements</span></span>  

 <span data-ttu-id="0b2c4-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b2c4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b2c4-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b2c4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b2c4-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b2c4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b2c4-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b2c4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
