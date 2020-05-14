---
title: 'IXCLRDataProcess :: EnumMethodInstanceByAddress, méthode'
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
ms.openlocfilehash: f3800a5980304394dd648111fe23a3bb0890c575
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395109"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="d120d-102">IXCLRDataProcess :: EnumMethodInstanceByAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="d120d-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="d120d-103">Énumère les instances de méthode de ce processus à partir d’un décalage d’adresse.</span><span class="sxs-lookup"><span data-stu-id="d120d-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d120d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d120d-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="d120d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d120d-105">Parameters</span></span>

`handle`\
<span data-ttu-id="d120d-106">dans Handle pour énumérer les instances de méthode.</span><span class="sxs-lookup"><span data-stu-id="d120d-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="d120d-107">à Instance de la méthode énumérée.</span><span class="sxs-lookup"><span data-stu-id="d120d-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="d120d-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d120d-108">Remarks</span></span>

<span data-ttu-id="d120d-109">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 29ème emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="d120d-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d120d-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d120d-110">Requirements</span></span>

<span data-ttu-id="d120d-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d120d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>
<span data-ttu-id="d120d-112">**En-tête :** **Bibliothèque None :** aucune **.NET Framework versions :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d120d-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d120d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d120d-113">See also</span></span>

- [<span data-ttu-id="d120d-114">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="d120d-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="d120d-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="d120d-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="d120d-116">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="d120d-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
