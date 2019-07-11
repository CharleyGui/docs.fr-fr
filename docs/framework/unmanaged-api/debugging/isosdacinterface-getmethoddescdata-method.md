---
title: ISOSDacInterface::GetMethodDescData (méthode)
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ea54fdd83b9470db4a08daceaa695e450f5ca1af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764824"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="830c0-102">ISOSDacInterface::GetMethodDescData (méthode)</span><span class="sxs-lookup"><span data-stu-id="830c0-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="830c0-103">Obtient les données pour le pointeur MethodDesc donné.</span><span class="sxs-lookup"><span data-stu-id="830c0-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="830c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="830c0-104">Syntax</span></span>

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a><span data-ttu-id="830c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="830c0-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="830c0-106">[in] L’adresse de la MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="830c0-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="830c0-107">[in] L’adresse IP de la méthode.</span><span class="sxs-lookup"><span data-stu-id="830c0-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="830c0-108">[out] Les données associées à la MethodDesc tel que retourné par l’API internes.</span><span class="sxs-lookup"><span data-stu-id="830c0-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="830c0-109">[out] Le nombre de versions de rejit rétablie.</span><span class="sxs-lookup"><span data-stu-id="830c0-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="830c0-110">[out] Les données associées aux versions rejit rétabli tel que retourné par l’API internes.</span><span class="sxs-lookup"><span data-stu-id="830c0-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="830c0-111">[out] Le nombre d’octets requis pour stocker les données associées avec les versions ReJit rétablies.</span><span class="sxs-lookup"><span data-stu-id="830c0-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="830c0-112">Notes</span><span class="sxs-lookup"><span data-stu-id="830c0-112">Remarks</span></span>

<span data-ttu-id="830c0-113">La méthode fournie fait partie de la `ISOSDacInterface` interface et correspond à l’emplacement de la table de la méthode virtuelle de 20.</span><span class="sxs-lookup"><span data-stu-id="830c0-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="830c0-114">Pour pouvoir les utiliser, [ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md) doit être définie comme un entier non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="830c0-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="830c0-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="830c0-115">Requirements</span></span>

<span data-ttu-id="830c0-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="830c0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="830c0-117">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="830c0-117">**Header:** None</span></span>  
<span data-ttu-id="830c0-118">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="830c0-118">**Library:** None</span></span>  
<span data-ttu-id="830c0-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="830c0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="830c0-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="830c0-120">See also</span></span>

- [<span data-ttu-id="830c0-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="830c0-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="830c0-122">Interface de ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="830c0-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
