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
ms.openlocfilehash: 95ad3cbea4269173f22e662d15772ff97f7ee900
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705447"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a><span data-ttu-id="4cb57-102">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="4cb57-102">ISymUnmanagedSymbolSearchInfo Interface</span></span>

<span data-ttu-id="4cb57-103">Fournit des méthodes qui obtiennent des informations sur le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="4cb57-103">Provides methods that get information about the search path.</span></span> <span data-ttu-id="4cb57-104">Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4cb57-104">Obtain this interface by calling `QueryInterface` on an object that implements the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4cb57-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4cb57-105">Methods</span></span>  
  
|<span data-ttu-id="4cb57-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="4cb57-106">Method</span></span>|<span data-ttu-id="4cb57-107">Description</span><span class="sxs-lookup"><span data-stu-id="4cb57-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4cb57-108">GetHRESULT, méthode</span><span class="sxs-lookup"><span data-stu-id="4cb57-108">GetHRESULT Method</span></span>](isymunmanagedsymbolsearchinfo-gethresult-method.md)|<span data-ttu-id="4cb57-109">Obtient le HRESULT.</span><span class="sxs-lookup"><span data-stu-id="4cb57-109">Gets the HRESULT.</span></span>|  
|[<span data-ttu-id="4cb57-110">GetSearchPath, méthode</span><span class="sxs-lookup"><span data-stu-id="4cb57-110">GetSearchPath Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|<span data-ttu-id="4cb57-111">Obtient le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="4cb57-111">Gets the search path.</span></span>|  
|[<span data-ttu-id="4cb57-112">GetSearchPathLength, méthode</span><span class="sxs-lookup"><span data-stu-id="4cb57-112">GetSearchPathLength Method</span></span>](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|<span data-ttu-id="4cb57-113">Obtient la longueur du chemin d’accès de recherche.</span><span class="sxs-lookup"><span data-stu-id="4cb57-113">Gets the search path length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4cb57-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4cb57-114">Requirements</span></span>  

 <span data-ttu-id="4cb57-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4cb57-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cb57-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cb57-116">See also</span></span>

- [<span data-ttu-id="4cb57-117">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="4cb57-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
