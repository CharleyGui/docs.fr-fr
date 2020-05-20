---
title: 'IXCLRDataProcess :: StartEnumMethodInstancesByAddress, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 52d533f1c86b34b7b9febade8590e7ab58d8221e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420732"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="d3607-102">IXCLRDataProcess :: StartEnumMethodInstancesByAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="d3607-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="d3607-103">Fournit un handle pour énumérer les instances de méthode de `AppDomain` à partir d’une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="d3607-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d3607-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3607-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="d3607-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d3607-105">Parameters</span></span>

`address`\
<span data-ttu-id="d3607-106">dans Adresse de la première instance de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d3607-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="d3607-107">dans AppDomain des instances de méthode.</span><span class="sxs-lookup"><span data-stu-id="d3607-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="d3607-108">à Handle pour énumérer les instances de méthode.</span><span class="sxs-lookup"><span data-stu-id="d3607-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="d3607-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d3607-109">Remarks</span></span>

<span data-ttu-id="d3607-110">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 28ème emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="d3607-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d3607-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d3607-111">Requirements</span></span>

<span data-ttu-id="d3607-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3607-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d3607-113">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="d3607-113">**Header:** None</span></span>  
<span data-ttu-id="d3607-114">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="d3607-114">**Library:** None</span></span>  
<span data-ttu-id="d3607-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d3607-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d3607-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3607-116">See also</span></span>

- [<span data-ttu-id="d3607-117">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="d3607-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="d3607-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="d3607-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="d3607-119">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="d3607-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
