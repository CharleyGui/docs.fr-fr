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
ms.openlocfilehash: 0cb0b91f2dca8203c37599400b3b61f84eb7d282
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727313"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="7048a-102">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="7048a-102">ISymUnmanagedBinder3 Interface</span></span>

<span data-ttu-id="7048a-103">Étend l’interface de classeur de symboles.</span><span class="sxs-lookup"><span data-stu-id="7048a-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="7048a-104">Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l' `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="7048a-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7048a-105">L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="7048a-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7048a-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7048a-106">Methods</span></span>  
  
|<span data-ttu-id="7048a-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="7048a-107">Method</span></span>|<span data-ttu-id="7048a-108">Description</span><span class="sxs-lookup"><span data-stu-id="7048a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7048a-109">GetReaderFromCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="7048a-109">GetReaderFromCallback Method</span></span>](isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="7048a-110">Permet à l’utilisateur d’implémenter ou de fournir via le rappel d’un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations du répertoire de débogage à partir de la mémoire</span><span class="sxs-lookup"><span data-stu-id="7048a-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7048a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7048a-111">Requirements</span></span>  

 <span data-ttu-id="7048a-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7048a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7048a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7048a-113">See also</span></span>

- [<span data-ttu-id="7048a-114">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="7048a-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7048a-115">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="7048a-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="7048a-116">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="7048a-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
