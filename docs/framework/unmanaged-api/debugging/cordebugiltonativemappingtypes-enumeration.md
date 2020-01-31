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
ms.openlocfilehash: ddb5af486ab6fb1c8c4fabf3ccf7b43d037e1eeb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789317"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="aa71d-102">CorDebugIlToNativeMappingTypes, énumération</span><span class="sxs-lookup"><span data-stu-id="aa71d-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="aa71d-103">Indique si une plage particulière d’instructions natives, représentées par une instance de la structure COR_DEBUG_IL_TO_NATIVE_MAP, correspond à une région de code spéciale.</span><span class="sxs-lookup"><span data-stu-id="aa71d-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa71d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa71d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="aa71d-105">Members</span><span class="sxs-lookup"><span data-stu-id="aa71d-105">Members</span></span>  
  
|<span data-ttu-id="aa71d-106">Member</span><span class="sxs-lookup"><span data-stu-id="aa71d-106">Member</span></span>|<span data-ttu-id="aa71d-107">Description</span><span class="sxs-lookup"><span data-stu-id="aa71d-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="aa71d-108">La plage d’instructions natives ne correspond à aucune région de code spéciale.</span><span class="sxs-lookup"><span data-stu-id="aa71d-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="aa71d-109">La plage d’instructions natives correspond au prologue.</span><span class="sxs-lookup"><span data-stu-id="aa71d-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="aa71d-110">La plage d’instructions natives correspond à l’épilogue.</span><span class="sxs-lookup"><span data-stu-id="aa71d-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa71d-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="aa71d-111">Requirements</span></span>  
 <span data-ttu-id="aa71d-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa71d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa71d-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa71d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa71d-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa71d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa71d-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa71d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa71d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa71d-116">See also</span></span>

- [<span data-ttu-id="aa71d-117">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="aa71d-117">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="aa71d-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="aa71d-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
