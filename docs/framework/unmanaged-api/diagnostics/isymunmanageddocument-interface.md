---
title: ISymUnmanagedDocument, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: a8ff6d3a925773e58e0713a87b167420c246f85b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615564"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="9e289-102">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="9e289-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="9e289-103">Représente un document référencé par un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="9e289-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="9e289-104">Un document est défini par une URL (Uniform Resource Locator) et un GUID de type de document.</span><span class="sxs-lookup"><span data-stu-id="9e289-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="9e289-105">Vous pouvez localiser le document, quelle que soit la manière dont il est stocké à l’aide de l’URL et du GUID du type de document.</span><span class="sxs-lookup"><span data-stu-id="9e289-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="9e289-106">Vous pouvez stocker la source du document dans le magasin de symboles et la récupérer par le biais de cette interface.</span><span class="sxs-lookup"><span data-stu-id="9e289-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e289-107">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9e289-107">Methods</span></span>  
  
|<span data-ttu-id="9e289-108">Méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-108">Method</span></span>|<span data-ttu-id="9e289-109">Description</span><span class="sxs-lookup"><span data-stu-id="9e289-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e289-110">FindClosestLine, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-110">FindClosestLine Method</span></span>](isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="9e289-111">Retourne la ligne la plus proche qui est un point de séquence, en fonction d’une ligne dans ce document qui peut être ou non un point de séquence.</span><span class="sxs-lookup"><span data-stu-id="9e289-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="9e289-112">GetCheckSum, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-112">GetCheckSum Method</span></span>](isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="9e289-113">Obtient la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="9e289-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="9e289-114">GetCheckSumAlgorithmId, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-114">GetCheckSumAlgorithmId Method</span></span>](isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="9e289-115">Obtient l’identificateur de l’algorithme de somme de contrôle, ou retourne un GUID de tous les zéros s’il n’y a pas de somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="9e289-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="9e289-116">GetDocumentType, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-116">GetDocumentType Method</span></span>](isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="9e289-117">Obtient le type de document de ce document.</span><span class="sxs-lookup"><span data-stu-id="9e289-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="9e289-118">GetLanguage, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-118">GetLanguage Method</span></span>](isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="9e289-119">Obtient l’identificateur de langue de ce document.</span><span class="sxs-lookup"><span data-stu-id="9e289-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="9e289-120">GetLanguageVendor, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-120">GetLanguageVendor Method</span></span>](isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="9e289-121">Obtient le fournisseur de langage de ce document.</span><span class="sxs-lookup"><span data-stu-id="9e289-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="9e289-122">GetSourceLength, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-122">GetSourceLength Method</span></span>](isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="9e289-123">Obtient la longueur, en octets, de la source incorporée.</span><span class="sxs-lookup"><span data-stu-id="9e289-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="9e289-124">GetSourceRange, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-124">GetSourceRange Method</span></span>](isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="9e289-125">Retourne la plage spécifiée de la source incorporée dans la mémoire tampon donnée.</span><span class="sxs-lookup"><span data-stu-id="9e289-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="9e289-126">GetURL, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-126">GetURL Method</span></span>](isymunmanageddocument-geturl-method.md)|<span data-ttu-id="9e289-127">Retourne l’URL de ce document.</span><span class="sxs-lookup"><span data-stu-id="9e289-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="9e289-128">HasEmbeddedSource, méthode</span><span class="sxs-lookup"><span data-stu-id="9e289-128">HasEmbeddedSource Method</span></span>](isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="9e289-129">Retourne `true` si la source du document est incorporée dans les symboles de débogage ; sinon, retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="9e289-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e289-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e289-130">See also</span></span>

- [<span data-ttu-id="9e289-131">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="9e289-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
