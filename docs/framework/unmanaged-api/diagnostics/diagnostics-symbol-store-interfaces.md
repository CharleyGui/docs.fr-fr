---
title: Interfaces du magasin de symboles de diagnostics
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 34eee8c05e1c356d4c431245c6837bd2b3a89b32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504470"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="17d49-102">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="17d49-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="17d49-103">Cette rubrique décrit les interfaces non managées qui permettent à un compilateur de générer des informations de symbole pour une utilisation par un débogueur.</span><span class="sxs-lookup"><span data-stu-id="17d49-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17d49-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="17d49-104">In This Section</span></span>  
 [<span data-ttu-id="17d49-105">IBindingDisplay, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-105">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="17d49-106">Fournit des méthodes qui affichent les informations de liaison actuelles sur l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="17d49-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="17d49-107">IDebugAutoAttach, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-107">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="17d49-108">Définit l’interface pour un attachement automatique du débogueur appelé par le serveur.</span><span class="sxs-lookup"><span data-stu-id="17d49-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="17d49-109">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-109">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="17d49-110">Déclare des méthodes pour l’inscription et l’annulation de l’inscription d’une source de notification de connexion.</span><span class="sxs-lookup"><span data-stu-id="17d49-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="17d49-111">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-111">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="17d49-112">Déclare des méthodes pour la notification du récepteur.</span><span class="sxs-lookup"><span data-stu-id="17d49-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="17d49-113">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="17d49-114">Déclare une méthode pour définir des filtres de notification.</span><span class="sxs-lookup"><span data-stu-id="17d49-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="17d49-115">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="17d49-116">Fournit des informations pour la fonctionnalité modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="17d49-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="17d49-117">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-117">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="17d49-118">Cette interface est le complément de lecture de l' [interface ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="17d49-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="17d49-119">ISymUnmanagedAsyncMethodPropertiesWriter, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="17d49-120">Autorise la définition d’informations de méthode Async facultatives par symbole de méthode.</span><span class="sxs-lookup"><span data-stu-id="17d49-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="17d49-121">Doit utiliser avec une méthode ouverte (c’est-à-dire entre les appels à la [méthode OpenMethod,](isymunmanagedwriter-openmethod-method.md)et la [méthode CloseMethod,](isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="17d49-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="17d49-122">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-122">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="17d49-123">Représente un Binder de symboles pour du code non managé.</span><span class="sxs-lookup"><span data-stu-id="17d49-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="17d49-124">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-124">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="17d49-125">Représente un Binder de symboles pour du code non managé et étend l' `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="17d49-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="17d49-126">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-126">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="17d49-127">Représente un Binder de symboles pour du code non managé et étend l' `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="17d49-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="17d49-128">ISymUnmanagedConstant, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-128">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="17d49-129">Fournit l’accès aux constantes non managées.</span><span class="sxs-lookup"><span data-stu-id="17d49-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="17d49-130">ISymUnmanagedDispose, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-130">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="17d49-131">Supprime les ressources non managées.</span><span class="sxs-lookup"><span data-stu-id="17d49-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="17d49-132">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-132">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="17d49-133">Représente un document référencé par un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="17d49-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="17d49-134">ISymUnmanagedDocumentWriter, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-134">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="17d49-135">Fournit des méthodes d'écriture dans un document référencé par un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="17d49-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="17d49-136">ISymUnmanagedENCUpdate, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-136">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="17d49-137">Fournit des méthodes pour la fonctionnalité modifier et continuer.</span><span class="sxs-lookup"><span data-stu-id="17d49-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="17d49-138">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-138">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="17d49-139">Représente une méthode dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="17d49-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="17d49-140">ISymUnmanagedNamespace, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-140">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="17d49-141">Représente un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="17d49-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="17d49-142">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-142">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="17d49-143">Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables dans un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="17d49-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="17d49-144">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-144">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="17d49-145">Obtient une méthode de lecteur de symboles en fonction d’un jeton de méthode et d’un numéro de version de modification et de copie.</span><span class="sxs-lookup"><span data-stu-id="17d49-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="17d49-146">ISymUnmanagedReaderSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="17d49-147">Fournit des méthodes qui obtiennent des informations de recherche de symboles.</span><span class="sxs-lookup"><span data-stu-id="17d49-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="17d49-148">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-148">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="17d49-149">Représente une portée lexicale dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="17d49-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="17d49-150">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-150">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="17d49-151">Représente une portée lexicale dans une méthode et étend l' `ISymUnmanagedScope` interface avec des méthodes qui obtiennent des informations sur les constantes définies dans la portée.</span><span class="sxs-lookup"><span data-stu-id="17d49-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="17d49-152">ISymUnmanagedSourceServerModule, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-152">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="17d49-153">Fournit les données du serveur source pour un module.</span><span class="sxs-lookup"><span data-stu-id="17d49-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="17d49-154">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="17d49-155">Fournit des méthodes qui obtiennent des informations sur le chemin de recherche.</span><span class="sxs-lookup"><span data-stu-id="17d49-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="17d49-156">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-156">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="17d49-157">Représente une variable, telle qu’un paramètre, une variable locale ou un champ.</span><span class="sxs-lookup"><span data-stu-id="17d49-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="17d49-158">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-158">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="17d49-159">Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables.</span><span class="sxs-lookup"><span data-stu-id="17d49-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="17d49-160">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="17d49-161">Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables.</span><span class="sxs-lookup"><span data-stu-id="17d49-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="17d49-162">Étend l' `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="17d49-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="17d49-163">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-163">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="17d49-164">Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables.</span><span class="sxs-lookup"><span data-stu-id="17d49-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="17d49-165">Étend l' `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="17d49-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="17d49-166">ISymUnmanagedWriter4, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-166">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="17d49-167">Interface Isymunmanagedwriter4,.</span><span class="sxs-lookup"><span data-stu-id="17d49-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="17d49-168">ISymUnmanagedWriter5, interface</span><span class="sxs-lookup"><span data-stu-id="17d49-168">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="17d49-169">Interface ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="17d49-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="17d49-170">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="17d49-170">Related Sections</span></span>  
 [<span data-ttu-id="17d49-171">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="17d49-171">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="17d49-172">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="17d49-172">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="17d49-173">Débogage</span><span class="sxs-lookup"><span data-stu-id="17d49-173">Debugging</span></span>](../debugging/index.md)
