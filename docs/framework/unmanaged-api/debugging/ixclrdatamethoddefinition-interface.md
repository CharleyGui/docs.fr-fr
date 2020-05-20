---
title: IXCLRDataMethodDefinition, interface
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ebb689eee4a89a70e81d8f9d958e7826c3b3421b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420953"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="58ffa-102">IXCLRDataMethodDefinition, interface</span><span class="sxs-lookup"><span data-stu-id="58ffa-102">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="58ffa-103">Fournit des méthodes pour interroger des informations sur une définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="58ffa-103">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="58ffa-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="58ffa-104">Methods</span></span>

<span data-ttu-id="58ffa-105">Voici quelques-unes des méthodes disponibles dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="58ffa-105">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="58ffa-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="58ffa-106">Method</span></span>                                                                                                                          | <span data-ttu-id="58ffa-107">Description</span><span class="sxs-lookup"><span data-stu-id="58ffa-107">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="58ffa-108">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="58ffa-108">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="58ffa-109">Fournit un handle pour l’énumération des instances de méthode pour un donné `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="58ffa-109">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="58ffa-110">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="58ffa-110">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="58ffa-111">Énumère les instances de cette définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="58ffa-111">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="58ffa-112">EndEnumInstances</span><span class="sxs-lookup"><span data-stu-id="58ffa-112">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="58ffa-113">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération d’instance.</span><span class="sxs-lookup"><span data-stu-id="58ffa-113">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="58ffa-114">Notes</span><span class="sxs-lookup"><span data-stu-id="58ffa-114">Remarks</span></span>

<span data-ttu-id="58ffa-115">Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="58ffa-115">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="58ffa-116">Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec `AAF60008-FB2C-420b-8FB1-42D244A54A97` un GUID qui peut être obtenu par le biais des mécanismes com habituels.</span><span class="sxs-lookup"><span data-stu-id="58ffa-116">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="58ffa-117">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="58ffa-117">Requirements</span></span>

<span data-ttu-id="58ffa-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58ffa-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="58ffa-119">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="58ffa-119">**Header:** None</span></span>  
<span data-ttu-id="58ffa-120">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="58ffa-120">**Library:** None</span></span>  
<span data-ttu-id="58ffa-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="58ffa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="58ffa-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58ffa-122">See also</span></span>

- [<span data-ttu-id="58ffa-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="58ffa-123">Debugging</span></span>](index.md)
- [<span data-ttu-id="58ffa-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="58ffa-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
