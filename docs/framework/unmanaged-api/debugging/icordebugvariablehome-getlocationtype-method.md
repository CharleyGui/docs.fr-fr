---
title: ICorDebugVariableHome::GetLocationType (méthode)
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b7b95c79b41737ade42e6a9a2741f9c43a41130
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774471"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="5435a-102">ICorDebugVariableHome::GetLocationType (méthode)</span><span class="sxs-lookup"><span data-stu-id="5435a-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="5435a-103">Obtient le type d’emplacement native de la variable.</span><span class="sxs-lookup"><span data-stu-id="5435a-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5435a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5435a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5435a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5435a-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="5435a-106">[out] Pointeur vers le type d’emplacement native de la variable.</span><span class="sxs-lookup"><span data-stu-id="5435a-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="5435a-107">Consultez le [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) énumération pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="5435a-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5435a-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5435a-108">Requirements</span></span>  
 <span data-ttu-id="5435a-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5435a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5435a-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5435a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5435a-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5435a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5435a-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5435a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5435a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5435a-113">See also</span></span>

- [<span data-ttu-id="5435a-114">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="5435a-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="5435a-115">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="5435a-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
