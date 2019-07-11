---
title: IXCLRDataMethodDefinition::StartEnumInstances (méthode)
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
ms.openlocfilehash: 89473f2a6a3da73ee5d172a3700bdb4d624278ff
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756296"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="19d88-102">IXCLRDataMethodDefinition::StartEnumInstances (méthode)</span><span class="sxs-lookup"><span data-stu-id="19d88-102">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="19d88-103">Fournit un handle pour l’énumération des instances de méthode pour une donnée `IXCLRDataAppDomain`.</span><span class="sxs-lookup"><span data-stu-id="19d88-103">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="19d88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19d88-104">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="19d88-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="19d88-105">Parameters</span></span>

`appDomain`\
<span data-ttu-id="19d88-106">[in] Un AppDomain pour l’énumération.</span><span class="sxs-lookup"><span data-stu-id="19d88-106">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="19d88-107">[out] Un handle pour énumérer les instances.</span><span class="sxs-lookup"><span data-stu-id="19d88-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="19d88-108">Notes</span><span class="sxs-lookup"><span data-stu-id="19d88-108">Remarks</span></span>

<span data-ttu-id="19d88-109">La méthode fournie fait partie de la `IXCLRDataMethodDefinition` interface et correspond à la troisième emplacement de la table de la méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="19d88-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the third slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="19d88-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="19d88-110">Requirements</span></span>

<span data-ttu-id="19d88-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19d88-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="19d88-112">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="19d88-112">**Header:** None</span></span>  
<span data-ttu-id="19d88-113">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="19d88-113">**Library:** None</span></span>  
<span data-ttu-id="19d88-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="19d88-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="19d88-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19d88-115">See also</span></span>

- [<span data-ttu-id="19d88-116">Énumération de CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="19d88-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="19d88-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="19d88-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="19d88-118">Interface de IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="19d88-118">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
