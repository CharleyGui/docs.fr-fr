---
title: 'IXCLRDataMethodInstance :: GetRepresentativeEntryAddress, méthode'
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
ms.openlocfilehash: d9f9e16d243c0f3b45ac24776caea5bb9c32dcc1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395752"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="d0892-102">IXCLRDataMethodInstance :: GetRepresentativeEntryAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="d0892-102">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="d0892-103">Obtient l’adresse de point d’entrée la plus représentative pour la compilation native de tous les points d’entrée possibles pour une méthode.</span><span class="sxs-lookup"><span data-stu-id="d0892-103">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d0892-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0892-104">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="d0892-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0892-105">Parameters</span></span>

`addr`\
<span data-ttu-id="d0892-106">à Adresse du point d’entrée natif le plus représentatif de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d0892-106">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0892-107">Notes</span><span class="sxs-lookup"><span data-stu-id="d0892-107">Remarks</span></span>

<span data-ttu-id="d0892-108">La méthode fournie fait partie de l' [ `IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) et correspond au vingtième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="d0892-108">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0892-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d0892-109">Requirements</span></span>

<span data-ttu-id="d0892-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0892-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d0892-111">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="d0892-111">**Header:** None</span></span>  
<span data-ttu-id="d0892-112">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="d0892-112">**Library:** None</span></span>  
<span data-ttu-id="d0892-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d0892-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d0892-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0892-114">See also</span></span>

- [<span data-ttu-id="d0892-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="d0892-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="d0892-116">IXCLRDataMethodInstance, interface</span><span class="sxs-lookup"><span data-stu-id="d0892-116">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
