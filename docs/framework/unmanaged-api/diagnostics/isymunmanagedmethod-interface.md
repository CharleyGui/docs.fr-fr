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
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="8ab8b-102">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="8ab8b-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="8ab8b-103">Représente une méthode dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="8ab8b-104">Cette interface fournit l’accès uniquement aux attributs liés aux symboles d’une méthode, plutôt qu’aux attributs liés au type.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ab8b-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8ab8b-105">Methods</span></span>  
  
|<span data-ttu-id="8ab8b-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-106">Method</span></span>|<span data-ttu-id="8ab8b-107">Description</span><span class="sxs-lookup"><span data-stu-id="8ab8b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ab8b-108">GetNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="8ab8b-109">Obtient l’espace de noms dans lequel cette méthode est définie.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="8ab8b-110">GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="8ab8b-111">Retourne l’offset dans cette méthode qui correspond à une position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="8ab8b-112">GetParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="8ab8b-113">Obtient les paramètres de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="8ab8b-114">GetRanges, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="8ab8b-115">À partir d’une position dans un document, retourne un tableau de paires d’offsets de début et de fin qui correspondent aux plages de langage MSIL (Microsoft Intermediate Language) couvertes par la position dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="8ab8b-116">GetRootScope, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="8ab8b-117">Obtient la portée lexicale racine dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="8ab8b-118">Cette portée englobe la totalité de la méthode.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="8ab8b-119">GetScopeFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="8ab8b-120">Obtient la portée lexicale la plus englobante dans cette méthode qui englobe l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="8ab8b-121">GetSequencePointCount, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="8ab8b-122">Obtient le nombre de points de séquence dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="8ab8b-123">GetSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="8ab8b-124">Obtient tous les points de séquence de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="8ab8b-125">GetSourceStartEnd, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="8ab8b-126">Obtient les positions de début et de fin du document pour la source de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="8ab8b-127">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="8ab8b-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="8ab8b-128">Retourne le jeton de métadonnées pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8ab8b-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ab8b-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ab8b-129">Requirements</span></span>  
 <span data-ttu-id="8ab8b-130">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8ab8b-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab8b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ab8b-131">See also</span></span>

- [<span data-ttu-id="8ab8b-132">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="8ab8b-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
