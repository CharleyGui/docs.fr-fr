---
title: 'IXCLRDataMethodDefinition :: StartEnumInstances, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b0c37c666f23f04239ed827246b87c43ee8d5ad9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420927"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="8985f-102">IXCLRDataMethodDefinition :: StartEnumInstances, méthode</span><span class="sxs-lookup"><span data-stu-id="8985f-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="8985f-103">Fournit un handle pour l’énumération des instances de méthode pour un donné `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="8985f-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="8985f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8985f-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="8985f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8985f-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="8985f-106">dans AppDomain pour l’énumération.</span><span class="sxs-lookup"><span data-stu-id="8985f-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="8985f-107">à Handle pour énumérer les instances.</span><span class="sxs-lookup"><span data-stu-id="8985f-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="8985f-108">Notes</span><span class="sxs-lookup"><span data-stu-id="8985f-108">Remarks</span></span>

<span data-ttu-id="8985f-109">La méthode fournie fait partie de l' `IXCLRDataMethodDefinition` interface et correspond au cinquième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="8985f-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="8985f-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="8985f-110">Requirements</span></span>

<span data-ttu-id="8985f-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8985f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8985f-112">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="8985f-112">**Header:** None</span></span>  
<span data-ttu-id="8985f-113">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="8985f-113">**Library:** None</span></span>  
<span data-ttu-id="8985f-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8985f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8985f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8985f-115">See also</span></span>

- [<span data-ttu-id="8985f-116">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="8985f-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="8985f-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="8985f-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="8985f-118">IXCLRDataMethodDefinition, interface</span><span class="sxs-lookup"><span data-stu-id="8985f-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
