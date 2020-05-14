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
ms.openlocfilehash: febe6766c7a35228820421eee975c777988efd1f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396488"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="49070-102">IXCLRDataMethodDefinition :: EndEnumInstances, méthode</span><span class="sxs-lookup"><span data-stu-id="49070-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="49070-103">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération d’instance.</span><span class="sxs-lookup"><span data-stu-id="49070-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="49070-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49070-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="49070-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49070-105">Parameters</span></span>

`handle`\
<span data-ttu-id="49070-106">à Handle pour énumérer les instances.</span><span class="sxs-lookup"><span data-stu-id="49070-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="49070-107">Notes</span><span class="sxs-lookup"><span data-stu-id="49070-107">Remarks</span></span>

<span data-ttu-id="49070-108">La méthode fournie fait partie de l' `IXCLRDataMethodDefinition` interface et correspond au septième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="49070-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="49070-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="49070-109">Requirements</span></span>

<span data-ttu-id="49070-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49070-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="49070-111">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="49070-111">**Header:** None</span></span>  
<span data-ttu-id="49070-112">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="49070-112">**Library:** None</span></span>  
<span data-ttu-id="49070-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="49070-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="49070-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49070-114">See also</span></span>

- [<span data-ttu-id="49070-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="49070-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="49070-116">IXCLRDataMethodDefinition, interface</span><span class="sxs-lookup"><span data-stu-id="49070-116">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
