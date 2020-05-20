---
title: 'IXCLRDataProcess :: EndEnumModules, méthode'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 9a7a23e53f5c2bc7d643046830cf335fec780f11
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420836"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="984ac-102">IXCLRDataProcess :: EndEnumModules, méthode</span><span class="sxs-lookup"><span data-stu-id="984ac-102">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="984ac-103">Libère les ressources utilisées par les itérateurs internes utilisés pendant l’énumération des modules.</span><span class="sxs-lookup"><span data-stu-id="984ac-103">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="984ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="984ac-104">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="984ac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="984ac-105">Parameters</span></span>

`handle`\
<span data-ttu-id="984ac-106">à Handle pour énumérer les modules.</span><span class="sxs-lookup"><span data-stu-id="984ac-106">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="984ac-107">Notes</span><span class="sxs-lookup"><span data-stu-id="984ac-107">Remarks</span></span>

<span data-ttu-id="984ac-108">La méthode fournie fait partie de l' `IXCLRDataProcess` interface et correspond au 26 emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="984ac-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="984ac-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="984ac-109">Requirements</span></span>

<span data-ttu-id="984ac-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="984ac-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="984ac-111">**En-tête :** **Bibliothèque None :** aucune **.NET Framework versions :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="984ac-111">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="984ac-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="984ac-112">See also</span></span>

- [<span data-ttu-id="984ac-113">Débogage</span><span class="sxs-lookup"><span data-stu-id="984ac-113">Debugging</span></span>](index.md)
- [<span data-ttu-id="984ac-114">IXCLRDataProcess, interface</span><span class="sxs-lookup"><span data-stu-id="984ac-114">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
