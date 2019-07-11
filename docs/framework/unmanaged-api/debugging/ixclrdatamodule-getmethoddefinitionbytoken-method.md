---
title: IXCLRDataModule::GetMethodDefinitionByToken Method
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
ms.openlocfilehash: 2c0cf56f108396226b7c7399f6da75e5f47d36f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744672"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="bbe00-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span><span class="sxs-lookup"><span data-stu-id="bbe00-102">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="bbe00-103">Obtient la définition de méthode correspondant à un jeton de métadonnées donné.</span><span class="sxs-lookup"><span data-stu-id="bbe00-103">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="bbe00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbe00-104">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="bbe00-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bbe00-105">Parameters</span></span>

`token`\
<span data-ttu-id="bbe00-106">[in] Le jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="bbe00-106">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="bbe00-107">[out] La définition de méthode.</span><span class="sxs-lookup"><span data-stu-id="bbe00-107">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbe00-108">Notes</span><span class="sxs-lookup"><span data-stu-id="bbe00-108">Remarks</span></span>

<span data-ttu-id="bbe00-109">La méthode fournie fait partie de la `IXCLRDataModule` interface et correspond à l’emplacement de la table de la méthode virtuelle de 25.</span><span class="sxs-lookup"><span data-stu-id="bbe00-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbe00-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bbe00-110">Requirements</span></span>

<span data-ttu-id="bbe00-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbe00-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="bbe00-112">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="bbe00-112">**Header:** None</span></span>  
<span data-ttu-id="bbe00-113">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="bbe00-113">**Library:** None</span></span>  
<span data-ttu-id="bbe00-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bbe00-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="bbe00-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bbe00-115">See also</span></span>

- [<span data-ttu-id="bbe00-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="bbe00-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="bbe00-117">Interface de IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="bbe00-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
