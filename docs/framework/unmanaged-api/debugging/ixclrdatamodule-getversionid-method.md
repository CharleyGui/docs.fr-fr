---
title: IXCLRDataModule::GetVersionId (méthode)
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
ms.openlocfilehash: 5bd84f784ea92e7b2ce2465e64972dc84e16a16c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744704"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="17cf4-102">IXCLRDataModule::GetVersionId (méthode)</span><span class="sxs-lookup"><span data-stu-id="17cf4-102">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="17cf4-103">Obtient l’identificateur de version du module.</span><span class="sxs-lookup"><span data-stu-id="17cf4-103">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="17cf4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17cf4-104">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="17cf4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17cf4-105">Parameters</span></span>

`vid`\
<span data-ttu-id="17cf4-106">[out] Identificateur de version du module.</span><span class="sxs-lookup"><span data-stu-id="17cf4-106">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="17cf4-107">Notes</span><span class="sxs-lookup"><span data-stu-id="17cf4-107">Remarks</span></span>

<span data-ttu-id="17cf4-108">La méthode fournie fait partie de la `IXCLRDataModule` interface et correspond à l’emplacement 40E de la table de la méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="17cf4-108">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 40th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="17cf4-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="17cf4-109">Requirements</span></span>

<span data-ttu-id="17cf4-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17cf4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="17cf4-111">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="17cf4-111">**Header:** None</span></span>  
<span data-ttu-id="17cf4-112">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="17cf4-112">**Library:** None</span></span>  
<span data-ttu-id="17cf4-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="17cf4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="17cf4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17cf4-114">See also</span></span>

- [<span data-ttu-id="17cf4-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="17cf4-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="17cf4-116">Interface de IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="17cf4-116">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
