---
title: ICorDebugVariableHome::GetOffset (méthode)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fdab81d499fe1508493cb0bf05a1787974a9d01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774528"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="a7c62-102">ICorDebugVariableHome::GetOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="a7c62-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="a7c62-103">Obtient le décalage à partir du Registre de base pour une variable.</span><span class="sxs-lookup"><span data-stu-id="a7c62-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7c62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7c62-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a7c62-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="a7c62-106">[out] Le décalage à partir du Registre de base.</span><span class="sxs-lookup"><span data-stu-id="a7c62-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7c62-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a7c62-107">Return Value</span></span>  
 <span data-ttu-id="a7c62-108">La méthode retourne les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="a7c62-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="a7c62-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="a7c62-109">Value</span></span>|<span data-ttu-id="a7c62-110">Description</span><span class="sxs-lookup"><span data-stu-id="a7c62-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="a7c62-111">La variable est dans un emplacement de mémoire relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="a7c62-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="a7c62-112">La variable n’est pas dans un emplacement de mémoire relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="a7c62-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7c62-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a7c62-113">Requirements</span></span>  
 <span data-ttu-id="a7c62-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7c62-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7c62-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7c62-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7c62-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7c62-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7c62-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7c62-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c62-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7c62-118">See also</span></span>

- [<span data-ttu-id="a7c62-119">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="a7c62-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
