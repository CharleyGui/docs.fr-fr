---
title: 'ICorDebugVariableHome :: GetOffset,, méthode'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: 3af8c925b80b9fd4ed0a46d2bd50fe37a6f3154a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125094"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="5e123-102">ICorDebugVariableHome :: GetOffset,, méthode</span><span class="sxs-lookup"><span data-stu-id="5e123-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="5e123-103">Obtient le décalage à partir du registre de base pour une variable.</span><span class="sxs-lookup"><span data-stu-id="5e123-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e123-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e123-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e123-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e123-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="5e123-106">à Offset à partir du registre de base.</span><span class="sxs-lookup"><span data-stu-id="5e123-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e123-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5e123-107">Return Value</span></span>  
 <span data-ttu-id="5e123-108">La méthode retourne les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="5e123-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="5e123-109">valeur</span><span class="sxs-lookup"><span data-stu-id="5e123-109">Value</span></span>|<span data-ttu-id="5e123-110">Description</span><span class="sxs-lookup"><span data-stu-id="5e123-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="5e123-111">La variable se trouve dans un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="5e123-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="5e123-112">La variable n’est pas dans un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="5e123-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e123-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="5e123-113">Requirements</span></span>  
 <span data-ttu-id="5e123-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e123-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e123-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e123-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e123-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e123-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e123-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e123-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e123-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e123-118">See also</span></span>

- [<span data-ttu-id="5e123-119">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="5e123-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
