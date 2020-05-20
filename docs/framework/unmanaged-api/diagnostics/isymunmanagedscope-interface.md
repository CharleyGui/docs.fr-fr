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
ms.openlocfilehash: 1ee406c97fa4ccb7f87098cba2925568d8ce069f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615343"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="57eb5-102">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="57eb5-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="57eb5-103">Représente une portée lexicale dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="57eb5-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57eb5-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="57eb5-104">Methods</span></span>  
  
|<span data-ttu-id="57eb5-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="57eb5-105">Method</span></span>|<span data-ttu-id="57eb5-106">Description</span><span class="sxs-lookup"><span data-stu-id="57eb5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57eb5-107">GetChildren, méthode</span><span class="sxs-lookup"><span data-stu-id="57eb5-107">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="57eb5-108">Obtient les enfants de cette portée.</span><span class="sxs-lookup"><span data-stu-id="57eb5-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="57eb5-109">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="57eb5-109">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="57eb5-110">Obtient l’offset de fin pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="57eb5-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="57eb5-111">GetLocalCount, méthode</span><span class="sxs-lookup"><span data-stu-id="57eb5-111">GetLocalCount Method</span></span>](isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="57eb5-112">Obtient le nombre de variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="57eb5-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="57eb5-113">GetLocals, méthode</span><span class="sxs-lookup"><span data-stu-id="57eb5-113">GetLocals Method</span></span>](isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="57eb5-114">Obtient les variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="57eb5-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="57eb5-115">GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="57eb5-115">GetMethod Method</span></span>](isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="57eb5-116">Obtient la méthode qui contient cette portée.</span><span class="sxs-lookup"><span data-stu-id="57eb5-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="57eb5-117">GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="57eb5-117">GetNamespaces Method</span></span>](isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="57eb5-118">Obtient les espaces de noms utilisés dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="57eb5-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="57eb5-119">GetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="57eb5-119">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)|<span data-ttu-id="57eb5-120">Obtient la portée parente de cette portée.</span><span class="sxs-lookup"><span data-stu-id="57eb5-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="57eb5-121">GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="57eb5-121">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="57eb5-122">Obtient le décalage de début pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="57eb5-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57eb5-123">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="57eb5-123">Requirements</span></span>  
 <span data-ttu-id="57eb5-124">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="57eb5-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57eb5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57eb5-125">See also</span></span>

- [<span data-ttu-id="57eb5-126">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="57eb5-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="57eb5-127">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="57eb5-127">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
