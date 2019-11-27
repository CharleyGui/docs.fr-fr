---
title: ISymUnmanagedWriter2, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2
helpviewer_keywords:
- ISymUnmanagedWriter2 interface [.NET Framework debugging]
ms.assetid: 8e78faa4-cf43-44fb-a91d-94d6df692a25
topic_type:
- apiref
ms.openlocfilehash: c7f0235aa7096a790a0fd956081e330c8fdad9fe
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438258"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="d5c36-102">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="d5c36-102">ISymUnmanagedWriter2 Interface</span></span>
<span data-ttu-id="d5c36-103">Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables.</span><span class="sxs-lookup"><span data-stu-id="d5c36-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="d5c36-104">Cette interface étend l’interface [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d5c36-104">This interface extends the [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d5c36-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d5c36-105">Methods</span></span>  
  
|<span data-ttu-id="d5c36-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="d5c36-106">Method</span></span>|<span data-ttu-id="d5c36-107">Description</span><span class="sxs-lookup"><span data-stu-id="d5c36-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d5c36-108">DefineConstant2, méthode</span><span class="sxs-lookup"><span data-stu-id="d5c36-108">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="d5c36-109">Définit un nom pour une valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="d5c36-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="d5c36-110">DefineGlobalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="d5c36-110">DefineGlobalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="d5c36-111">Définit une variable globale unique.</span><span class="sxs-lookup"><span data-stu-id="d5c36-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="d5c36-112">DefineLocalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="d5c36-112">DefineLocalVariable2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="d5c36-113">Définit une variable unique dans la portée lexicale actuelle.</span><span class="sxs-lookup"><span data-stu-id="d5c36-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5c36-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d5c36-114">Requirements</span></span>  
 <span data-ttu-id="d5c36-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d5c36-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c36-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5c36-116">See also</span></span>

- [<span data-ttu-id="d5c36-117">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="d5c36-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d5c36-118">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="d5c36-118">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="d5c36-119">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="d5c36-119">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
