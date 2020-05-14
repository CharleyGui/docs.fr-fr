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
ms.openlocfilehash: 72560de9777b2d826418e63b4a4fcccf1e4fa8b9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396481"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="a7f42-102">IXCLRDataMethodDefinition :: EnumInstance, méthode</span><span class="sxs-lookup"><span data-stu-id="a7f42-102">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="a7f42-103">Énumère les instances de cette définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="a7f42-103">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="a7f42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7f42-104">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="a7f42-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a7f42-105">Parameters</span></span>

`handle`\
<span data-ttu-id="a7f42-106">[in, out] Handle pour énumérer les instances.</span><span class="sxs-lookup"><span data-stu-id="a7f42-106">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="a7f42-107">à Instance énumérée.</span><span class="sxs-lookup"><span data-stu-id="a7f42-107">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="a7f42-108">Notes</span><span class="sxs-lookup"><span data-stu-id="a7f42-108">Remarks</span></span>

<span data-ttu-id="a7f42-109">La méthode fournie fait partie de l' `IXCLRDataMethodDefinition` interface et correspond au sixième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="a7f42-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 6th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="a7f42-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a7f42-110">Requirements</span></span>

<span data-ttu-id="a7f42-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7f42-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="a7f42-112">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="a7f42-112">**Header:** None</span></span>  
<span data-ttu-id="a7f42-113">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="a7f42-113">**Library:** None</span></span>  
<span data-ttu-id="a7f42-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a7f42-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a7f42-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7f42-115">See also</span></span>

- [<span data-ttu-id="a7f42-116">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="a7f42-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="a7f42-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="a7f42-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="a7f42-118">IXCLRDataMethodDefinition, interface</span><span class="sxs-lookup"><span data-stu-id="a7f42-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="a7f42-119">IXCLRDataMethodInstance, interface</span><span class="sxs-lookup"><span data-stu-id="a7f42-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
