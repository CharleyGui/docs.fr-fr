---
title: CLRDATA_ADDRESS_RANGE, structure
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8eb841b4c4f06a3932805ae6222bdd693def5ea0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274308"
---
# <a name="clrdata_address_range-structure"></a><span data-ttu-id="bfe19-102">CLRDATA_ADDRESS_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="bfe19-102">CLRDATA_ADDRESS_RANGE Structure</span></span>

<span data-ttu-id="bfe19-103">Définit une plage d’adresses.</span><span class="sxs-lookup"><span data-stu-id="bfe19-103">Defines an address range.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bfe19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfe19-104">Syntax</span></span>

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a><span data-ttu-id="bfe19-105">Membres</span><span class="sxs-lookup"><span data-stu-id="bfe19-105">Members</span></span>

| <span data-ttu-id="bfe19-106">Membre</span><span class="sxs-lookup"><span data-stu-id="bfe19-106">Member</span></span>         | <span data-ttu-id="bfe19-107">Description</span><span class="sxs-lookup"><span data-stu-id="bfe19-107">Description</span></span>                     |
| -------------- | ------------------------------- |
| `startAddress` | <span data-ttu-id="bfe19-108">Adresse de début de la plage.</span><span class="sxs-lookup"><span data-stu-id="bfe19-108">The start address of the range.</span></span> |
| `endAddress`   | <span data-ttu-id="bfe19-109">Adresse de fin de la plage.</span><span class="sxs-lookup"><span data-stu-id="bfe19-109">The end address of the range.</span></span>   |

## <a name="remarks"></a><span data-ttu-id="bfe19-110">Notes</span><span class="sxs-lookup"><span data-stu-id="bfe19-110">Remarks</span></span>

<span data-ttu-id="bfe19-111">Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="bfe19-111">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="bfe19-112">Pour l’utiliser, définissez la structure comme indiqué ci-dessus `CLRDATA_ADDRESS` , où est un entier non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="bfe19-112">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="bfe19-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bfe19-113">Requirements</span></span>

<span data-ttu-id="bfe19-114">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfe19-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bfe19-115">**En-tête :** Aucun.</span><span class="sxs-lookup"><span data-stu-id="bfe19-115">**Header:** None</span></span>  
<span data-ttu-id="bfe19-116">**Bibliothèque** Aucun.</span><span class="sxs-lookup"><span data-stu-id="bfe19-116">**Library:** None</span></span>  
<span data-ttu-id="bfe19-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bfe19-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="bfe19-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfe19-118">See also</span></span>

- [<span data-ttu-id="bfe19-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="bfe19-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="bfe19-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="bfe19-120">Debugging Structures</span></span>](debugging-structures.md)
