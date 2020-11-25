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
ms.openlocfilehash: 554e59484f00626726f7f024c69e93a5e6647130
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727378"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="54ab5-102">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="54ab5-102">ISymUnmanagedBinder Interface</span></span>

<span data-ttu-id="54ab5-103">Représente un binder de symboles pour du code non managé.</span><span class="sxs-lookup"><span data-stu-id="54ab5-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="54ab5-104">L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="54ab5-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54ab5-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="54ab5-105">Methods</span></span>  
  
|<span data-ttu-id="54ab5-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="54ab5-106">Method</span></span>|<span data-ttu-id="54ab5-107">Description</span><span class="sxs-lookup"><span data-stu-id="54ab5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54ab5-108">GetReaderForFile, méthode</span><span class="sxs-lookup"><span data-stu-id="54ab5-108">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="54ab5-109">Pour une interface de métadonnées et un nom de fichier donnés, retourne la structure [ISymUnmanagedReader](isymunmanagedreader-interface.md) correcte qui lira les symboles de débogage associés au module.</span><span class="sxs-lookup"><span data-stu-id="54ab5-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="54ab5-110">GetReaderFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="54ab5-110">GetReaderFromStream Method</span></span>](isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="54ab5-111">À partir d’une interface de métadonnées et d’un flux de données qui contient le magasin de symboles, retourne la structure [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage du magasin de symboles donné.</span><span class="sxs-lookup"><span data-stu-id="54ab5-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="54ab5-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="54ab5-112">Requirements</span></span>  

 <span data-ttu-id="54ab5-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="54ab5-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54ab5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54ab5-114">See also</span></span>

- [<span data-ttu-id="54ab5-115">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="54ab5-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="54ab5-116">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="54ab5-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="54ab5-117">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="54ab5-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
