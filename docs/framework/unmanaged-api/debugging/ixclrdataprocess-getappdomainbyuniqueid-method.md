---
title: 'IXCLRDataProcess :: GetAppDomainByUniqueId, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method
helpviewer.keywords:
- IXCLRDataProcess::GetAppDomainByUniqueId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: bb02ffed09cbcc31e653bfd3165050c247908c5d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420780"
---
# <a name="ixclrdataprocessgetappdomainbyuniqueid-method"></a><span data-ttu-id="79bff-102">IXCLRDataProcess :: GetAppDomainByUniqueId, méthode</span><span class="sxs-lookup"><span data-stu-id="79bff-102">IXCLRDataProcess::GetAppDomainByUniqueId Method</span></span>

<span data-ttu-id="79bff-103">Obtient un `AppDomain` dans un processus en fonction de son identificateur unique.</span><span class="sxs-lookup"><span data-stu-id="79bff-103">Gets an `AppDomain` in a process based on its unique identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="79bff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79bff-104">Syntax</span></span>

```cpp
HRESULT GetAppDomainByUniqueID(
    [in] ULONG64               id,
    [out] IXCLRDataAppDomain **appDomain
);
```

## <a name="parameters"></a><span data-ttu-id="79bff-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79bff-105">Parameters</span></span>

`id`\
<span data-ttu-id="79bff-106">dans Identificateur unique de l’AppDomain.</span><span class="sxs-lookup"><span data-stu-id="79bff-106">[in] The unique identifier of the AppDomain</span></span>

`appDomain`\
<span data-ttu-id="79bff-107">à AppDomain</span><span class="sxs-lookup"><span data-stu-id="79bff-107">[out] The AppDomain</span></span>

## <a name="remarks"></a><span data-ttu-id="79bff-108">Notes</span><span class="sxs-lookup"><span data-stu-id="79bff-108">Remarks</span></span>

<span data-ttu-id="79bff-109">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au vingtième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="79bff-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 20th slot of the virtual method table.</span></span> <span data-ttu-id="79bff-110">Le `IXCLRDataAppDomain*` retourné est utilisé pour l’interaction avec d’autres API.</span><span class="sxs-lookup"><span data-stu-id="79bff-110">The `IXCLRDataAppDomain*` returned is used for interaction with other APIs.</span></span>

## <a name="requirements"></a><span data-ttu-id="79bff-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="79bff-111">Requirements</span></span>

<span data-ttu-id="79bff-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79bff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="79bff-113">**En-tête :** **Bibliothèque None :** aucune **.NET Framework versions :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="79bff-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="79bff-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79bff-114">See also</span></span>

- [<span data-ttu-id="79bff-115">Débogage</span><span class="sxs-lookup"><span data-stu-id="79bff-115">Debugging</span></span>](index.md)
- [<span data-ttu-id="79bff-116">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="79bff-116">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
