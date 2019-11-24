---
title: ISymUnmanagedMethod, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: 1d3ccb2265f056d5776199d997dc067c8d5513e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448784"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="e14ee-102">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="e14ee-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="e14ee-103">Represents a method within the symbol store.</span><span class="sxs-lookup"><span data-stu-id="e14ee-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="e14ee-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span><span class="sxs-lookup"><span data-stu-id="e14ee-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e14ee-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e14ee-105">Methods</span></span>  
  
|<span data-ttu-id="e14ee-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-106">Method</span></span>|<span data-ttu-id="e14ee-107">Description</span><span class="sxs-lookup"><span data-stu-id="e14ee-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e14ee-108">GetNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="e14ee-109">Gets the namespace within which this method is defined.</span><span class="sxs-lookup"><span data-stu-id="e14ee-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="e14ee-110">GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="e14ee-111">Returns the offset within this method that corresponds to a given position within a document.</span><span class="sxs-lookup"><span data-stu-id="e14ee-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="e14ee-112">GetParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="e14ee-113">Gets the parameters for this method.</span><span class="sxs-lookup"><span data-stu-id="e14ee-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="e14ee-114">GetRanges, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="e14ee-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span><span class="sxs-lookup"><span data-stu-id="e14ee-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="e14ee-116">GetRootScope, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="e14ee-117">Gets the root lexical scope within this method.</span><span class="sxs-lookup"><span data-stu-id="e14ee-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="e14ee-118">Cette portée englobe la totalité de la méthode.</span><span class="sxs-lookup"><span data-stu-id="e14ee-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="e14ee-119">GetScopeFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="e14ee-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span><span class="sxs-lookup"><span data-stu-id="e14ee-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="e14ee-121">GetSequencePointCount, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="e14ee-122">Gets the count of sequence points within this method.</span><span class="sxs-lookup"><span data-stu-id="e14ee-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="e14ee-123">GetSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="e14ee-124">Gets all the sequence points within this method.</span><span class="sxs-lookup"><span data-stu-id="e14ee-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="e14ee-125">GetSourceStartEnd, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="e14ee-126">Gets the start and end document positions for the source of this method.</span><span class="sxs-lookup"><span data-stu-id="e14ee-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="e14ee-127">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="e14ee-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="e14ee-128">Returns the metadata token for this method.</span><span class="sxs-lookup"><span data-stu-id="e14ee-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e14ee-129">spécifications</span><span class="sxs-lookup"><span data-stu-id="e14ee-129">Requirements</span></span>  
 <span data-ttu-id="e14ee-130">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e14ee-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e14ee-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e14ee-131">See also</span></span>

- [<span data-ttu-id="e14ee-132">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="e14ee-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
