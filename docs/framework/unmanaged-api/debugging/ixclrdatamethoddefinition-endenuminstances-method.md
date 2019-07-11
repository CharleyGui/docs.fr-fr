---
title: IXCLRDataMethodDefinition::EndEnumInstances (méthode)
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
ms.openlocfilehash: 3d9e3ca31eddff9d08607c4d6d37ca76139bf5d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756308"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="f8aad-102">IXCLRDataMethodDefinition::EndEnumInstances (méthode)</span><span class="sxs-lookup"><span data-stu-id="f8aad-102">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="f8aad-103">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération de l’instance.</span><span class="sxs-lookup"><span data-stu-id="f8aad-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f8aad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8aad-104">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="f8aad-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8aad-105">Parameters</span></span>

`handle`\
<span data-ttu-id="f8aad-106">[out] Un handle pour énumérer les instances.</span><span class="sxs-lookup"><span data-stu-id="f8aad-106">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8aad-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f8aad-107">Remarks</span></span>

<span data-ttu-id="f8aad-108">La méthode fournie fait partie de la `IXCLRDataMethodDefinition` interface et correspond à l’emplacement de cinquième de la table de la méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="f8aad-108">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the fifth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8aad-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8aad-109">Requirements</span></span>

<span data-ttu-id="f8aad-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8aad-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f8aad-111">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="f8aad-111">**Header:** None</span></span>  
<span data-ttu-id="f8aad-112">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="f8aad-112">**Library:** None</span></span>  
<span data-ttu-id="f8aad-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f8aad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f8aad-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8aad-114">See also</span></span>

- [<span data-ttu-id="f8aad-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="f8aad-115">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="f8aad-116">Interface de IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="f8aad-116">IXCLRDataMethodDefinition Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
