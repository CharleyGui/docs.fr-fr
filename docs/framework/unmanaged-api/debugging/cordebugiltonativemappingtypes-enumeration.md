---
title: CorDebugIlToNativeMappingTypes, énumération
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: 949d04fe8d9ce492fb320fb4732677ffb35302ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132827"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="d5753-102">CorDebugIlToNativeMappingTypes, énumération</span><span class="sxs-lookup"><span data-stu-id="d5753-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="d5753-103">Indique si une plage particulière d’instructions natives, représentée par une instance de la structure COR_DEBUG_IL_TO_NATIVE_MAP, correspond à une région de code spéciale.</span><span class="sxs-lookup"><span data-stu-id="d5753-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5753-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5753-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="d5753-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d5753-105">Members</span></span>  
  
|<span data-ttu-id="d5753-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d5753-106">Member</span></span>|<span data-ttu-id="d5753-107">Description</span><span class="sxs-lookup"><span data-stu-id="d5753-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="d5753-108">La plage d’instructions natives ne correspond à aucune région de code spéciale.</span><span class="sxs-lookup"><span data-stu-id="d5753-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="d5753-109">La plage d’instructions natives correspond au prologue.</span><span class="sxs-lookup"><span data-stu-id="d5753-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="d5753-110">La plage d’instructions natives correspond à l’épilogue.</span><span class="sxs-lookup"><span data-stu-id="d5753-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5753-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="d5753-111">Requirements</span></span>  
 <span data-ttu-id="d5753-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5753-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5753-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5753-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5753-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5753-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5753-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5753-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5753-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5753-116">See also</span></span>

- [<span data-ttu-id="d5753-117">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="d5753-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="d5753-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="d5753-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
