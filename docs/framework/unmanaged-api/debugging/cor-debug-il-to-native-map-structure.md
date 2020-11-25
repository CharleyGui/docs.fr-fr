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
ms.openlocfilehash: 61544d0dfe876f35fdfbe5afa945fad0620c0eb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726650"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="1df31-102">COR_DEBUG_IL_TO_NATIVE_MAP, structure</span><span class="sxs-lookup"><span data-stu-id="1df31-102">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>

<span data-ttu-id="1df31-103">Contient les décalages qui sont utilisés pour mapper du code MSIL (Microsoft Intermediate Language) à du code natif.</span><span class="sxs-lookup"><span data-stu-id="1df31-103">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1df31-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1df31-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="1df31-105">Membres</span><span class="sxs-lookup"><span data-stu-id="1df31-105">Members</span></span>  
  
|<span data-ttu-id="1df31-106">Membre</span><span class="sxs-lookup"><span data-stu-id="1df31-106">Member</span></span>|<span data-ttu-id="1df31-107">Description</span><span class="sxs-lookup"><span data-stu-id="1df31-107">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="1df31-108">Offset du code MSIL.</span><span class="sxs-lookup"><span data-stu-id="1df31-108">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="1df31-109">Offset du début du code natif.</span><span class="sxs-lookup"><span data-stu-id="1df31-109">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="1df31-110">Offset de la fin du code natif.</span><span class="sxs-lookup"><span data-stu-id="1df31-110">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1df31-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1df31-111">Requirements</span></span>  

 <span data-ttu-id="1df31-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1df31-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1df31-113">**En-tête :** CorProf. idl, CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="1df31-113">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="1df31-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1df31-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1df31-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1df31-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df31-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1df31-116">See also</span></span>

- [<span data-ttu-id="1df31-117">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="1df31-117">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="1df31-118">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="1df31-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="1df31-119">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="1df31-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="1df31-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="1df31-120">Debugging</span></span>](index.md)
