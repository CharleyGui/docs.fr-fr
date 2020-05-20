---
title: ISymUnmanagedReader, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
ms.openlocfilehash: b372021fcda39d9973d96a9c39e93e38617887a6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615460"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="94569-102">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="94569-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="94569-103">Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables dans un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="94569-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94569-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="94569-104">Methods</span></span>  
  
|<span data-ttu-id="94569-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="94569-105">Method</span></span>|<span data-ttu-id="94569-106">Description</span><span class="sxs-lookup"><span data-stu-id="94569-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94569-107">GetDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-107">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="94569-108">Recherche un document.</span><span class="sxs-lookup"><span data-stu-id="94569-108">Finds a document.</span></span>|  
|[<span data-ttu-id="94569-109">GetDocuments, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-109">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="94569-110">Retourne un tableau de tous les documents définis dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="94569-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="94569-111">GetDocumentVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-111">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="94569-112">Obtient la version spécifiée du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="94569-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="94569-113">GetGlobalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-113">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="94569-114">Retourne toutes les variables globales.</span><span class="sxs-lookup"><span data-stu-id="94569-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="94569-115">GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-115">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="94569-116">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="94569-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="94569-117">GetMethodByVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-117">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="94569-118">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version de modification et de copie.</span><span class="sxs-lookup"><span data-stu-id="94569-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="94569-119">GetMethodFromDocumentPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-119">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="94569-120">Retourne la méthode qui contient le point d’arrêt à la position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="94569-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="94569-121">GetMethodsFromDocumentPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-121">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="94569-122">Retourne un tableau de méthodes, chacune contenant le point d’arrêt à la position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="94569-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="94569-123">GetMethodVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-123">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="94569-124">Obtient la version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="94569-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="94569-125">GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-125">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="94569-126">Obtient les espaces de noms définis au niveau de la portée globale dans ce magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="94569-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="94569-127">GetSymAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-127">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="94569-128">Obtient un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="94569-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="94569-129">GetSymbolStoreFileName, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-129">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="94569-130">Fournit le nom de fichier sur disque du magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="94569-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="94569-131">GetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-131">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="94569-132">Retourne la méthode spécifiée en tant que point d’entrée utilisateur pour le module, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="94569-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="94569-133">GetVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-133">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="94569-134">Retourne une variable non locale, en fonction de son parent et de son nom.</span><span class="sxs-lookup"><span data-stu-id="94569-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="94569-135">Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-135">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="94569-136">Initialise le lecteur de symboles avec l’interface de l’importateur de métadonnées à laquelle ce lecteur sera associé, ainsi que le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="94569-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="94569-137">ReplaceSymbolStore, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-137">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="94569-138">Remplace le magasin de symboles existant par un magasin de symboles delta.</span><span class="sxs-lookup"><span data-stu-id="94569-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="94569-139">UpdateSymbolStore, méthode</span><span class="sxs-lookup"><span data-stu-id="94569-139">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="94569-140">Met à jour le magasin de symboles existant avec un magasin de symboles delta.</span><span class="sxs-lookup"><span data-stu-id="94569-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94569-141">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="94569-141">Requirements</span></span>  
 <span data-ttu-id="94569-142">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="94569-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94569-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94569-143">See also</span></span>

- [<span data-ttu-id="94569-144">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="94569-144">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="94569-145">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="94569-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
