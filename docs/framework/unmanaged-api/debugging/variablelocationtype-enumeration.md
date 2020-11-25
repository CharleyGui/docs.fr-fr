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
ms.openlocfilehash: 1c65efa006a8b2f4fb4db257b4ad2cde99c4e75e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725259"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="2159b-102">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="2159b-102">VariableLocationType Enumeration</span></span>

<span data-ttu-id="2159b-103">Indique le type d’emplacement natif d’une variable.</span><span class="sxs-lookup"><span data-stu-id="2159b-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2159b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2159b-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="2159b-105">Membres</span><span class="sxs-lookup"><span data-stu-id="2159b-105">Members</span></span>  
  
|<span data-ttu-id="2159b-106">Membre</span><span class="sxs-lookup"><span data-stu-id="2159b-106">Member</span></span>|<span data-ttu-id="2159b-107">Description</span><span class="sxs-lookup"><span data-stu-id="2159b-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="2159b-108">La variable se trouve dans un registre.</span><span class="sxs-lookup"><span data-stu-id="2159b-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="2159b-109">La variable se trouve dans un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="2159b-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="2159b-110">La variable n’est pas stockée dans un registre ou un emplacement de mémoire relatif à un registre.</span><span class="sxs-lookup"><span data-stu-id="2159b-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2159b-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="2159b-111">Remarks</span></span>  

 <span data-ttu-id="2159b-112">Un membre de l' `VariableLocationType` énumération est retourné par la méthode [ICorDebugVariableHome :: GetLocationType](icordebugvariablehome-getlocationtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2159b-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2159b-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2159b-113">Requirements</span></span>  

 <span data-ttu-id="2159b-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2159b-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2159b-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2159b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2159b-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2159b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2159b-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2159b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2159b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2159b-118">See also</span></span>

- [<span data-ttu-id="2159b-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="2159b-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
