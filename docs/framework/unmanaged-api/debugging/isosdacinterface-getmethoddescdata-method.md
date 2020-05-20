---
title: 'ISOSDacInterface :: GetMethodDescData, méthode'
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
ms.openlocfilehash: 105149d0abf312c33a8498e7428e3a8b23d6ae7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421018"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a><span data-ttu-id="d0d55-102">ISOSDacInterface :: GetMethodDescData, méthode</span><span class="sxs-lookup"><span data-stu-id="d0d55-102">ISOSDacInterface::GetMethodDescData Method</span></span>

<span data-ttu-id="d0d55-103">Obtient les données pour le pointeur MethodDesc donné.</span><span class="sxs-lookup"><span data-stu-id="d0d55-103">Gets the data for the given MethodDesc pointer.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="d0d55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0d55-104">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="d0d55-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0d55-105">Parameters</span></span>

`methodDesc`\
<span data-ttu-id="d0d55-106">dans Adresse du MethodDesc.</span><span class="sxs-lookup"><span data-stu-id="d0d55-106">[in] The address of the MethodDesc.</span></span>

`ip`\
<span data-ttu-id="d0d55-107">dans Adresse IP de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d0d55-107">[in] The IP address of the method.</span></span>

`data`\
<span data-ttu-id="d0d55-108">à Données associées à MethodDesc, telles qu’elles sont retournées par les API internes.</span><span class="sxs-lookup"><span data-stu-id="d0d55-108">[out] The data associated with the MethodDesc as returned from the internal APIs.</span></span>

`cRevertedRejitVersions`\
<span data-ttu-id="d0d55-109">à Nombre de versions de ReJIT restaurées.</span><span class="sxs-lookup"><span data-stu-id="d0d55-109">[out] The number of reverted rejit versions.</span></span>

`rgRevertedRejitData`\
<span data-ttu-id="d0d55-110">à Les données associées aux versions ReJIT restaurées sont retournées par les API internes.</span><span class="sxs-lookup"><span data-stu-id="d0d55-110">[out] The data associated with the reverted rejit versions as returned from the internal APIs.</span></span>

`pcNeededRevertedRejitData`\
<span data-ttu-id="d0d55-111">à Nombre d’octets requis pour stocker les données associées aux versions ReJit restaurées.</span><span class="sxs-lookup"><span data-stu-id="d0d55-111">[out] The number of bytes required to store the data associated with the reverted ReJit versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0d55-112">Notes</span><span class="sxs-lookup"><span data-stu-id="d0d55-112">Remarks</span></span>

<span data-ttu-id="d0d55-113">La méthode fournie fait partie de l' `ISOSDacInterface` interface et correspond à l’emplacement du 21e de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="d0d55-113">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 21st slot of the virtual method table.</span></span> <span data-ttu-id="d0d55-114">Pour pouvoir les utiliser, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) doit être défini en tant qu’entier non signé 64 bits.</span><span class="sxs-lookup"><span data-stu-id="d0d55-114">To be able to use them, [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) must be defined as a 64-bit unsigned integer.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0d55-115">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d0d55-115">Requirements</span></span>

<span data-ttu-id="d0d55-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0d55-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="d0d55-117">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="d0d55-117">**Header:** None</span></span>  
<span data-ttu-id="d0d55-118">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="d0d55-118">**Library:** None</span></span>  
<span data-ttu-id="d0d55-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d0d55-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="d0d55-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0d55-120">See also</span></span>

- [<span data-ttu-id="d0d55-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="d0d55-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="d0d55-122">ISOSDacInterface, interface</span><span class="sxs-lookup"><span data-stu-id="d0d55-122">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
