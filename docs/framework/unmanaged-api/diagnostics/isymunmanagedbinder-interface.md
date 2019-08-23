---
title: ISymUnmanagedBinder, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2160ad4174d9cdfe6e27d2ba7f4748bd473a5f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944229"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="0d9c7-102">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="0d9c7-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="0d9c7-103">Représente un Binder de symboles pour du code non managé.</span><span class="sxs-lookup"><span data-stu-id="0d9c7-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0d9c7-104">L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="0d9c7-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d9c7-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0d9c7-105">Methods</span></span>  
  
|<span data-ttu-id="0d9c7-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="0d9c7-106">Method</span></span>|<span data-ttu-id="0d9c7-107">Description</span><span class="sxs-lookup"><span data-stu-id="0d9c7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d9c7-108">GetReaderForFile, méthode</span><span class="sxs-lookup"><span data-stu-id="0d9c7-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="0d9c7-109">Pour une interface de métadonnées et un nom de fichier donnés, retourne la structure [ISymUnmanagedReader](isymunmanagedreader-interface.md) correcte qui lira les symboles de débogage associés au module.</span><span class="sxs-lookup"><span data-stu-id="0d9c7-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="0d9c7-110">GetReaderFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="0d9c7-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="0d9c7-111">À partir d’une interface de métadonnées et d’un flux de données qui contient le magasin de symboles, retourne la structure [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage du magasin de symboles donné.</span><span class="sxs-lookup"><span data-stu-id="0d9c7-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d9c7-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0d9c7-112">Requirements</span></span>  
 <span data-ttu-id="0d9c7-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0d9c7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d9c7-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d9c7-114">See also</span></span>

- [<span data-ttu-id="0d9c7-115">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="0d9c7-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0d9c7-116">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="0d9c7-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="0d9c7-117">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="0d9c7-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
