---
title: 'IXCLRDataModule :: GetMethodDefinitionByToken, méthode'
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
ms.openlocfilehash: 074949145be588fc34266a9f2ee501caeeffb9d3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420875"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="9045c-102">IXCLRDataModule :: GetMethodDefinitionByToken, méthode</span><span class="sxs-lookup"><span data-stu-id="9045c-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="9045c-103">Obtient la définition de méthode correspondant à un jeton de métadonnées donné.</span><span class="sxs-lookup"><span data-stu-id="9045c-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9045c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9045c-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="9045c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9045c-105">Parameters</span></span>

`token`\
<span data-ttu-id="9045c-106">dans Jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="9045c-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="9045c-107">à Définition de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9045c-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="9045c-108">Notes</span><span class="sxs-lookup"><span data-stu-id="9045c-108">Remarks</span></span>

<span data-ttu-id="9045c-109">La méthode fournie fait partie de l' `IXCLRDataModule` interface et correspond au 26 emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="9045c-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="9045c-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="9045c-110">Requirements</span></span>

<span data-ttu-id="9045c-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9045c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9045c-112">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="9045c-112">**Header:** None</span></span>  
<span data-ttu-id="9045c-113">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="9045c-113">**Library:** None</span></span>  
<span data-ttu-id="9045c-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9045c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9045c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9045c-115">See also</span></span>

- [<span data-ttu-id="9045c-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="9045c-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="9045c-117">IXCLRDataModule, interface</span><span class="sxs-lookup"><span data-stu-id="9045c-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
