---
title: CLRDATA_IL_ADDRESS_MAP, structure
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179377"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="a6203-102">CLRDATA_IL_ADDRESS_MAP, structure</span><span class="sxs-lookup"><span data-stu-id="a6203-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="a6203-103">Définit un IL pour aborder la cartographie.</span><span class="sxs-lookup"><span data-stu-id="a6203-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a6203-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6203-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="a6203-105">Membres</span><span class="sxs-lookup"><span data-stu-id="a6203-105">Members</span></span>

| <span data-ttu-id="a6203-106">Membre</span><span class="sxs-lookup"><span data-stu-id="a6203-106">Member</span></span>         | <span data-ttu-id="a6203-107">Description</span><span class="sxs-lookup"><span data-stu-id="a6203-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="a6203-108">DÉCALAGE IL pour la plage d’adresse contenue</span><span class="sxs-lookup"><span data-stu-id="a6203-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="a6203-109">L’adresse de départ de la plage.</span><span class="sxs-lookup"><span data-stu-id="a6203-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="a6203-110">L’adresse de fin de la plage.</span><span class="sxs-lookup"><span data-stu-id="a6203-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="a6203-111">Type des données.</span><span class="sxs-lookup"><span data-stu-id="a6203-111">The type of the data.</span></span> <span data-ttu-id="a6203-112">Cette valeur n’est actuellement pas utilisée</span><span class="sxs-lookup"><span data-stu-id="a6203-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="a6203-113">Notes </span><span class="sxs-lookup"><span data-stu-id="a6203-113">Remarks</span></span>

<span data-ttu-id="a6203-114">Cette structure vit à l’intérieur du temps d’exécution et n’est pas exposée à travers des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a6203-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="a6203-115">Pour l’utiliser, définissez la `CLRDATA_ADDRESS` structure comme indiqué ci-dessus, où est un integer non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a6203-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6203-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a6203-116">Requirements</span></span>

<span data-ttu-id="a6203-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6203-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a6203-118">**En-tête:** Aucun</span><span class="sxs-lookup"><span data-stu-id="a6203-118">**Header:** None</span></span>  
<span data-ttu-id="a6203-119">**Bibliothèque:** Aucune **version cadre .NET:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a6203-119">**Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a6203-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6203-120">See also</span></span>

- [<span data-ttu-id="a6203-121">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="a6203-121">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="a6203-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="a6203-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="a6203-123">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="a6203-123">Debugging Structures</span></span>](debugging-structures.md)
