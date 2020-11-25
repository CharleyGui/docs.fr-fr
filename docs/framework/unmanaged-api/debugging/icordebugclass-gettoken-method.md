---
title: ICorDebugClass::GetToken, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetToken
helpviewer_keywords:
- GetToken method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetToken method [.NET Framework debugging]
ms.assetid: ee5c848a-eac4-4462-b07a-07ccd76a75df
topic_type:
- apiref
ms.openlocfilehash: 59f450117d1a52ce7b900d9d67330fc98281afa0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728418"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="c6d53-102">ICorDebugClass::GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="c6d53-102">ICorDebugClass::GetToken Method</span></span>

<span data-ttu-id="c6d53-103">Obtient le `TypeDef` jeton de métadonnées qui référence la définition de cette classe.</span><span class="sxs-lookup"><span data-stu-id="c6d53-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6d53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6d53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6d53-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c6d53-105">Parameters</span></span>  

 `pTypeDef`  
 <span data-ttu-id="c6d53-106">à Pointeur vers un `mdTypeDef` jeton qui référence la définition de cette classe.</span><span class="sxs-lookup"><span data-stu-id="c6d53-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6d53-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c6d53-107">Requirements</span></span>  

 <span data-ttu-id="c6d53-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6d53-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6d53-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6d53-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6d53-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6d53-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6d53-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6d53-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6d53-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6d53-112">See also</span></span>

- [<span data-ttu-id="c6d53-113">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="c6d53-113">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
