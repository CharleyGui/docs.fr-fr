---
title: Énumération CLRDataSourceType
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274093"
---
# <a name="clrdatasourcetype-enumeration"></a><span data-ttu-id="239f2-102">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="239f2-102">CLRDataSourceType Enumeration</span></span>

<span data-ttu-id="239f2-103">Fournit des valeurs utilisées par la structure CLRDATA_IL_ADDRESS_MAP.</span><span class="sxs-lookup"><span data-stu-id="239f2-103">Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="239f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="239f2-104">Syntax</span></span>

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a><span data-ttu-id="239f2-105">Membres</span><span class="sxs-lookup"><span data-stu-id="239f2-105">Members</span></span>

| <span data-ttu-id="239f2-106">Membre</span><span class="sxs-lookup"><span data-stu-id="239f2-106">Member</span></span>                        | <span data-ttu-id="239f2-107">Description</span><span class="sxs-lookup"><span data-stu-id="239f2-107">Description</span></span>                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | <span data-ttu-id="239f2-108">Pour indiquer que rien d’autre ne s’applique</span><span class="sxs-lookup"><span data-stu-id="239f2-108">To indicate that nothing else applies</span></span> |

## <a name="remarks"></a><span data-ttu-id="239f2-109">Notes</span><span class="sxs-lookup"><span data-stu-id="239f2-109">Remarks</span></span>

<span data-ttu-id="239f2-110">Cette énumération se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="239f2-110">This enumeration lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="239f2-111">Pour l’utiliser, définissez une énumération telle que définie ci-dessus dans votre code.</span><span class="sxs-lookup"><span data-stu-id="239f2-111">To use it, define an enumeration as defined above in your code.</span></span> <span data-ttu-id="239f2-112">Il s’agit également d' `CLRDATA_ENUM` un alias comme indiqué dans types de [données communs](../common-data-types-unmanaged-api-reference.md).</span><span class="sxs-lookup"><span data-stu-id="239f2-112">This is also aliased to `CLRDATA_ENUM` as mentioned in [Common Data Types](../common-data-types-unmanaged-api-reference.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="239f2-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="239f2-113">Requirements</span></span>

<span data-ttu-id="239f2-114">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="239f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="239f2-115">**En-tête :** Aucun.</span><span class="sxs-lookup"><span data-stu-id="239f2-115">**Header:** None</span></span>  
<span data-ttu-id="239f2-116">**Bibliothèque** Aucun.</span><span class="sxs-lookup"><span data-stu-id="239f2-116">**Library:** None</span></span>  
<span data-ttu-id="239f2-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="239f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="239f2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="239f2-118">See also</span></span>

- [<span data-ttu-id="239f2-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="239f2-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="239f2-120">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="239f2-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
