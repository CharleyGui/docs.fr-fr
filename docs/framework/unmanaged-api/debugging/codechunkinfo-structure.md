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
ms.openlocfilehash: d33c8b31473e389e07fb24076dc32272e9dde387
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132401"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="08237-102">CodeChunkInfo, structure</span><span class="sxs-lookup"><span data-stu-id="08237-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="08237-103">Représente un bloc de code unique en mémoire.</span><span class="sxs-lookup"><span data-stu-id="08237-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08237-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="08237-105">Membres</span><span class="sxs-lookup"><span data-stu-id="08237-105">Members</span></span>  
  
|<span data-ttu-id="08237-106">Membre</span><span class="sxs-lookup"><span data-stu-id="08237-106">Member</span></span>|<span data-ttu-id="08237-107">Description</span><span class="sxs-lookup"><span data-stu-id="08237-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="08237-108">Valeur `CORDB_ADDRESS` qui spécifie l’adresse de début du bloc.</span><span class="sxs-lookup"><span data-stu-id="08237-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="08237-109">Taille, en octets, du segment.</span><span class="sxs-lookup"><span data-stu-id="08237-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08237-110">Notes</span><span class="sxs-lookup"><span data-stu-id="08237-110">Remarks</span></span>  
 <span data-ttu-id="08237-111">Le segment de code unique est une région de code natif qui fait partie d’un objet de code tel qu’une fonction.</span><span class="sxs-lookup"><span data-stu-id="08237-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08237-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="08237-112">Requirements</span></span>  
 <span data-ttu-id="08237-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08237-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08237-114">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="08237-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="08237-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08237-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08237-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08237-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08237-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08237-117">See also</span></span>

- [<span data-ttu-id="08237-118">GetCodeChunks, méthode</span><span class="sxs-lookup"><span data-stu-id="08237-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="08237-119">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="08237-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="08237-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="08237-120">Debugging</span></span>](index.md)
