---
title: CodeChunkInfo, structure
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: 11197246662a93f6a8b57c6e61e49505a9999d00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727430"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="3fecc-102">CodeChunkInfo, structure</span><span class="sxs-lookup"><span data-stu-id="3fecc-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="3fecc-103">Représente un bloc de code unique en mémoire.</span><span class="sxs-lookup"><span data-stu-id="3fecc-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fecc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fecc-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="3fecc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="3fecc-105">Members</span></span>  
  
|<span data-ttu-id="3fecc-106">Membre</span><span class="sxs-lookup"><span data-stu-id="3fecc-106">Member</span></span>|<span data-ttu-id="3fecc-107">Description</span><span class="sxs-lookup"><span data-stu-id="3fecc-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="3fecc-108">`CORDB_ADDRESS`Valeur qui spécifie l’adresse de début du bloc.</span><span class="sxs-lookup"><span data-stu-id="3fecc-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="3fecc-109">Taille, en octets, du segment.</span><span class="sxs-lookup"><span data-stu-id="3fecc-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fecc-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="3fecc-110">Remarks</span></span>  

 <span data-ttu-id="3fecc-111">Le segment de code unique est une région de code natif qui fait partie d’un objet de code tel qu’une fonction.</span><span class="sxs-lookup"><span data-stu-id="3fecc-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fecc-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3fecc-112">Requirements</span></span>  

 <span data-ttu-id="3fecc-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fecc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fecc-114">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="3fecc-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="3fecc-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fecc-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fecc-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fecc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fecc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fecc-117">See also</span></span>

- [<span data-ttu-id="3fecc-118">GetCodeChunks, méthode</span><span class="sxs-lookup"><span data-stu-id="3fecc-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="3fecc-119">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="3fecc-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3fecc-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="3fecc-120">Debugging</span></span>](index.md)
