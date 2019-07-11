---
title: VariableLocationType, énumération
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2093466c78b039a06a01e2d850b88ff4543d0ab3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752458"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="32379-102">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="32379-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="32379-103">Indique le type d’emplacement native d’une variable.</span><span class="sxs-lookup"><span data-stu-id="32379-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32379-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32379-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="32379-105">Membres</span><span class="sxs-lookup"><span data-stu-id="32379-105">Members</span></span>  
  
|<span data-ttu-id="32379-106">Membre</span><span class="sxs-lookup"><span data-stu-id="32379-106">Member</span></span>|<span data-ttu-id="32379-107">Description</span><span class="sxs-lookup"><span data-stu-id="32379-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="32379-108">La variable est dans un Registre.</span><span class="sxs-lookup"><span data-stu-id="32379-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="32379-109">La variable est dans un emplacement de mémoire relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="32379-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="32379-110">La variable n’est pas stockée dans un Registre ou un emplacement de mémoire relative au Registre.</span><span class="sxs-lookup"><span data-stu-id="32379-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32379-111">Notes</span><span class="sxs-lookup"><span data-stu-id="32379-111">Remarks</span></span>  
 <span data-ttu-id="32379-112">Un membre de la `VariableLocationType` énumération est retournée par la [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="32379-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32379-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="32379-113">Requirements</span></span>  
 <span data-ttu-id="32379-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32379-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32379-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32379-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32379-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32379-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32379-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32379-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32379-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32379-118">See also</span></span>

- [<span data-ttu-id="32379-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="32379-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
