---
title: IAssemblyCacheItem, interface
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: ccc9387a-9f44-4f4f-bf8f-0ea6d2afa21b
topic_type:
- apiref
ms.openlocfilehash: 2493b5338824e1eab3f82a9023bbcced59a98fc8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134464"
---
# <a name="iassemblycacheitem-interface"></a><span data-ttu-id="0393a-102">IAssemblyCacheItem, interface</span><span class="sxs-lookup"><span data-stu-id="0393a-102">IAssemblyCacheItem Interface</span></span>
<span data-ttu-id="0393a-103">Représente un assembly unique dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="0393a-103">Represents a single assembly in the global assembly cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0393a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0393a-104">Methods</span></span>  
  
|<span data-ttu-id="0393a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0393a-105">Method</span></span>|<span data-ttu-id="0393a-106">Description</span><span class="sxs-lookup"><span data-stu-id="0393a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0393a-107">AbortItem, méthode</span><span class="sxs-lookup"><span data-stu-id="0393a-107">AbortItem Method</span></span>](iassemblycacheitem-abortitem-method.md)|<span data-ttu-id="0393a-108">Permet à l’assembly dans le Global Assembly Cache d’effectuer des opérations de nettoyage avant qu’il ne soit libéré.</span><span class="sxs-lookup"><span data-stu-id="0393a-108">Allows the assembly in the global assembly cache to perform cleanup operations before it is released.</span></span>|  
|[<span data-ttu-id="0393a-109">Commit, méthode</span><span class="sxs-lookup"><span data-stu-id="0393a-109">Commit Method</span></span>](iassemblycacheitem-commit-method.md)|<span data-ttu-id="0393a-110">Valide la référence de l’assembly mis en cache dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="0393a-110">Commits the cached assembly reference to memory.</span></span>|  
|[<span data-ttu-id="0393a-111">CreateStream, méthode</span><span class="sxs-lookup"><span data-stu-id="0393a-111">CreateStream Method</span></span>](iassemblycacheitem-createstream-method.md)|<span data-ttu-id="0393a-112">Crée un flux de donnée avec le nom et le format spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0393a-112">Creates a stream with the specified name and format.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0393a-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="0393a-113">Requirements</span></span>  
 <span data-ttu-id="0393a-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0393a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0393a-115">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="0393a-115">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0393a-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0393a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0393a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0393a-117">See also</span></span>

- [<span data-ttu-id="0393a-118">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="0393a-118">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="0393a-119">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="0393a-119">Global Assembly Cache</span></span>](../../app-domains/gac.md)
- [<span data-ttu-id="0393a-120">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="0393a-120">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
