---
title: IXCLRDataProcess::StartEnumModules (méthode)
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 79c4e0ed99a068d7d806d5c25580dc477aac6475
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752631"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="e5ce8-102">IXCLRDataProcess::StartEnumModules (méthode)</span><span class="sxs-lookup"><span data-stu-id="e5ce8-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="e5ce8-103">Fournit un handle pour énumérer les modules d’un processus.</span><span class="sxs-lookup"><span data-stu-id="e5ce8-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e5ce8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5ce8-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="e5ce8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5ce8-105">Parameters</span></span>

`handle`\
<span data-ttu-id="e5ce8-106">[out] Un handle pour énumérer les modules.</span><span class="sxs-lookup"><span data-stu-id="e5ce8-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5ce8-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e5ce8-107">Remarks</span></span>

<span data-ttu-id="e5ce8-108">La méthode fournie fait partie de la `IXCLRDataProcess` interface et correspond à l’emplacement de la table de la méthode virtuelle de 24.</span><span class="sxs-lookup"><span data-stu-id="e5ce8-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5ce8-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e5ce8-109">Requirements</span></span>

<span data-ttu-id="e5ce8-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5ce8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e5ce8-111">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="e5ce8-111">**Header:** None</span></span>  
<span data-ttu-id="e5ce8-112">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="e5ce8-112">**Library:** None</span></span>  
<span data-ttu-id="e5ce8-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ce8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e5ce8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5ce8-114">See also</span></span>

- [<span data-ttu-id="e5ce8-115">Énumération de CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="e5ce8-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e5ce8-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="e5ce8-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="e5ce8-117">Interface de IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="e5ce8-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
