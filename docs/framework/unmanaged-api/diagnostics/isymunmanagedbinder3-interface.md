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
ms.openlocfilehash: e4a415b21e3980e7603319d7acbb3831462fac9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449297"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="a5091-102">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="a5091-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="a5091-103">Étend l’interface de classeur de symboles.</span><span class="sxs-lookup"><span data-stu-id="a5091-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="a5091-104">Obtenez cette interface en appelant `QueryInterface` sur un objet qui implémente l’interface `ISymUnmanagedBinder`.</span><span class="sxs-lookup"><span data-stu-id="a5091-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a5091-105">L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="a5091-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5091-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a5091-106">Methods</span></span>  
  
|<span data-ttu-id="a5091-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="a5091-107">Method</span></span>|<span data-ttu-id="a5091-108">Description</span><span class="sxs-lookup"><span data-stu-id="a5091-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5091-109">GetReaderFromCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="a5091-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="a5091-110">Permet à l’utilisateur d’implémenter ou de fournir par le biais du rappel un `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` pour obtenir les informations du répertoire de débogage à partir de la mémoire</span><span class="sxs-lookup"><span data-stu-id="a5091-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5091-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a5091-111">Requirements</span></span>  
 <span data-ttu-id="a5091-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a5091-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5091-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5091-113">See also</span></span>

- [<span data-ttu-id="a5091-114">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="a5091-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="a5091-115">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="a5091-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="a5091-116">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="a5091-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
