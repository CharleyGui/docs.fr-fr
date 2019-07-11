---
title: COR_DEBUG_IL_TO_NATIVE_MAP, structure
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 238e59978bd084379fe6c0576107d674812bce8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740785"
---
# <a name="cordebugiltonativemap-structure"></a><span data-ttu-id="4e570-102">COR_DEBUG_IL_TO_NATIVE_MAP, structure</span><span class="sxs-lookup"><span data-stu-id="4e570-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>
<span data-ttu-id="4e570-103">Contient les décalages qui sont utilisés pour mapper du code MSIL (Microsoft Intermediate Language) à du code natif.</span><span class="sxs-lookup"><span data-stu-id="4e570-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e570-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e570-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="4e570-105">Membres</span><span class="sxs-lookup"><span data-stu-id="4e570-105">Members</span></span>  
  
|<span data-ttu-id="4e570-106">Membre</span><span class="sxs-lookup"><span data-stu-id="4e570-106">Member</span></span>|<span data-ttu-id="4e570-107">Description</span><span class="sxs-lookup"><span data-stu-id="4e570-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="4e570-108">Le décalage du code MSIL.</span><span class="sxs-lookup"><span data-stu-id="4e570-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="4e570-109">Le décalage du début du code natif.</span><span class="sxs-lookup"><span data-stu-id="4e570-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="4e570-110">Le décalage de la fin du code natif.</span><span class="sxs-lookup"><span data-stu-id="4e570-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4e570-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4e570-111">Requirements</span></span>  
 <span data-ttu-id="4e570-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e570-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e570-113">**En-tête :** CorProf.idl, CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="4e570-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="4e570-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e570-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e570-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e570-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e570-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e570-116">See also</span></span>

- [<span data-ttu-id="4e570-117">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="4e570-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="4e570-118">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="4e570-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="4e570-119">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="4e570-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="4e570-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="4e570-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
