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
ms.openlocfilehash: 455fd06dbdbfd5d9753f3d7270647a742751d804
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420654"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="189c8-102">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="189c8-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="189c8-103">Indique le type d’emplacement natif d’une variable.</span><span class="sxs-lookup"><span data-stu-id="189c8-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="189c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="189c8-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="189c8-105">Membres</span><span class="sxs-lookup"><span data-stu-id="189c8-105">Members</span></span>  
  
|<span data-ttu-id="189c8-106">Membre</span><span class="sxs-lookup"><span data-stu-id="189c8-106">Member</span></span>|<span data-ttu-id="189c8-107">Description</span><span class="sxs-lookup"><span data-stu-id="189c8-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="189c8-108">La variable se trouve dans un registre.</span><span class="sxs-lookup"><span data-stu-id="189c8-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="189c8-109">La variable se trouve dans un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="189c8-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="189c8-110">La variable n’est pas stockée dans un registre ou un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="189c8-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="189c8-111">Notes</span><span class="sxs-lookup"><span data-stu-id="189c8-111">Remarks</span></span>  
 <span data-ttu-id="189c8-112">Un membre de l' `VariableLocationType` énumération est retourné par la méthode [ICorDebugVariableHome :: GetLocationType](icordebugvariablehome-getlocationtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="189c8-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="189c8-113">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="189c8-113">Requirements</span></span>  
 <span data-ttu-id="189c8-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="189c8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="189c8-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="189c8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="189c8-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="189c8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="189c8-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="189c8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="189c8-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="189c8-118">See also</span></span>

- [<span data-ttu-id="189c8-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="189c8-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
