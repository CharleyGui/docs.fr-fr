---
title: IXCLRDataMethodInstance, interface
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c51825433bbc86c897c097475d5c15c855f6ec8b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790410"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="23a66-102">IXCLRDataMethodInstance, interface</span><span class="sxs-lookup"><span data-stu-id="23a66-102">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="23a66-103">Fournit des méthodes pour interroger les informations relatives à une instance de méthode.</span><span class="sxs-lookup"><span data-stu-id="23a66-103">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="23a66-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="23a66-104">Methods</span></span>

| <span data-ttu-id="23a66-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="23a66-105">Method</span></span>                                                                                                                  | <span data-ttu-id="23a66-106">Description</span><span class="sxs-lookup"><span data-stu-id="23a66-106">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="23a66-107">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="23a66-107">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="23a66-108">Obtient le IL pour traiter les informations de mappage.</span><span class="sxs-lookup"><span data-stu-id="23a66-108">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="23a66-109">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="23a66-109">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="23a66-110">Obtient l’adresse de point d’entrée la plus représentative pour la compilation native de tous les points d’entrée possibles pour une méthode.</span><span class="sxs-lookup"><span data-stu-id="23a66-110">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="23a66-111">Notes</span><span class="sxs-lookup"><span data-stu-id="23a66-111">Remarks</span></span>

<span data-ttu-id="23a66-112">Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="23a66-112">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="23a66-113">Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` qui peuvent être obtenus par le biais des mécanismes COM habituels.</span><span class="sxs-lookup"><span data-stu-id="23a66-113">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="23a66-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="23a66-114">Requirements</span></span>

<span data-ttu-id="23a66-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23a66-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="23a66-116">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="23a66-116">**Header:** None</span></span>  
<span data-ttu-id="23a66-117">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="23a66-117">**Library:** None</span></span>  
<span data-ttu-id="23a66-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="23a66-118">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="23a66-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23a66-119">See also</span></span>

- [<span data-ttu-id="23a66-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="23a66-120">Debugging</span></span>](index.md)
- [<span data-ttu-id="23a66-121">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="23a66-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
