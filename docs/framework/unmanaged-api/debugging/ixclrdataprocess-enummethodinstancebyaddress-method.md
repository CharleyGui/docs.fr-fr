---
title: IXCLRDataProcess::EnumMethodInstanceByAddress Méthode
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: afc5fc377dd45d5e8d4d2d7b3385ca0524df69e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176654"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="f8c22-102">IXCLRDataProcess::EnumMethodInstanceByAddress Méthode</span><span class="sxs-lookup"><span data-stu-id="f8c22-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="f8c22-103">Énumère les instances de méthode de ce processus à partir d’une compensation d’adresse.</span><span class="sxs-lookup"><span data-stu-id="f8c22-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f8c22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8c22-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="f8c22-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8c22-105">Parameters</span></span>

`handle`\
<span data-ttu-id="f8c22-106">[dans] Une poignée pour énumérer les instances de méthode.</span><span class="sxs-lookup"><span data-stu-id="f8c22-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="f8c22-107">[out] L’instance de méthode énumérée.</span><span class="sxs-lookup"><span data-stu-id="f8c22-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8c22-108">Notes </span><span class="sxs-lookup"><span data-stu-id="f8c22-108">Remarks</span></span>

<span data-ttu-id="f8c22-109">La méthode fournie fait `IXCLRDataProcess` partie de l’interface et correspond à la 28ème fente de la table de méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="f8c22-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8c22-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f8c22-110">Requirements</span></span>

<span data-ttu-id="f8c22-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8c22-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="f8c22-112">**En-tête:** Aucune **bibliothèque:** Aucune **version cadre .NET:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f8c22-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f8c22-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8c22-113">See also</span></span>

- [<span data-ttu-id="f8c22-114">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="f8c22-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="f8c22-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="f8c22-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="f8c22-116">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="f8c22-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
