---
title: ISymUnmanagedBinder2, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: c5a43f6c277f582f9f14cefe5bfba6f5300c09d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727352"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="87307-102">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="87307-102">ISymUnmanagedBinder2 Interface</span></span>

<span data-ttu-id="87307-103">Représente un Binder de symboles pour du code non managé et étend l’interface [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="87307-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="87307-104">L’ouverture d’un fichier de base de données du programme (PDB) à partir d’une source non fiable constitue un risque pour la sécurité.</span><span class="sxs-lookup"><span data-stu-id="87307-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87307-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="87307-105">Methods</span></span>  
  
|<span data-ttu-id="87307-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="87307-106">Method</span></span>|<span data-ttu-id="87307-107">Description</span><span class="sxs-lookup"><span data-stu-id="87307-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87307-108">GetReaderForFile2, méthode</span><span class="sxs-lookup"><span data-stu-id="87307-108">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="87307-109">À partir d’une interface de métadonnées et d’un nom de fichier, retourne l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) appropriée qui lira les symboles de débogage associés au module.</span><span class="sxs-lookup"><span data-stu-id="87307-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="87307-110">Fournit une recherche plus complète que la méthode [ISymUnmanagedBinder :: GetReaderForFile,](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="87307-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87307-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="87307-111">Requirements</span></span>  

 <span data-ttu-id="87307-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="87307-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87307-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87307-113">See also</span></span>

- [<span data-ttu-id="87307-114">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="87307-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="87307-115">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="87307-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="87307-116">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="87307-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
