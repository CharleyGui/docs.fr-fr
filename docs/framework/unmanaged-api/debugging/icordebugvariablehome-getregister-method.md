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
ms.openlocfilehash: 6cf66774209bd07426872c29c15b2225421c2b4d
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396831"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="be9fb-102">ICorDebugVariableHome :: GetRegister, méthode</span><span class="sxs-lookup"><span data-stu-id="be9fb-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="be9fb-103">Obtient le Registre qui contient une variable avec un type d’emplacement `VLT_REGISTER` et le registre de base pour une variable avec un type d’emplacement `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="be9fb-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be9fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be9fb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be9fb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be9fb-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="be9fb-106">à Valeur d’énumération CorDebugRegister qui indique le registre d’une variable avec un type d’emplacement `VLT_REGISTER` et le registre de base pour une variable avec un type d’emplacement `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="be9fb-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be9fb-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="be9fb-107">Return Value</span></span>  
 <span data-ttu-id="be9fb-108">La méthode retourne les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="be9fb-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="be9fb-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="be9fb-109">Value</span></span>|<span data-ttu-id="be9fb-110">Description</span><span class="sxs-lookup"><span data-stu-id="be9fb-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="be9fb-111">La variable se trouve dans le registre indiqué par l' `pRegister` argument.</span><span class="sxs-lookup"><span data-stu-id="be9fb-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="be9fb-112">La variable n’est pas dans un registre ou un emplacement relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="be9fb-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be9fb-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="be9fb-113">Requirements</span></span>  
 <span data-ttu-id="be9fb-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be9fb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be9fb-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be9fb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be9fb-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be9fb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be9fb-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be9fb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be9fb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be9fb-118">See also</span></span>

- [<span data-ttu-id="be9fb-119">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="be9fb-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="be9fb-120">ICorDebugVariableHome, interface</span><span class="sxs-lookup"><span data-stu-id="be9fb-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
