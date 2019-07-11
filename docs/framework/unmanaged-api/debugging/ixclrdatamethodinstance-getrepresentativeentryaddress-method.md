---
title: IXCLRDataMethodInstance::GetRepresentativeEntryAddress (méthode)
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 5c79e916a06e796fc87b57eb949cccda77b8a9bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744663"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="f8152-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="f8152-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="f8152-103">Obtient l’adresse de point d’entrée plus représentatif de la compilation native de tous les points d’entrée possibles pour une méthode.</span><span class="sxs-lookup"><span data-stu-id="f8152-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="f8152-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8152-104">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="f8152-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8152-105">Parameters</span></span>

`addr`\
<span data-ttu-id="f8152-106">[out] L’adresse du point d’entrée natif plus représentatif pour la méthode.</span><span class="sxs-lookup"><span data-stu-id="f8152-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8152-107">Notes</span><span class="sxs-lookup"><span data-stu-id="f8152-107">Remarks</span></span>

<span data-ttu-id="f8152-108">La méthode fournie fait partie de la [ `IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) et correspond à l’emplacement de la table de la méthode virtuelle de 19.</span><span class="sxs-lookup"><span data-stu-id="f8152-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 19th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8152-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8152-109">Requirements</span></span>

<span data-ttu-id="f8152-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8152-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="f8152-111">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="f8152-111">**Header:** None</span></span>  
<span data-ttu-id="f8152-112">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="f8152-112">**Library:** None</span></span>  
<span data-ttu-id="f8152-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f8152-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="f8152-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8152-114">See also</span></span>

- [<span data-ttu-id="f8152-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="f8152-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="f8152-116">Interface de IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="f8152-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
