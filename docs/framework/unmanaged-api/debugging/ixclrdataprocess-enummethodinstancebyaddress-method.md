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
ms.openlocfilehash: 142099ae5cf9637cc28e8c82aabcd831cc8f0f52
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420797"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="5ae10-102">IXCLRDataProcess :: EnumMethodInstanceByAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="5ae10-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="5ae10-103">Énumère les instances de méthode de ce processus à partir d’un décalage d’adresse.</span><span class="sxs-lookup"><span data-stu-id="5ae10-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="5ae10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ae10-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="5ae10-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ae10-105">Parameters</span></span>

`handle`\
<span data-ttu-id="5ae10-106">dans Handle pour énumérer les instances de méthode.</span><span class="sxs-lookup"><span data-stu-id="5ae10-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="5ae10-107">à Instance de la méthode énumérée.</span><span class="sxs-lookup"><span data-stu-id="5ae10-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ae10-108">Notes</span><span class="sxs-lookup"><span data-stu-id="5ae10-108">Remarks</span></span>

<span data-ttu-id="5ae10-109">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 29ème emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="5ae10-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ae10-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="5ae10-110">Requirements</span></span>

<span data-ttu-id="5ae10-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ae10-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="5ae10-112">**En-tête :** **Bibliothèque None :** aucune **.NET Framework versions :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ae10-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5ae10-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ae10-113">See also</span></span>

- [<span data-ttu-id="5ae10-114">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="5ae10-114">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="5ae10-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="5ae10-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="5ae10-116">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="5ae10-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
