---
title: 'IXCLRDataMethodDefinition :: EnumInstance, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790442"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="21694-102">IXCLRDataMethodDefinition :: EnumInstance, méthode</span><span class="sxs-lookup"><span data-stu-id="21694-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="21694-103">Énumère les instances de cette définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="21694-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="21694-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21694-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="21694-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="21694-105">Parameters</span></span>

`handle`\
<span data-ttu-id="21694-106">[in, out] Handle pour énumérer les instances.</span><span class="sxs-lookup"><span data-stu-id="21694-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="21694-107">à Instance énumérée.</span><span class="sxs-lookup"><span data-stu-id="21694-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="21694-108">Notes</span><span class="sxs-lookup"><span data-stu-id="21694-108">Remarks</span></span>

<span data-ttu-id="21694-109">La méthode fournie fait partie de l’interface `IXCLRDataMethodDefinition` et correspond au quatrième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="21694-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="21694-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="21694-110">Requirements</span></span>

<span data-ttu-id="21694-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21694-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="21694-112">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="21694-112">**Header:** None</span></span>  
<span data-ttu-id="21694-113">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="21694-113">**Library:** None</span></span>  
<span data-ttu-id="21694-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="21694-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="21694-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21694-115">See also</span></span>

- [<span data-ttu-id="21694-116">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="21694-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="21694-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="21694-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="21694-118">Interface IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="21694-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="21694-119">Interface IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="21694-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
