---
title: IXCLRDataModule::GetMethodDefinitionByToken Méthode
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 294c5340caf2217f9337d654a11a63a43d46febd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176667"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="ae012-102">IXCLRDataModule::GetMethodDefinitionByToken Méthode</span><span class="sxs-lookup"><span data-stu-id="ae012-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="ae012-103">Obtient la définition de méthode correspondant à un jeton de métadonnées donné.</span><span class="sxs-lookup"><span data-stu-id="ae012-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ae012-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae012-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="ae012-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae012-105">Parameters</span></span>

`token`\
<span data-ttu-id="ae012-106">[dans] Le jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="ae012-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="ae012-107">[out] La définition de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ae012-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae012-108">Notes </span><span class="sxs-lookup"><span data-stu-id="ae012-108">Remarks</span></span>

<span data-ttu-id="ae012-109">La méthode fournie fait `IXCLRDataModule` partie de l’interface et correspond à la 25ème fente de la table de méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="ae012-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae012-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ae012-110">Requirements</span></span>

<span data-ttu-id="ae012-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae012-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ae012-112">**En-tête:** Aucun</span><span class="sxs-lookup"><span data-stu-id="ae012-112">**Header:** None</span></span>  
<span data-ttu-id="ae012-113">**Bibliothèque:** Aucun</span><span class="sxs-lookup"><span data-stu-id="ae012-113">**Library:** None</span></span>  
<span data-ttu-id="ae012-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ae012-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ae012-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae012-115">See also</span></span>

- [<span data-ttu-id="ae012-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="ae012-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="ae012-117">IXCLRDataModule, interface</span><span class="sxs-lookup"><span data-stu-id="ae012-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
