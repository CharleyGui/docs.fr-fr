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
ms.openlocfilehash: 8da4da38d23ed65a0fdc44a0f919ee8cad2fe18e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446268"
---
# <a name="isymunmanagedscope-interface"></a><span data-ttu-id="0d4ca-102">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="0d4ca-102">ISymUnmanagedScope Interface</span></span>
<span data-ttu-id="0d4ca-103">Représente une portée lexicale dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-103">Represents a lexical scope within a method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d4ca-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0d4ca-104">Methods</span></span>  
  
|<span data-ttu-id="0d4ca-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0d4ca-105">Method</span></span>|<span data-ttu-id="0d4ca-106">Description</span><span class="sxs-lookup"><span data-stu-id="0d4ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d4ca-107">GetChildren, méthode</span><span class="sxs-lookup"><span data-stu-id="0d4ca-107">GetChildren Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|<span data-ttu-id="0d4ca-108">Obtient les enfants de cette portée.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-108">Gets the children of this scope.</span></span>|  
|[<span data-ttu-id="0d4ca-109">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="0d4ca-109">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|<span data-ttu-id="0d4ca-110">Obtient l’offset de fin pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-110">Gets the end offset for this scope.</span></span>|  
|[<span data-ttu-id="0d4ca-111">GetLocalCount, méthode</span><span class="sxs-lookup"><span data-stu-id="0d4ca-111">GetLocalCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|<span data-ttu-id="0d4ca-112">Obtient le nombre de variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-112">Gets a count of the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="0d4ca-113">GetLocals, méthode</span><span class="sxs-lookup"><span data-stu-id="0d4ca-113">GetLocals Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|<span data-ttu-id="0d4ca-114">Obtient les variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-114">Gets the local variables defined within this scope.</span></span>|  
|[<span data-ttu-id="0d4ca-115">GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="0d4ca-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|<span data-ttu-id="0d4ca-116">Obtient la méthode qui contient cette portée.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-116">Gets the method that contains this scope.</span></span>|  
|[<span data-ttu-id="0d4ca-117">GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="0d4ca-117">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|<span data-ttu-id="0d4ca-118">Obtient les espaces de noms utilisés dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-118">Gets the namespaces that are being used within this scope.</span></span>|  
|[<span data-ttu-id="0d4ca-119">GetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="0d4ca-119">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|<span data-ttu-id="0d4ca-120">Obtient la portée parente de cette portée.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-120">Gets the parent scope of this scope.</span></span>|  
|[<span data-ttu-id="0d4ca-121">GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="0d4ca-121">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|<span data-ttu-id="0d4ca-122">Obtient le décalage de début pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="0d4ca-122">Gets the start offset for this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d4ca-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0d4ca-123">Requirements</span></span>  
 <span data-ttu-id="0d4ca-124">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0d4ca-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d4ca-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d4ca-125">See also</span></span>

- [<span data-ttu-id="0d4ca-126">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="0d4ca-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0d4ca-127">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="0d4ca-127">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
