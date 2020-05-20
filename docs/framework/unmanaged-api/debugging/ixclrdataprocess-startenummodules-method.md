---
title: 'IXCLRDataProcess :: StartEnumModules, méthode'
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
ms.openlocfilehash: d55b07ea3fada73237919bf677163a9096d5ad04
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420719"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="caffe-102">IXCLRDataProcess :: StartEnumModules, méthode</span><span class="sxs-lookup"><span data-stu-id="caffe-102">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="caffe-103">Fournit un handle pour énumérer les modules d’un processus.</span><span class="sxs-lookup"><span data-stu-id="caffe-103">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="caffe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caffe-104">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="caffe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="caffe-105">Parameters</span></span>

`handle`\
<span data-ttu-id="caffe-106">à Handle pour énumérer les modules.</span><span class="sxs-lookup"><span data-stu-id="caffe-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="caffe-107">Notes</span><span class="sxs-lookup"><span data-stu-id="caffe-107">Remarks</span></span>

<span data-ttu-id="caffe-108">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond à l’emplacement 24 de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="caffe-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="caffe-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="caffe-109">Requirements</span></span>

<span data-ttu-id="caffe-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caffe-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="caffe-111">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="caffe-111">**Header:** None</span></span>  
<span data-ttu-id="caffe-112">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="caffe-112">**Library:** None</span></span>  
<span data-ttu-id="caffe-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="caffe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="caffe-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="caffe-114">See also</span></span>

- [<span data-ttu-id="caffe-115">Énumération CLRDataSourceType</span><span class="sxs-lookup"><span data-stu-id="caffe-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="caffe-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="caffe-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="caffe-117">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="caffe-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
