---
title: CorDebugJITCompilerFlagsDeprecated, énumération
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
ms.openlocfilehash: 39b90ba35510a5eda7b34e0a80b0e889e5804ca7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778226"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="4a1b1-102">CorDebugJITCompilerFlagsDeprecated, énumération</span><span class="sxs-lookup"><span data-stu-id="4a1b1-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>
<span data-ttu-id="4a1b1-103">Cette énumération est obsolète.</span><span class="sxs-lookup"><span data-stu-id="4a1b1-103">This enumeration is obsolete.</span></span> <span data-ttu-id="4a1b1-104">Utilisez à la place le membre `CORDEBUG_JIT_DEFAULT` de l’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4a1b1-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a1b1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a1b1-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="4a1b1-106">Members</span><span class="sxs-lookup"><span data-stu-id="4a1b1-106">Members</span></span>  
  
|<span data-ttu-id="4a1b1-107">Member</span><span class="sxs-lookup"><span data-stu-id="4a1b1-107">Member</span></span>|<span data-ttu-id="4a1b1-108">Description</span><span class="sxs-lookup"><span data-stu-id="4a1b1-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="4a1b1-109">Utilisez plutôt `CORDEBUG_JIT_DEFAULT` .</span><span class="sxs-lookup"><span data-stu-id="4a1b1-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a1b1-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="4a1b1-110">Requirements</span></span>  
 <span data-ttu-id="4a1b1-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a1b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a1b1-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a1b1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a1b1-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a1b1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a1b1-114">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="4a1b1-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a1b1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a1b1-115">See also</span></span>

- [<span data-ttu-id="4a1b1-116">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="4a1b1-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
