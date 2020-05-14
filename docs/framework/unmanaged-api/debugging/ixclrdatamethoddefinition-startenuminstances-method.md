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
ms.openlocfilehash: 84e0ad392c5fee8377115427482d80543454fff3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397205"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="87828-102">IXCLRDataMethodDefinition :: StartEnumInstances, méthode</span><span class="sxs-lookup"><span data-stu-id="87828-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="87828-103">Fournit un handle pour l’énumération des instances de méthode pour un donné `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="87828-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="87828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87828-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="87828-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="87828-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="87828-106">dans AppDomain pour l’énumération.</span><span class="sxs-lookup"><span data-stu-id="87828-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="87828-107">à Handle pour énumérer les instances.</span><span class="sxs-lookup"><span data-stu-id="87828-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="87828-108">Notes</span><span class="sxs-lookup"><span data-stu-id="87828-108">Remarks</span></span>

<span data-ttu-id="87828-109">La méthode fournie fait partie de l' `IXCLRDataMethodDefinition` interface et correspond au cinquième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="87828-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="87828-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="87828-110">Requirements</span></span>

<span data-ttu-id="87828-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87828-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="87828-112">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="87828-112">**Header:** None</span></span>  
<span data-ttu-id="87828-113">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="87828-113">**Library:** None</span></span>  
<span data-ttu-id="87828-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="87828-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="87828-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87828-115">See also</span></span>

- [<span data-ttu-id="87828-116">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="87828-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="87828-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="87828-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="87828-118">IXCLRDataMethodDefinition, interface</span><span class="sxs-lookup"><span data-stu-id="87828-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
