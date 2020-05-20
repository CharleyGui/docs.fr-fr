---
title: IXCLRDataModule, interface
ms.date: 01/16/2019
api.name:
- IXCLRDataModule Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule Interface
helpviewer.keywords:
- IXCLRDataModule Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 3c2bc771c0a131329b9403c99a33ca7b79023771
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420849"
---
# <a name="ixclrdatamodule-interface"></a><span data-ttu-id="8bba6-102">IXCLRDataModule, interface</span><span class="sxs-lookup"><span data-stu-id="8bba6-102">IXCLRDataModule Interface</span></span>

<span data-ttu-id="8bba6-103">Fournit des méthodes pour interroger des informations sur un module chargé.</span><span class="sxs-lookup"><span data-stu-id="8bba6-103">Provides methods for querying information about a loaded module.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="8bba6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8bba6-104">Methods</span></span>

| <span data-ttu-id="8bba6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="8bba6-105">Method</span></span>                                                                                                                                | <span data-ttu-id="8bba6-106">Description</span><span class="sxs-lookup"><span data-stu-id="8bba6-106">Description</span></span>                                                         |
| ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="8bba6-107">GetMethodDefinitionByToken</span><span class="sxs-lookup"><span data-stu-id="8bba6-107">GetMethodDefinitionByToken</span></span>](ixclrdatamodule-getmethoddefinitionbytoken-method.md) | <span data-ttu-id="8bba6-108">Obtient la définition de méthode correspondant à un jeton de métadonnées donné.</span><span class="sxs-lookup"><span data-stu-id="8bba6-108">Gets the method definition corresponding to a given metadata token.</span></span> |
| [<span data-ttu-id="8bba6-109">Requête</span><span class="sxs-lookup"><span data-stu-id="8bba6-109">Request</span></span>](ixclrdatamodule-request-method.md)                                       | <span data-ttu-id="8bba6-110">Demandes de remplissage de la mémoire tampon donnée avec les données du module.</span><span class="sxs-lookup"><span data-stu-id="8bba6-110">Requests to populate the buffer given with the module's data.</span></span>       |
| [<span data-ttu-id="8bba6-111">GetVersionId</span><span class="sxs-lookup"><span data-stu-id="8bba6-111">GetVersionId</span></span>](ixclrdatamodule-getversionid-method.md)                             | <span data-ttu-id="8bba6-112">Obtient l’ID de version du module.</span><span class="sxs-lookup"><span data-stu-id="8bba6-112">Gets the module's version ID.</span></span>                                       |

## <a name="remarks"></a><span data-ttu-id="8bba6-113">Notes</span><span class="sxs-lookup"><span data-stu-id="8bba6-113">Remarks</span></span>

<span data-ttu-id="8bba6-114">Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="8bba6-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="8bba6-115">Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` un GUID qui peut être obtenu par le biais des mécanismes com habituels.</span><span class="sxs-lookup"><span data-stu-id="8bba6-115">However, it's a COM interface that derives from `IUnknown` with GUID `88E32849-0A0A-4cb0-9022-7CD2E9E139E2` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="8bba6-116">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="8bba6-116">Requirements</span></span>

<span data-ttu-id="8bba6-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bba6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="8bba6-118">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="8bba6-118">**Header:** None</span></span>  
<span data-ttu-id="8bba6-119">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="8bba6-119">**Library:** None</span></span>  
<span data-ttu-id="8bba6-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8bba6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8bba6-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8bba6-121">See also</span></span>

- [<span data-ttu-id="8bba6-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="8bba6-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="8bba6-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8bba6-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
