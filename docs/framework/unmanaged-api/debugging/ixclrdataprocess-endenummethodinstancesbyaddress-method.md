---
title: IXCLRDataProcess::EndEnumMethodInstancesByAddress (méthode)
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
ms.openlocfilehash: 378095aa2b363f4003a5372b4158df27412655e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757851"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="82f8b-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="82f8b-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="82f8b-103">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération de l’instance.</span><span class="sxs-lookup"><span data-stu-id="82f8b-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="82f8b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82f8b-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="82f8b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82f8b-105">Parameters</span></span>

`handle`\
<span data-ttu-id="82f8b-106">[out] Un handle pour énumérer les instances de la méthode.</span><span class="sxs-lookup"><span data-stu-id="82f8b-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="82f8b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="82f8b-107">Remarks</span></span>

<span data-ttu-id="82f8b-108">La méthode fournie fait partie de la `IXCLRDataProcess` interface et correspond à l’emplacement de la table de la méthode virtuelle de 29.</span><span class="sxs-lookup"><span data-stu-id="82f8b-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="82f8b-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="82f8b-109">Requirements</span></span>

<span data-ttu-id="82f8b-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82f8b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="82f8b-111">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="82f8b-111">**Header:** None</span></span>  
<span data-ttu-id="82f8b-112">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="82f8b-112">**Library:** None</span></span>  
<span data-ttu-id="82f8b-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="82f8b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="82f8b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82f8b-114">See also</span></span>

- [<span data-ttu-id="82f8b-115">Énumération de CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="82f8b-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="82f8b-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="82f8b-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="82f8b-117">Interface de IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="82f8b-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
