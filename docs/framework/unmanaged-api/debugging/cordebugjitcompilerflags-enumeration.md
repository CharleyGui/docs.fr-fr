---
title: CorDebugJITCompilerFlags, énumération
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39bc1316bb7d8e2aba3390499437aadf263dac07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739848"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="cb857-102">CorDebugJITCompilerFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="cb857-102">CorDebugJITCompilerFlags Enumeration</span></span>
<span data-ttu-id="cb857-103">Contient des valeurs qui influencent le comportement du compilateur juste-à-temps managé.</span><span class="sxs-lookup"><span data-stu-id="cb857-103">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb857-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb857-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="cb857-105">Membres</span><span class="sxs-lookup"><span data-stu-id="cb857-105">Members</span></span>  
  
|<span data-ttu-id="cb857-106">Membre</span><span class="sxs-lookup"><span data-stu-id="cb857-106">Member</span></span>|<span data-ttu-id="cb857-107">Description</span><span class="sxs-lookup"><span data-stu-id="cb857-107">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="cb857-108">Spécifie que le compilateur doit suivre des données de compilation et permet des optimisations.</span><span class="sxs-lookup"><span data-stu-id="cb857-108">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="cb857-109">Spécifie que le compilateur doit suivre des données de compilation, mais désactive les optimisations.</span><span class="sxs-lookup"><span data-stu-id="cb857-109">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="cb857-110">Spécifie que le compilateur doit suivre des données de compilation, désactive les optimisations, et permet aux technologies Modifier & Continue.</span><span class="sxs-lookup"><span data-stu-id="cb857-110">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb857-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cb857-111">Requirements</span></span>  
 <span data-ttu-id="cb857-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb857-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb857-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb857-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb857-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb857-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb857-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb857-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb857-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb857-116">See also</span></span>

- [<span data-ttu-id="cb857-117">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="cb857-117">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
