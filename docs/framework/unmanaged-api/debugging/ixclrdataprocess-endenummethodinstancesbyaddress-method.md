---
title: 'IXCLRDataProcess :: EndEnumMethodInstancesByAddress, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 04ce8f44b0c9f532951666de7bfb9de475c14746
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395256"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="623b3-102">IXCLRDataProcess :: EndEnumMethodInstancesByAddress, méthode</span><span class="sxs-lookup"><span data-stu-id="623b3-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="623b3-103">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération d’instance.</span><span class="sxs-lookup"><span data-stu-id="623b3-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="623b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="623b3-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="623b3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="623b3-105">Parameters</span></span>

`handle`\
<span data-ttu-id="623b3-106">à Handle pour énumérer les instances de méthode.</span><span class="sxs-lookup"><span data-stu-id="623b3-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="623b3-107">Notes</span><span class="sxs-lookup"><span data-stu-id="623b3-107">Remarks</span></span>

<span data-ttu-id="623b3-108">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 30 emplacements de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="623b3-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="623b3-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="623b3-109">Requirements</span></span>

<span data-ttu-id="623b3-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="623b3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="623b3-111">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="623b3-111">**Header:** None</span></span>  
<span data-ttu-id="623b3-112">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="623b3-112">**Library:** None</span></span>  
<span data-ttu-id="623b3-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="623b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="623b3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="623b3-114">See also</span></span>

- [<span data-ttu-id="623b3-115">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="623b3-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="623b3-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="623b3-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="623b3-117">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="623b3-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
