---
title: 'ISOSDacInterface :: GetModuleData, méthode'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b302100eb6cbfa83896cd358762c496ea01f7509
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420979"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="59042-102">ISOSDacInterface :: GetModuleData, méthode</span><span class="sxs-lookup"><span data-stu-id="59042-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="59042-103">Récupère les données correspondant au module chargé à une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="59042-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="59042-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59042-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="59042-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59042-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="59042-106">dans Adresse du module pour lequel des informations doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="59042-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="59042-107">à La [structure DacpModuleData](dacpmoduledata-structure.md) pour contenir les informations du module chargé.</span><span class="sxs-lookup"><span data-stu-id="59042-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="59042-108">Notes</span><span class="sxs-lookup"><span data-stu-id="59042-108">Remarks</span></span>

<span data-ttu-id="59042-109">La méthode fournie fait partie de l' `ISOSDacInterface` interface et correspond au quatorzième emplacement de la table de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="59042-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 14th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="59042-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="59042-110">Requirements</span></span>

<span data-ttu-id="59042-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59042-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="59042-112">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="59042-112">**Header:** None</span></span>  
<span data-ttu-id="59042-113">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="59042-113">**Library:** None</span></span>  
<span data-ttu-id="59042-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="59042-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="59042-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59042-115">See also</span></span>

- [<span data-ttu-id="59042-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="59042-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="59042-117">ISOSDacInterface, interface</span><span class="sxs-lookup"><span data-stu-id="59042-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
