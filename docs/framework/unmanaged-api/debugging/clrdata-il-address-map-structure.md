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
ms.openlocfilehash: 3f6928832d822422177ebd7def142422953468a0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274292"
---
# <a name="clrdata_il_address_map-structure"></a><span data-ttu-id="6e64f-102">CLRDATA_IL_ADDRESS_MAP, structure</span><span class="sxs-lookup"><span data-stu-id="6e64f-102">CLRDATA_IL_ADDRESS_MAP Structure</span></span>

<span data-ttu-id="6e64f-103">Définit un mappage IL à adresse.</span><span class="sxs-lookup"><span data-stu-id="6e64f-103">Defines an IL to address mapping.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="6e64f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e64f-104">Syntax</span></span>

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a><span data-ttu-id="6e64f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="6e64f-105">Members</span></span>

| <span data-ttu-id="6e64f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="6e64f-106">Member</span></span>         | <span data-ttu-id="6e64f-107">Description</span><span class="sxs-lookup"><span data-stu-id="6e64f-107">Description</span></span>                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | <span data-ttu-id="6e64f-108">Offset IL pour la plage d’adresses contenue</span><span class="sxs-lookup"><span data-stu-id="6e64f-108">IL offset for the contained address range</span></span>              |
| `startAddress` | <span data-ttu-id="6e64f-109">Adresse de début de la plage.</span><span class="sxs-lookup"><span data-stu-id="6e64f-109">The start address of the range.</span></span>                        |
| `endAddress`   | <span data-ttu-id="6e64f-110">Adresse de fin de la plage.</span><span class="sxs-lookup"><span data-stu-id="6e64f-110">The end address of the range.</span></span>                          |
| `type`         | <span data-ttu-id="6e64f-111">Type des données.</span><span class="sxs-lookup"><span data-stu-id="6e64f-111">The type of the data.</span></span> <span data-ttu-id="6e64f-112">Cette valeur n’est pas utilisée actuellement</span><span class="sxs-lookup"><span data-stu-id="6e64f-112">This value is currently not used</span></span> |

## <a name="remarks"></a><span data-ttu-id="6e64f-113">Notes</span><span class="sxs-lookup"><span data-stu-id="6e64f-113">Remarks</span></span>

<span data-ttu-id="6e64f-114">Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="6e64f-114">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="6e64f-115">Pour l’utiliser, définissez la structure comme indiqué ci-dessus `CLRDATA_ADDRESS` , où est un entier non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="6e64f-115">To use it, define the structure as specified above, where `CLRDATA_ADDRESS` is a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="6e64f-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6e64f-116">Requirements</span></span>

<span data-ttu-id="6e64f-117">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e64f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6e64f-118">**En-tête :** Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e64f-118">**Header:** None</span></span>  
<span data-ttu-id="6e64f-119">**Bibliothèque** Aucun.</span><span class="sxs-lookup"><span data-stu-id="6e64f-119">**Library:** None</span></span>   
<span data-ttu-id="6e64f-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6e64f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6e64f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e64f-121">See also</span></span>

- [<span data-ttu-id="6e64f-122">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="6e64f-122">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="6e64f-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="6e64f-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="6e64f-124">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="6e64f-124">Debugging Structures</span></span>](debugging-structures.md)
