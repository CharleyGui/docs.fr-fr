---
title: DacpGetModuleAddress::Request, méthode
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
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860840"
---
# <a name="dacpgetmoduleaddressrequest-method"></a><span data-ttu-id="166db-102">DacpGetModuleAddress::Request, méthode</span><span class="sxs-lookup"><span data-stu-id="166db-102">DacpGetModuleAddress::Request Method</span></span>

<span data-ttu-id="166db-103">Exécute une requête pour remplir la structure à partir de la structure d’exécution donnée.</span><span class="sxs-lookup"><span data-stu-id="166db-103">Performs a request to populate the structure from the given runtime structure.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="166db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="166db-104">Syntax</span></span>

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a><span data-ttu-id="166db-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="166db-105">Parameters</span></span>

`pDataModule`\
<span data-ttu-id="166db-106">dans Pointeur vers le module de données de départ.</span><span class="sxs-lookup"><span data-stu-id="166db-106">[in] A pointer to the seed data module.</span></span>

## <a name="remarks"></a><span data-ttu-id="166db-107">Notes </span><span class="sxs-lookup"><span data-stu-id="166db-107">Remarks</span></span>

<span data-ttu-id="166db-108">Cette structure se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="166db-108">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="166db-109">Pour l’utiliser, le moyen le plus simple consiste à imiter l’implémentation :</span><span class="sxs-lookup"><span data-stu-id="166db-109">To use it, the easiest way is to mimic the implementation:</span></span>

- <span data-ttu-id="166db-110">Retournez la valeur obtenue à partir de `Request` l’appel de `IXCLRDataModule*` la méthode sur le paramètre avec les paramètres suivants :`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span><span class="sxs-lookup"><span data-stu-id="166db-110">Return the value obtained from calling the `Request` method on the `IXCLRDataModule*` parameter with the following parameters: `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`</span></span>

## <a name="requirements"></a><span data-ttu-id="166db-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="166db-111">Requirements</span></span>

<span data-ttu-id="166db-112">**Plateformes :** Voir [Configuration système requise](../../get-started/system-requirements.md)</span><span class="sxs-lookup"><span data-stu-id="166db-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md)</span></span>\
<span data-ttu-id="166db-113">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="166db-113">**Header:** None\</span></span>
<span data-ttu-id="166db-114">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="166db-114">**Library:** None\</span></span>
<span data-ttu-id="166db-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="166db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="166db-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="166db-116">See also</span></span>

- [<span data-ttu-id="166db-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="166db-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="166db-118">DacpGetModuleAddress, structure</span><span class="sxs-lookup"><span data-stu-id="166db-118">DacpGetModuleAddress structure</span></span>](dacpgetmoduleaddress-structure.md)
