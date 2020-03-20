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
ms.openlocfilehash: e2fa5d5a998f51e0e90cfde22b40ec12f278307b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178360"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="f7202-102">VariableLocationType, énumération</span><span class="sxs-lookup"><span data-stu-id="f7202-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="f7202-103">Indique le type d’emplacement natif d’une variable.</span><span class="sxs-lookup"><span data-stu-id="f7202-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7202-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7202-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,
    VLT_REGISTER_RELATIVE,
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="f7202-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f7202-105">Members</span></span>  
  
|<span data-ttu-id="f7202-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f7202-106">Member</span></span>|<span data-ttu-id="f7202-107">Description</span><span class="sxs-lookup"><span data-stu-id="f7202-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="f7202-108">La variable est dans un registre.</span><span class="sxs-lookup"><span data-stu-id="f7202-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="f7202-109">La variable se trouve dans un lieu de mémoire relatif au registre.</span><span class="sxs-lookup"><span data-stu-id="f7202-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="f7202-110">La variable n’est pas stockée dans un registre ou un lieu de mémoire d’enregistrement relatif.</span><span class="sxs-lookup"><span data-stu-id="f7202-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7202-111">Notes </span><span class="sxs-lookup"><span data-stu-id="f7202-111">Remarks</span></span>  
 <span data-ttu-id="f7202-112">Un membre `VariableLocationType` de l’énumération est retourné par la méthode [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) méthode.</span><span class="sxs-lookup"><span data-stu-id="f7202-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7202-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f7202-113">Requirements</span></span>  
 <span data-ttu-id="f7202-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7202-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7202-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7202-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7202-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7202-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7202-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7202-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7202-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7202-118">See also</span></span>

- [<span data-ttu-id="f7202-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="f7202-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
