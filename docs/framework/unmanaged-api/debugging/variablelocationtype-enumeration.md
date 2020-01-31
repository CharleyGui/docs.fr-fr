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
ms.openlocfilehash: 1aa59ee559abff8006f0ac63a812e4315aa48154
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790308"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="d182e-102">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="d182e-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="d182e-103">Indique le type d’emplacement natif d’une variable.</span><span class="sxs-lookup"><span data-stu-id="d182e-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d182e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d182e-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="d182e-105">Members</span><span class="sxs-lookup"><span data-stu-id="d182e-105">Members</span></span>  
  
|<span data-ttu-id="d182e-106">Member</span><span class="sxs-lookup"><span data-stu-id="d182e-106">Member</span></span>|<span data-ttu-id="d182e-107">Description</span><span class="sxs-lookup"><span data-stu-id="d182e-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="d182e-108">La variable se trouve dans un registre.</span><span class="sxs-lookup"><span data-stu-id="d182e-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="d182e-109">La variable se trouve dans un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="d182e-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="d182e-110">La variable n’est pas stockée dans un registre ou un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="d182e-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d182e-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d182e-111">Remarks</span></span>  
 <span data-ttu-id="d182e-112">Un membre de l’énumération `VariableLocationType` est retourné par la méthode [ICorDebugVariableHome :: GetLocationType](icordebugvariablehome-getlocationtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d182e-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d182e-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d182e-113">Requirements</span></span>  
 <span data-ttu-id="d182e-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d182e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d182e-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d182e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d182e-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d182e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d182e-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d182e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d182e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d182e-118">See also</span></span>

- [<span data-ttu-id="d182e-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="d182e-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
