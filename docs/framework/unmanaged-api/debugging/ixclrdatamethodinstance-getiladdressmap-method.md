---
title: 'IXCLRDataMethodInstance :: GetILAddressMap, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7c4dcf59ce159434d5012120043f5bb548d49731
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396816"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="7985f-102">IXCLRDataMethodInstance :: GetILAddressMap, méthode</span><span class="sxs-lookup"><span data-stu-id="7985f-102">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="7985f-103">Obtient le IL pour traiter les informations de mappage.</span><span class="sxs-lookup"><span data-stu-id="7985f-103">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="7985f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7985f-104">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="7985f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7985f-105">Parameters</span></span>

`mapLen`\
<span data-ttu-id="7985f-106">dans Longueur du tableau Maps fourni.</span><span class="sxs-lookup"><span data-stu-id="7985f-106">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="7985f-107">à Nombre d’entrées de mappage dont la méthode a besoin.</span><span class="sxs-lookup"><span data-stu-id="7985f-107">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="7985f-108">[out, size_is (érable)] Tableau pour le stockage des entrées de mappage.</span><span class="sxs-lookup"><span data-stu-id="7985f-108">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="7985f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7985f-109">Remarks</span></span>

<span data-ttu-id="7985f-110">La méthode fournie fait partie de l' `IXCLRDataMethodInstance` interface et correspond au quinzième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="7985f-110">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="7985f-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7985f-111">Requirements</span></span>

<span data-ttu-id="7985f-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7985f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="7985f-113">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="7985f-113">**Header:** None</span></span>  
<span data-ttu-id="7985f-114">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="7985f-114">**Library:** None</span></span>  
<span data-ttu-id="7985f-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7985f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="7985f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7985f-116">See also</span></span>

- [<span data-ttu-id="7985f-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="7985f-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="7985f-118">IXCLRDataMethodInstance, interface</span><span class="sxs-lookup"><span data-stu-id="7985f-118">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
