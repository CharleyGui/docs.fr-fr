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
ms.openlocfilehash: 7f912f4b13620b567f5aa097604e98112d85f02d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711752"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="b7959-102">ICorDebugVariableHome :: GetRegister, méthode</span><span class="sxs-lookup"><span data-stu-id="b7959-102">ICorDebugVariableHome::GetRegister Method</span></span>

<span data-ttu-id="b7959-103">Obtient le Registre qui contient une variable avec un type d’emplacement `VLT_REGISTER` et le registre de base pour une variable avec un type d’emplacement `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="b7959-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7959-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7959-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7959-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7959-105">Parameters</span></span>  

 `pRegister`  
 <span data-ttu-id="b7959-106">à Valeur d’énumération CorDebugRegister qui indique le registre d’une variable avec un type d’emplacement `VLT_REGISTER` et le registre de base pour une variable avec un type d’emplacement `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="b7959-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7959-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b7959-107">Return Value</span></span>  

 <span data-ttu-id="b7959-108">La méthode retourne les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="b7959-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="b7959-109">Value</span><span class="sxs-lookup"><span data-stu-id="b7959-109">Value</span></span>|<span data-ttu-id="b7959-110">Description</span><span class="sxs-lookup"><span data-stu-id="b7959-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="b7959-111">La variable se trouve dans le registre indiqué par l' `pRegister` argument.</span><span class="sxs-lookup"><span data-stu-id="b7959-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="b7959-112">La variable n’est pas dans un registre ou un emplacement relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="b7959-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7959-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b7959-113">Requirements</span></span>  

 <span data-ttu-id="b7959-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7959-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7959-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7959-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7959-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7959-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7959-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7959-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7959-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7959-118">See also</span></span>

- [<span data-ttu-id="b7959-119">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="b7959-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="b7959-120">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="b7959-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
