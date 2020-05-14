---
title: 'IXCLRDataProcess :: StartEnumMethodInstancesByAddress, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e28fa73300e147ac07a2d325fbf517480bb73797
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394945"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="b4ae2-102">IXCLRDataProcess :: StartEnumMethodInstancesByAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="b4ae2-102">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="b4ae2-103">Fournit un handle pour énumérer les instances de méthode de `AppDomain` à partir d’une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="b4ae2-103">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="b4ae2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4ae2-104">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="b4ae2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4ae2-105">Parameters</span></span>

`address`\
<span data-ttu-id="b4ae2-106">dans Adresse de la première instance de la méthode.</span><span class="sxs-lookup"><span data-stu-id="b4ae2-106">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="b4ae2-107">dans AppDomain des instances de méthode.</span><span class="sxs-lookup"><span data-stu-id="b4ae2-107">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="b4ae2-108">à Handle pour énumérer les instances de méthode.</span><span class="sxs-lookup"><span data-stu-id="b4ae2-108">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4ae2-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b4ae2-109">Remarks</span></span>

<span data-ttu-id="b4ae2-110">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 28ème emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="b4ae2-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="b4ae2-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b4ae2-111">Requirements</span></span>

<span data-ttu-id="b4ae2-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4ae2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="b4ae2-113">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="b4ae2-113">**Header:** None</span></span>  
<span data-ttu-id="b4ae2-114">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="b4ae2-114">**Library:** None</span></span>  
<span data-ttu-id="b4ae2-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b4ae2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b4ae2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4ae2-116">See also</span></span>

- [<span data-ttu-id="b4ae2-117">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="b4ae2-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="b4ae2-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="b4ae2-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="b4ae2-119">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="b4ae2-119">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
