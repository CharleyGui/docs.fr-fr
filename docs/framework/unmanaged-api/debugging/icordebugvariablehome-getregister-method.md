---
title: 'ICorDebugVariableHome :: GetRegister, méthode'
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
ms.openlocfilehash: 396dd9c017fca6dc7037b43355ba7f726d7390ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790989"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="35df8-102">ICorDebugVariableHome :: GetRegister, méthode</span><span class="sxs-lookup"><span data-stu-id="35df8-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="35df8-103">Obtient le Registre qui contient une variable avec un type d’emplacement `VLT_REGISTER`et le registre de base pour une variable avec un type d’emplacement de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="35df8-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35df8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35df8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35df8-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="35df8-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="35df8-106">à Valeur d’énumération CorDebugRegister qui indique le registre pour une variable avec un type d’emplacement de `VLT_REGISTER`, et le registre de base pour une variable avec un type d’emplacement de `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="35df8-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35df8-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="35df8-107">Return Value</span></span>  
 <span data-ttu-id="35df8-108">La méthode retourne les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="35df8-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="35df8-109">Value</span><span class="sxs-lookup"><span data-stu-id="35df8-109">Value</span></span>|<span data-ttu-id="35df8-110">Description</span><span class="sxs-lookup"><span data-stu-id="35df8-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="35df8-111">La variable se trouve dans le registre indiqué par l’argument `pRegister`.</span><span class="sxs-lookup"><span data-stu-id="35df8-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="35df8-112">La variable n’est pas dans un registre ou un emplacement relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="35df8-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="35df8-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="35df8-113">Requirements</span></span>  
 <span data-ttu-id="35df8-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35df8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35df8-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35df8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35df8-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35df8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35df8-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35df8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35df8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35df8-118">See also</span></span>

- [<span data-ttu-id="35df8-119">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="35df8-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="35df8-120">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="35df8-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
