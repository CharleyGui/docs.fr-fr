---
title: ICorDebugCode::GetSize, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52ba9d5bac5e772d721d38e4e8a7ba6757d0ae2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747492"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="cf068-102">ICorDebugCode::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="cf068-102">ICorDebugCode::GetSize Method</span></span>
<span data-ttu-id="cf068-103">Obtient la taille, en octets, du code binaire représenté par « ICorDebugCode ».</span><span class="sxs-lookup"><span data-stu-id="cf068-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf068-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf068-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32    *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf068-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf068-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="cf068-106">[out] Un pointeur vers la taille, en octets, du fichier binaire de code que ce `ICorDebugCode` représente l’objet.</span><span class="sxs-lookup"><span data-stu-id="cf068-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf068-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cf068-107">Requirements</span></span>  
 <span data-ttu-id="cf068-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf068-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf068-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf068-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf068-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf068-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf068-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf068-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf068-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf068-112">See also</span></span>
