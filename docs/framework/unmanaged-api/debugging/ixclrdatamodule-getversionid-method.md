---
title: 'IXCLRDataModule :: GetVersionId, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9d5ef137a5d76c3d7545ab16921352123e978fb1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420862"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="fef59-102">IXCLRDataModule :: GetVersionId, méthode</span><span class="sxs-lookup"><span data-stu-id="fef59-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="fef59-103">Obtient l’identificateur de version du module.</span><span class="sxs-lookup"><span data-stu-id="fef59-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="fef59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fef59-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="fef59-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fef59-105">Parameters</span></span>

`vid`\
<span data-ttu-id="fef59-106">à Identificateur de version du module.</span><span class="sxs-lookup"><span data-stu-id="fef59-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="fef59-107">Notes</span><span class="sxs-lookup"><span data-stu-id="fef59-107">Remarks</span></span>

<span data-ttu-id="fef59-108">La méthode fournie fait partie de l' `IXCLRDataModule` interface et correspond à l’emplacement 41e de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="fef59-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="fef59-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="fef59-109">Requirements</span></span>

<span data-ttu-id="fef59-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fef59-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="fef59-111">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="fef59-111">**Header:** None</span></span>  
<span data-ttu-id="fef59-112">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="fef59-112">**Library:** None</span></span>  
<span data-ttu-id="fef59-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fef59-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="fef59-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fef59-114">See also</span></span>

- [<span data-ttu-id="fef59-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="fef59-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="fef59-116">IXCLRDataModule, interface</span><span class="sxs-lookup"><span data-stu-id="fef59-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
