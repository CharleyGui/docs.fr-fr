---
title: ISymUnmanagedScope, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: 9256342ad3a91e6770d6fd19d9d2f94fab267d3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725883"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="0a8a6-102">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="0a8a6-102">ISymUnmanagedScope Interface</span></span>

<span data-ttu-id="0a8a6-103">Représente une portée lexicale dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="0a8a6-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a8a6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0a8a6-104">Methods</span></span>  
  
|<span data-ttu-id="0a8a6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0a8a6-105">Method</span></span>|<span data-ttu-id="0a8a6-106">Description</span><span class="sxs-lookup"><span data-stu-id="0a8a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a8a6-107">GetChildren, méthode</span><span class="sxs-lookup"><span data-stu-id="0a8a6-107">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="0a8a6-108">Obtient les enfants de cette portée.</span><span class="sxs-lookup"><span data-stu-id="0a8a6-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="0a8a6-109">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="0a8a6-109">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="0a8a6-110">Obtient l’offset de fin pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="0a8a6-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="0a8a6-111">GetLocalCount, méthode</span><span class="sxs-lookup"><span data-stu-id="0a8a6-111">GetLocalCount Method</span></span>](isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="0a8a6-112">Obtient le nombre de variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="0a8a6-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="0a8a6-113">GetLocals, méthode</span><span class="sxs-lookup"><span data-stu-id="0a8a6-113">GetLocals Method</span></span>](isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="0a8a6-114">Obtient les variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="0a8a6-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="0a8a6-115">GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="0a8a6-115">GetMethod Method</span></span>](isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="0a8a6-116">Obtient la méthode qui contient cette portée.</span><span class="sxs-lookup"><span data-stu-id="0a8a6-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="0a8a6-117">GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="0a8a6-117">GetNamespaces Method</span></span>](isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="0a8a6-118">Obtient les espaces de noms utilisés dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="0a8a6-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="0a8a6-119">GetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="0a8a6-119">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)|<span data-ttu-id="0a8a6-120">Obtient la portée parente de cette portée.</span><span class="sxs-lookup"><span data-stu-id="0a8a6-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="0a8a6-121">GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="0a8a6-121">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="0a8a6-122">Obtient le décalage de début pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="0a8a6-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a8a6-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0a8a6-123">Requirements</span></span>  

 <span data-ttu-id="0a8a6-124">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0a8a6-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8a6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a8a6-125">See also</span></span>

- [<span data-ttu-id="0a8a6-126">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="0a8a6-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0a8a6-127">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="0a8a6-127">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
