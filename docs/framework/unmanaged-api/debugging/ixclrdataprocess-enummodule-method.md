---
title: 'IXCLRDataProcess :: EnumModule, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5caadcfe091393a8ff79106d57a50a532c349829
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420772"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="881a2-102">IXCLRDataProcess :: EnumModule, méthode</span><span class="sxs-lookup"><span data-stu-id="881a2-102">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="881a2-103">Énumère les modules de ce processus.</span><span class="sxs-lookup"><span data-stu-id="881a2-103">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="881a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="881a2-104">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="881a2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="881a2-105">Parameters</span></span>

`handle`\
<span data-ttu-id="881a2-106">[in, out] Handle pour énumérer les modules.</span><span class="sxs-lookup"><span data-stu-id="881a2-106">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="881a2-107">à Module énuméré.</span><span class="sxs-lookup"><span data-stu-id="881a2-107">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="881a2-108">Notes</span><span class="sxs-lookup"><span data-stu-id="881a2-108">Remarks</span></span>

<span data-ttu-id="881a2-109">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 25e emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="881a2-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="881a2-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="881a2-110">Requirements</span></span>

<span data-ttu-id="881a2-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="881a2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="881a2-112">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="881a2-112">**Header:** None</span></span>  
<span data-ttu-id="881a2-113">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="881a2-113">**Library:** None</span></span>  
<span data-ttu-id="881a2-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="881a2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="881a2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="881a2-115">See also</span></span>

- [<span data-ttu-id="881a2-116">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="881a2-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="881a2-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="881a2-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="881a2-118">IXCLRDataModule, interface</span><span class="sxs-lookup"><span data-stu-id="881a2-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="881a2-119">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="881a2-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
