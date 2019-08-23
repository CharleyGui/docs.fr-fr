---
title: ISymUnmanagedBinder3, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6f514cc070a0a38eb09a5387efc8611100765b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944098"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="aa0fe-102">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="aa0fe-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="aa0fe-103">Étend l’interface de classeur de symboles.</span><span class="sxs-lookup"><span data-stu-id="aa0fe-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="aa0fe-104">Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l' `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="aa0fe-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="aa0fe-105">L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="aa0fe-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa0fe-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="aa0fe-106">Methods</span></span>  
  
|<span data-ttu-id="aa0fe-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="aa0fe-107">Method</span></span>|<span data-ttu-id="aa0fe-108">Description</span><span class="sxs-lookup"><span data-stu-id="aa0fe-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa0fe-109">GetReaderFromCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="aa0fe-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="aa0fe-110">Permet à l’utilisateur d’implémenter ou de fournir via `IID_IDiaReadExeAtRVACallback` le `IID_IDiaReadExeAtOffsetCallback` rappel d’un ou pour obtenir les informations du répertoire de débogage à partir de la mémoire</span><span class="sxs-lookup"><span data-stu-id="aa0fe-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa0fe-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aa0fe-111">Requirements</span></span>  
 <span data-ttu-id="aa0fe-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="aa0fe-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa0fe-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa0fe-113">See also</span></span>

- [<span data-ttu-id="aa0fe-114">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="aa0fe-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="aa0fe-115">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="aa0fe-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="aa0fe-116">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="aa0fe-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
