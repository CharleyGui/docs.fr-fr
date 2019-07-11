---
title: IXCLRDataProcess::EnumMethodInstanceByAddress (méthode)
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 89b89a0cb056a0515bf0859069455a73f62aae4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769619"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="fb741-102">IXCLRDataProcess::EnumMethodInstanceByAddress (méthode)</span><span class="sxs-lookup"><span data-stu-id="fb741-102">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="fb741-103">Énumère les instances de la méthode de ce processus, en commençant à un offset d’adresse.</span><span class="sxs-lookup"><span data-stu-id="fb741-103">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fb741-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fb741-104">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="fb741-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fb741-105">Parameters</span></span>

`handle`\
<span data-ttu-id="fb741-106">[in] Un handle pour énumérer les instances de la méthode.</span><span class="sxs-lookup"><span data-stu-id="fb741-106">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="fb741-107">[out] L’instance de la méthode énumérée.</span><span class="sxs-lookup"><span data-stu-id="fb741-107">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="fb741-108">Notes</span><span class="sxs-lookup"><span data-stu-id="fb741-108">Remarks</span></span>

<span data-ttu-id="fb741-109">La méthode fournie fait partie de la `IXCLRDataProcess` interface et correspond à l’emplacement de la table de la méthode virtuelle de 28.</span><span class="sxs-lookup"><span data-stu-id="fb741-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="fb741-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fb741-110">Requirements</span></span>

<span data-ttu-id="fb741-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb741-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>   
<span data-ttu-id="fb741-112">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="fb741-112">**Header:** None</span></span>   
<span data-ttu-id="fb741-113">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="fb741-113">**Library:** None</span></span>   
<span data-ttu-id="fb741-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fb741-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>   
 
## <a name="see-also"></a><span data-ttu-id="fb741-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb741-115">See also</span></span>

- [<span data-ttu-id="fb741-116">Énumération de CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="fb741-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="fb741-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="fb741-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="fb741-118">Interface de IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="fb741-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
