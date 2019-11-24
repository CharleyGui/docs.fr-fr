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
ms.openlocfilehash: f23df98abc5355f0b25d7253b5f2ae808b3446a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449373"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="c9237-102">ISymUnmanagedBinder, interface</span><span class="sxs-lookup"><span data-stu-id="c9237-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="c9237-103">Represents a symbol binder for unmanaged code.</span><span class="sxs-lookup"><span data-stu-id="c9237-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c9237-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span><span class="sxs-lookup"><span data-stu-id="c9237-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9237-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c9237-105">Methods</span></span>  
  
|<span data-ttu-id="c9237-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="c9237-106">Method</span></span>|<span data-ttu-id="c9237-107">Description</span><span class="sxs-lookup"><span data-stu-id="c9237-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9237-108">GetReaderForFile, méthode</span><span class="sxs-lookup"><span data-stu-id="c9237-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="c9237-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span><span class="sxs-lookup"><span data-stu-id="c9237-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="c9237-110">GetReaderFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="c9237-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="c9237-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span><span class="sxs-lookup"><span data-stu-id="c9237-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9237-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="c9237-112">Requirements</span></span>  
 <span data-ttu-id="c9237-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9237-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9237-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9237-114">See also</span></span>

- [<span data-ttu-id="c9237-115">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="c9237-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="c9237-116">ISymUnmanagedBinder2, interface</span><span class="sxs-lookup"><span data-stu-id="c9237-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="c9237-117">ISymUnmanagedBinder3, interface</span><span class="sxs-lookup"><span data-stu-id="c9237-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
