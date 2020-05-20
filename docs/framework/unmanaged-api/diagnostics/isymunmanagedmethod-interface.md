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
ms.openlocfilehash: 7a98a0c40f68cef9bab1ea2de0850208aaef77a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615122"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="c5773-102">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="c5773-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="c5773-103">Représente une méthode dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="c5773-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="c5773-104">Cette interface fournit l’accès uniquement aux attributs liés aux symboles d’une méthode, plutôt qu’aux attributs liés au type.</span><span class="sxs-lookup"><span data-stu-id="c5773-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5773-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c5773-105">Methods</span></span>  
  
|<span data-ttu-id="c5773-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-106">Method</span></span>|<span data-ttu-id="c5773-107">Description</span><span class="sxs-lookup"><span data-stu-id="c5773-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5773-108">GetNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-108">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="c5773-109">Obtient l’espace de noms dans lequel cette méthode est définie.</span><span class="sxs-lookup"><span data-stu-id="c5773-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="c5773-110">GetOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-110">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="c5773-111">Retourne l’offset dans cette méthode qui correspond à une position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="c5773-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="c5773-112">GetParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-112">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="c5773-113">Obtient les paramètres de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c5773-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="c5773-114">GetRanges, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-114">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="c5773-115">À partir d’une position dans un document, retourne un tableau de paires d’offsets de début et de fin qui correspondent aux plages de langage MSIL (Microsoft Intermediate Language) couvertes par la position dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c5773-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="c5773-116">GetRootScope, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-116">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="c5773-117">Obtient la portée lexicale racine dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c5773-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="c5773-118">Cette portée englobe la totalité de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c5773-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="c5773-119">GetScopeFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-119">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="c5773-120">Obtient la portée lexicale la plus englobante dans cette méthode qui englobe l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="c5773-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="c5773-121">GetSequencePointCount, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-121">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="c5773-122">Obtient le nombre de points de séquence dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c5773-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="c5773-123">GetSequencePoints, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-123">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="c5773-124">Obtient tous les points de séquence de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c5773-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="c5773-125">GetSourceStartEnd, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-125">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="c5773-126">Obtient les positions de début et de fin du document pour la source de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c5773-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="c5773-127">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="c5773-127">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="c5773-128">Retourne le jeton de métadonnées de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c5773-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5773-129">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="c5773-129">Requirements</span></span>  
 <span data-ttu-id="c5773-130">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c5773-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5773-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5773-131">See also</span></span>

- [<span data-ttu-id="c5773-132">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="c5773-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
