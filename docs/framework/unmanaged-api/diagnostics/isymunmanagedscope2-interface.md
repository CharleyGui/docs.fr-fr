---
title: ISymUnmanagedScope2, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2
helpviewer_keywords:
- ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type:
- apiref
ms.openlocfilehash: 3374097c8d343fed6badf046742ca556d2a92f3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446228"
---
# <a name="isymunmanagedscope2-interface"></a><span data-ttu-id="06a44-102">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="06a44-102">ISymUnmanagedScope2 Interface</span></span>
<span data-ttu-id="06a44-103">Représente une portée lexicale dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="06a44-103">Represents a lexical scope within a method.</span></span> <span data-ttu-id="06a44-104">Cette interface étend l’interface [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) avec des méthodes qui obtiennent des informations sur les constantes définies dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="06a44-104">This interface extends the [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface with methods that get information about constants defined within the scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06a44-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="06a44-105">Methods</span></span>  
  
|<span data-ttu-id="06a44-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="06a44-106">Method</span></span>|<span data-ttu-id="06a44-107">Description</span><span class="sxs-lookup"><span data-stu-id="06a44-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06a44-108">GetConstantCount, méthode</span><span class="sxs-lookup"><span data-stu-id="06a44-108">GetConstantCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|<span data-ttu-id="06a44-109">Obtient le nombre des constantes définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="06a44-109">Gets a count of the constants defined within this scope.</span></span>|  
|[<span data-ttu-id="06a44-110">GetConstants, méthode</span><span class="sxs-lookup"><span data-stu-id="06a44-110">GetConstants Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|<span data-ttu-id="06a44-111">Obtient les constantes locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="06a44-111">Gets the local constants defined within this scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06a44-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="06a44-112">Requirements</span></span>  
 <span data-ttu-id="06a44-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="06a44-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a44-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06a44-114">See also</span></span>

- [<span data-ttu-id="06a44-115">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="06a44-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="06a44-116">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="06a44-116">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
