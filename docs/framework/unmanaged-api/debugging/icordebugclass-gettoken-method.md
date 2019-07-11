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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b944112ce0b00e84da6243e2e48917e2318b0f1c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746841"
---
# <a name="icordebugclassgettoken-method"></a><span data-ttu-id="d1275-102">ICorDebugClass::GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d1275-102">ICorDebugClass::GetToken Method</span></span>
<span data-ttu-id="d1275-103">Obtient le `TypeDef` jeton de métadonnées qui fait référence à la définition de cette classe.</span><span class="sxs-lookup"><span data-stu-id="d1275-103">Gets the `TypeDef` metadata token that references the definition of this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1275-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1275-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdTypeDef          *pTypeDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1275-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d1275-105">Parameters</span></span>  
 `pTypeDef`  
 <span data-ttu-id="d1275-106">[out] Un pointeur vers un `mdTypeDef` jeton qui fait référence à la définition de cette classe.</span><span class="sxs-lookup"><span data-stu-id="d1275-106">[out] A pointer to an `mdTypeDef` token that references the definition of this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1275-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d1275-107">Requirements</span></span>  
 <span data-ttu-id="d1275-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1275-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1275-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1275-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1275-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1275-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1275-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1275-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1275-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1275-112">See also</span></span>

- [<span data-ttu-id="d1275-113">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="d1275-113">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
