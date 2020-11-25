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
ms.openlocfilehash: 8797f77388bf4992dfb69191ce8a844a9b7fdb8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696438"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="69022-102">CorDebugJITCompilerFlagsDeprecated, énumération</span><span class="sxs-lookup"><span data-stu-id="69022-102">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>

<span data-ttu-id="69022-103">Cette énumération est obsolète.</span><span class="sxs-lookup"><span data-stu-id="69022-103">This enumeration is obsolete.</span></span> <span data-ttu-id="69022-104">Utilisez à la `CORDEBUG_JIT_DEFAULT` place le membre de l’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="69022-104">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69022-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69022-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="69022-106">Membres</span><span class="sxs-lookup"><span data-stu-id="69022-106">Members</span></span>  
  
|<span data-ttu-id="69022-107">Membre</span><span class="sxs-lookup"><span data-stu-id="69022-107">Member</span></span>|<span data-ttu-id="69022-108">Description</span><span class="sxs-lookup"><span data-stu-id="69022-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="69022-109">Utilisez plutôt `CORDEBUG_JIT_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="69022-109">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69022-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="69022-110">Requirements</span></span>  

 <span data-ttu-id="69022-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69022-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69022-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69022-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69022-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69022-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69022-114">**Versions de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="69022-114">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69022-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69022-115">See also</span></span>

- [<span data-ttu-id="69022-116">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="69022-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
