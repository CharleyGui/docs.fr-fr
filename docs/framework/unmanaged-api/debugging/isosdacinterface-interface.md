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
ms.openlocfilehash: 94349a3f7b18c8ce29bb3a71cb9d10ee4eac8036
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790480"
---
# <a name="isosdacinterface-interface"></a><span data-ttu-id="dbd39-102">ISOSDacInterface, interface</span><span class="sxs-lookup"><span data-stu-id="dbd39-102">ISOSDacInterface Interface</span></span>

<span data-ttu-id="dbd39-103">Fournit des méthodes d’assistance pour accéder aux données à partir de `SOS`.</span><span class="sxs-lookup"><span data-stu-id="dbd39-103">Provides helper methods to access data from `SOS`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="dbd39-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="dbd39-104">Methods</span></span>

| <span data-ttu-id="dbd39-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="dbd39-105">Method</span></span>                                                                                                               | <span data-ttu-id="dbd39-106">Description</span><span class="sxs-lookup"><span data-stu-id="dbd39-106">Description</span></span>                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="dbd39-107">GetMethodDescData</span><span class="sxs-lookup"><span data-stu-id="dbd39-107">GetMethodDescData</span></span>](isosdacinterface-getmethoddescdata-method.md) | <span data-ttu-id="dbd39-108">Obtient les données pour le pointeur MethodDesc donné.</span><span class="sxs-lookup"><span data-stu-id="dbd39-108">Gets the data for the given MethodDesc pointer.</span></span> |
| [<span data-ttu-id="dbd39-109">GetMethodDescPtrFromIP</span><span class="sxs-lookup"><span data-stu-id="dbd39-109">GetMethodDescPtrFromIP</span></span>](isosdacinterface-getmethoddescptrfromip-method.md) | <span data-ttu-id="dbd39-110">Récupère le pointeur de l’MethodDesc correspondant à la méthode contenant l’adresse d’instruction Native donnée.</span><span class="sxs-lookup"><span data-stu-id="dbd39-110">Retrieves the pointer of the MethodDesc corresponding the method containing the given native instruction address.</span></span> |
| [<span data-ttu-id="dbd39-111">GetModuleData</span><span class="sxs-lookup"><span data-stu-id="dbd39-111">GetModuleData</span></span>](isosdacinterface-getmoduledata-method.md)| <span data-ttu-id="dbd39-112">Récupère les données correspondant au module chargé à une adresse donnée.</span><span class="sxs-lookup"><span data-stu-id="dbd39-112">Fetches the data corresponding to the module loaded at a given address.</span></span> |

## <a name="remarks"></a><span data-ttu-id="dbd39-113">Notes</span><span class="sxs-lookup"><span data-stu-id="dbd39-113">Remarks</span></span>

<span data-ttu-id="dbd39-114">Cette interface se trouve à l’intérieur du runtime et n’est pas exposée via des en-têtes ou des fichiers de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="dbd39-114">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="dbd39-115">Toutefois, il s’agit d’une interface COM qui dérive de `IUnknown` avec GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` qui peuvent être obtenus par le biais des mécanismes COM habituels.</span><span class="sxs-lookup"><span data-stu-id="dbd39-115">However, it's a COM interface that derives from `IUnknown` with GUID `436f00f2-b42a-4b9f-870c-e73db66ae930` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="dbd39-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="dbd39-116">Requirements</span></span>

<span data-ttu-id="dbd39-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbd39-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="dbd39-118">**En-tête :** None</span><span class="sxs-lookup"><span data-stu-id="dbd39-118">**Header:** None</span></span>  
<span data-ttu-id="dbd39-119">**Bibliothèque :** None</span><span class="sxs-lookup"><span data-stu-id="dbd39-119">**Library:** None</span></span>  
<span data-ttu-id="dbd39-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dbd39-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dbd39-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbd39-121">See also</span></span>

- [<span data-ttu-id="dbd39-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="dbd39-122">Debugging</span></span>](index.md)
- [<span data-ttu-id="dbd39-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="dbd39-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
