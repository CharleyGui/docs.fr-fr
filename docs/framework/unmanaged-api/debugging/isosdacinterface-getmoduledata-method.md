---
title: ISOSDacInterface::GetModuleData (méthode)
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
ms.openlocfilehash: 97b297def9fba329ff6d9573f7b2e7cc811273f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764719"
---
# <a name="isosdacinterfacegetmoduledata-method"></a><span data-ttu-id="15a8a-102">ISOSDacInterface::GetModuleData (méthode)</span><span class="sxs-lookup"><span data-stu-id="15a8a-102">ISOSDacInterface::GetModuleData Method</span></span>

<span data-ttu-id="15a8a-103">Extrait les données correspondant au module chargé à une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="15a8a-103">Fetches the data corresponding to the module loaded at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="15a8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15a8a-104">Syntax</span></span>

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a><span data-ttu-id="15a8a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="15a8a-105">Parameters</span></span>

`moduleAddr`\
<span data-ttu-id="15a8a-106">[in] L’adresse du module pour récupérer des informations pour.</span><span class="sxs-lookup"><span data-stu-id="15a8a-106">[in] The address of the module to retrieve information for.</span></span>

`data`\
<span data-ttu-id="15a8a-107">[out] Le [DacpModuleData structure](dacpmoduledata-structure.md) pour contenir les informations du module chargé.</span><span class="sxs-lookup"><span data-stu-id="15a8a-107">[out] The [DacpModuleData structure](dacpmoduledata-structure.md) to hold the information of the loaded module.</span></span>

## <a name="remarks"></a><span data-ttu-id="15a8a-108">Notes</span><span class="sxs-lookup"><span data-stu-id="15a8a-108">Remarks</span></span>

<span data-ttu-id="15a8a-109">La méthode fournie fait partie de la `ISOSDacInterface` interface et correspond à l’emplacement de 13 de la table de la méthode virtuelle.</span><span class="sxs-lookup"><span data-stu-id="15a8a-109">The provided method is part of the `ISOSDacInterface` interface and corresponds to the 13th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="15a8a-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="15a8a-110">Requirements</span></span>

<span data-ttu-id="15a8a-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15a8a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="15a8a-112">**En-tête :** Aucun</span><span class="sxs-lookup"><span data-stu-id="15a8a-112">**Header:** None</span></span>  
<span data-ttu-id="15a8a-113">**Bibliothèque :** Aucun</span><span class="sxs-lookup"><span data-stu-id="15a8a-113">**Library:** None</span></span>  
<span data-ttu-id="15a8a-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="15a8a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="15a8a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15a8a-115">See also</span></span>

- [<span data-ttu-id="15a8a-116">Débogage</span><span class="sxs-lookup"><span data-stu-id="15a8a-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="15a8a-117">Interface de ISOSDacInterface</span><span class="sxs-lookup"><span data-stu-id="15a8a-117">ISOSDacInterface Interface</span></span>](isosdacinterface-interface.md)
