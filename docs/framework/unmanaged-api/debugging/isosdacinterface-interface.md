---
title: ISOSDacInterface, interface
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: c9b4e6e5b36fe38b6c0ea78f6d1848d155008bcc
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420966"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="4434b-102">ISOSDacInterface, interface</span><span class="sxs-lookup"><span data-stu-id="4434b-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="4434b-103">Fournit des méthodes d’assistance pour accéder aux données à partir de `SOS` .</span><span class="sxs-lookup"><span data-stu-id="4434b-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="4434b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4434b-104">Methods</span></span>

| <span data-ttu-id="4434b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4434b-105">Method</span></span>                                                                                                               | <span data-ttu-id="4434b-106">Description</span><span class="sxs-lookup"><span data-stu-id="4434b-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="4434b-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="4434b-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="4434b-108">Obtient les données pour le pointeur MethodDesc donné.</span><span class="sxs-lookup"><span data-stu-id="4434b-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="4434b-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="4434b-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="4434b-110">Récupère le pointeur de l’MethodDesc correspondant à la méthode contenant l’adresse d’instruction Native donnée.</span><span class="sxs-lookup"><span data-stu-id="4434b-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="4434b-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="4434b-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="4434b-112">Récupère les données correspondant au module chargé à une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="4434b-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4434b-113">Notes</span><span class="sxs-lookup"><span data-stu-id="4434b-113">Remarks</span></span>

<span data-ttu-id="4434b-114">Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="4434b-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="4434b-115">Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec `436f00f2-b42a-4b9f-870c-e73db66ae930` un GUID qui peut être obtenu par le biais des mécanismes com habituels.</span><span class="sxs-lookup"><span data-stu-id="4434b-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="4434b-116">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="4434b-116">Requirements</span></span>

<span data-ttu-id="4434b-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4434b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="4434b-118">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="4434b-118">**Header:** None</span></span>  
<span data-ttu-id="4434b-119">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="4434b-119">**Library:** None</span></span>  
<span data-ttu-id="4434b-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4434b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4434b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4434b-121">See also</span></span>

- [<span data-ttu-id="4434b-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="4434b-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="4434b-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4434b-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
