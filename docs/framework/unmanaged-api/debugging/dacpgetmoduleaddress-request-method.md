---
title: DacpGetModuleAddress::Méthode de demande
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4dbe6a2c295e5afae1b6761f0c7b695fdb906428
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102905"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="de0fd-102">DacpGetModuleAddress::Méthode de demande</span><span class="sxs-lookup"><span data-stu-id="de0fd-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="de0fd-103">Effectue une demande de remplir la structure de la structure donnée runtime.</span><span class="sxs-lookup"><span data-stu-id="de0fd-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="de0fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de0fd-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="de0fd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="de0fd-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="de0fd-106">[dans] Un pointeur vers le module de données sur les semences.</span><span class="sxs-lookup"><span data-stu-id="de0fd-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="de0fd-107">Notes</span><span class="sxs-lookup"><span data-stu-id="de0fd-107">Remarks</span></span>

<span data-ttu-id="de0fd-108">Cette structure vit à l’intérieur du temps d’exécution et n’est pas exposée à travers des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="de0fd-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="de0fd-109">Pour l’utiliser, le moyen le plus simple est d’imiter la mise en œuvre:</span><span class="sxs-lookup"><span data-stu-id="de0fd-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="de0fd-110">Retournez la valeur obtenue `Request` en `IXCLRDataModule*` appelant la méthode sur le paramètre avec les paramètres suivants :`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="de0fd-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="de0fd-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="de0fd-111">Requirements</span></span>

<span data-ttu-id="de0fd-112">**Plates-formes:** Voir [les exigences du système](../../../../docs/framework/get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="de0fd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md)</span></span>\
<span data-ttu-id="de0fd-113">**En-tête:** Aucun</span><span class="sxs-lookup"><span data-stu-id="de0fd-113">**Header:** None\</span></span>
<span data-ttu-id="de0fd-114">**Bibliothèque:** Aucun</span><span class="sxs-lookup"><span data-stu-id="de0fd-114">**Library:** None\</span></span>
<span data-ttu-id="de0fd-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="de0fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="de0fd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de0fd-116">See also</span></span>

- [<span data-ttu-id="de0fd-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="de0fd-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="de0fd-118">Structure DacpGetModuleAddress</span><span class="sxs-lookup"><span data-stu-id="de0fd-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
