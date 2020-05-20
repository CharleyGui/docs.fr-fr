---
title: ISymUnmanagedSymbolSearchInfo, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: 308c501e17446719067d2dc0580d698c1770bf53
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610663"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="3e261-102">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="3e261-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>
<span data-ttu-id="3e261-103">Fournit des méthodes qui obtiennent des informations sur le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="3e261-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="3e261-104">Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3e261-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e261-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3e261-105">Methods</span></span>  
  
|<span data-ttu-id="3e261-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="3e261-106">Method</span></span>|<span data-ttu-id="3e261-107">Description</span><span class="sxs-lookup"><span data-stu-id="3e261-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e261-108">GetHRESULT, méthode</span><span class="sxs-lookup"><span data-stu-id="3e261-108">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="3e261-109">Obtient le HRESULT.</span><span class="sxs-lookup"><span data-stu-id="3e261-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="3e261-110">GetSearchPath, méthode</span><span class="sxs-lookup"><span data-stu-id="3e261-110">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="3e261-111">Obtient le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="3e261-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="3e261-112">GetSearchPathLength, méthode</span><span class="sxs-lookup"><span data-stu-id="3e261-112">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="3e261-113">Obtient la longueur du chemin d’accès de recherche.</span><span class="sxs-lookup"><span data-stu-id="3e261-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e261-114">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="3e261-114">Requirements</span></span>  
 <span data-ttu-id="3e261-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3e261-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e261-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e261-116">See also</span></span>

- [<span data-ttu-id="3e261-117">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="3e261-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
