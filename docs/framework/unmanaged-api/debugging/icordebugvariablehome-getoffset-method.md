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
ms.openlocfilehash: c5d491b66e4ec64dffa4e19dabff876c9c473036
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711791"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="35cb2-102">ICorDebugVariableHome :: GetOffset,, méthode</span><span class="sxs-lookup"><span data-stu-id="35cb2-102">ICorDebugVariableHome::GetOffset Method</span></span>

<span data-ttu-id="35cb2-103">Obtient le décalage à partir du registre de base pour une variable.</span><span class="sxs-lookup"><span data-stu-id="35cb2-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35cb2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35cb2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35cb2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35cb2-105">Parameters</span></span>  

 `pOffset`  
 <span data-ttu-id="35cb2-106">à Offset à partir du registre de base.</span><span class="sxs-lookup"><span data-stu-id="35cb2-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35cb2-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="35cb2-107">Return Value</span></span>  

 <span data-ttu-id="35cb2-108">La méthode retourne les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="35cb2-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="35cb2-109">Value</span><span class="sxs-lookup"><span data-stu-id="35cb2-109">Value</span></span>|<span data-ttu-id="35cb2-110">Description</span><span class="sxs-lookup"><span data-stu-id="35cb2-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="35cb2-111">La variable se trouve dans un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="35cb2-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="35cb2-112">La variable n’est pas dans un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="35cb2-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="35cb2-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="35cb2-113">Requirements</span></span>  

 <span data-ttu-id="35cb2-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35cb2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35cb2-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35cb2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35cb2-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35cb2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35cb2-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35cb2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35cb2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35cb2-118">See also</span></span>

- [<span data-ttu-id="35cb2-119">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="35cb2-119">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
