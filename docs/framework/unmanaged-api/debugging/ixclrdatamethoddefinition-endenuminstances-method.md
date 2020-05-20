---
title: 'IXCLRDataMethodDefinition :: EndEnumInstances, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7271c9594a679af205c404f59ff6731821aa0acf
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420992"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="1431b-102">IXCLRDataMethodDefinition :: EndEnumInstances, méthode</span><span class="sxs-lookup"><span data-stu-id="1431b-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="1431b-103">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération d’instance.</span><span class="sxs-lookup"><span data-stu-id="1431b-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1431b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1431b-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="1431b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1431b-105">Parameters</span></span>

`handle`\
<span data-ttu-id="1431b-106">à Handle pour énumérer les instances.</span><span class="sxs-lookup"><span data-stu-id="1431b-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="1431b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="1431b-107">Remarks</span></span>

<span data-ttu-id="1431b-108">La méthode fournie fait partie de l' `IXCLRDataMethodDefinition` interface et correspond au septième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="1431b-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1431b-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="1431b-109">Requirements</span></span>

<span data-ttu-id="1431b-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1431b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1431b-111">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="1431b-111">**Header:** None</span></span>  
<span data-ttu-id="1431b-112">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="1431b-112">**Library:** None</span></span>  
<span data-ttu-id="1431b-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1431b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1431b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1431b-114">See also</span></span>

- [<span data-ttu-id="1431b-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="1431b-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="1431b-116">IXCLRDataMethodDefinition, interface</span><span class="sxs-lookup"><span data-stu-id="1431b-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
