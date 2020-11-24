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
ms.openlocfilehash: bca84fdba575ed9bfe572b9fd7a5869620962de6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675865"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="2f15a-102">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="2f15a-102">ISymUnmanagedReader Interface</span></span>

<span data-ttu-id="2f15a-103">Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables d’un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="2f15a-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f15a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="2f15a-104">Methods</span></span>  
  
|<span data-ttu-id="2f15a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-105">Method</span></span>|<span data-ttu-id="2f15a-106">Description</span><span class="sxs-lookup"><span data-stu-id="2f15a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f15a-107">GetDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-107">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="2f15a-108">Recherche un document.</span><span class="sxs-lookup"><span data-stu-id="2f15a-108">Finds a document.</span></span>|  
|[<span data-ttu-id="2f15a-109">GetDocuments, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-109">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="2f15a-110">Retourne un tableau de tous les documents définis dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="2f15a-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="2f15a-111">GetDocumentVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-111">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="2f15a-112">Obtient la version spécifiée du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="2f15a-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="2f15a-113">GetGlobalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-113">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="2f15a-114">Retourne toutes les variables globales.</span><span class="sxs-lookup"><span data-stu-id="2f15a-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="2f15a-115">GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-115">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="2f15a-116">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode.</span><span class="sxs-lookup"><span data-stu-id="2f15a-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="2f15a-117">GetMethodByVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-117">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="2f15a-118">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version de modification et de copie.</span><span class="sxs-lookup"><span data-stu-id="2f15a-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="2f15a-119">GetMethodFromDocumentPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-119">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="2f15a-120">Retourne la méthode qui contient le point d’arrêt à la position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="2f15a-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="2f15a-121">GetMethodsFromDocumentPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-121">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="2f15a-122">Retourne un tableau de méthodes, chacune contenant le point d’arrêt à la position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="2f15a-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="2f15a-123">GetMethodVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-123">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="2f15a-124">Obtient la version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="2f15a-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="2f15a-125">GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-125">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="2f15a-126">Obtient les espaces de noms définis au niveau de la portée globale dans ce magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="2f15a-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="2f15a-127">GetSymAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-127">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="2f15a-128">Obtient un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="2f15a-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="2f15a-129">GetSymbolStoreFileName, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-129">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="2f15a-130">Fournit le nom de fichier sur disque du magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="2f15a-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="2f15a-131">GetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-131">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="2f15a-132">Retourne la méthode spécifiée en tant que point d’entrée utilisateur pour le module, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="2f15a-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="2f15a-133">GetVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-133">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="2f15a-134">Retourne une variable non locale, en fonction de son parent et de son nom.</span><span class="sxs-lookup"><span data-stu-id="2f15a-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="2f15a-135">Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-135">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="2f15a-136">Initialise le lecteur de symboles avec l’interface de l’importateur de métadonnées à laquelle ce lecteur sera associé, ainsi que le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="2f15a-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="2f15a-137">ReplaceSymbolStore, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-137">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="2f15a-138">Remplace le magasin de symboles existant par un magasin de symboles delta.</span><span class="sxs-lookup"><span data-stu-id="2f15a-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="2f15a-139">UpdateSymbolStore, méthode</span><span class="sxs-lookup"><span data-stu-id="2f15a-139">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="2f15a-140">Met à jour le magasin de symboles existant avec un magasin de symboles delta.</span><span class="sxs-lookup"><span data-stu-id="2f15a-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f15a-141">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2f15a-141">Requirements</span></span>  

 <span data-ttu-id="2f15a-142">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2f15a-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f15a-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f15a-143">See also</span></span>

- [<span data-ttu-id="2f15a-144">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="2f15a-144">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="2f15a-145">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="2f15a-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
