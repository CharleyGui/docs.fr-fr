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
ms.openlocfilehash: ff8ccf42d1131fb15d7473ae12ecefde9d55177f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395279"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="39803-102">IXCLRDataModule :: GetVersionId, méthode</span><span class="sxs-lookup"><span data-stu-id="39803-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="39803-103">Obtient l’identificateur de version du module.</span><span class="sxs-lookup"><span data-stu-id="39803-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="39803-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39803-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="39803-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="39803-105">Parameters</span></span>

`vid`\
<span data-ttu-id="39803-106">à Identificateur de version du module.</span><span class="sxs-lookup"><span data-stu-id="39803-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="39803-107">Notes</span><span class="sxs-lookup"><span data-stu-id="39803-107">Remarks</span></span>

<span data-ttu-id="39803-108">La méthode fournie fait partie de l' `IXCLRDataModule` interface et correspond à l’emplacement 41e de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="39803-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="39803-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="39803-109">Requirements</span></span>

<span data-ttu-id="39803-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39803-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="39803-111">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="39803-111">**Header:** None</span></span>  
<span data-ttu-id="39803-112">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="39803-112">**Library:** None</span></span>  
<span data-ttu-id="39803-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="39803-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="39803-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39803-114">See also</span></span>

- [<span data-ttu-id="39803-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="39803-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="39803-116">IXCLRDataModule, interface</span><span class="sxs-lookup"><span data-stu-id="39803-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
