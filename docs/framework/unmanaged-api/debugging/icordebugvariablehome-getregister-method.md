---
title: ICorDebugVariableHome::GetRegister (méthode)
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b3b80546095b79dc5b551a9c5e92ec15c0dddb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771788"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="ce3c4-102">ICorDebugVariableHome::GetRegister (méthode)</span><span class="sxs-lookup"><span data-stu-id="ce3c4-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="ce3c4-103">Obtient le Registre qui contient une variable avec un type d’emplacement de `VLT_REGISTER`, le Registre de base et d’une variable avec un type d’emplacement de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="ce3c4-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce3c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce3c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce3c4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce3c4-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="ce3c4-106">[out] Une valeur d’énumération CorDebugRegister qui indique le Registre pour une variable avec un type d’emplacement de `VLT_REGISTER`, le Registre de base et d’une variable avec un type d’emplacement de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="ce3c4-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce3c4-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ce3c4-107">Return Value</span></span>  
 <span data-ttu-id="ce3c4-108">La méthode retourne les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce3c4-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="ce3c4-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="ce3c4-109">Value</span></span>|<span data-ttu-id="ce3c4-110">Description</span><span class="sxs-lookup"><span data-stu-id="ce3c4-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="ce3c4-111">La variable est dans le Registre indiqué par le `pRegister` argument.</span><span class="sxs-lookup"><span data-stu-id="ce3c4-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="ce3c4-112">La variable n’est pas dans un Registre ou un emplacement relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="ce3c4-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ce3c4-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ce3c4-113">Requirements</span></span>  
 <span data-ttu-id="ce3c4-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce3c4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce3c4-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce3c4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce3c4-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce3c4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce3c4-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce3c4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce3c4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce3c4-118">See also</span></span>

- [<span data-ttu-id="ce3c4-119">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="ce3c4-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="ce3c4-120">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="ce3c4-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
