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
ms.openlocfilehash: 6feb48b7c78dda64ba372e470b83ffb14f21f2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683327"
---
# <a name="isymunmanagedwriter2-interface"></a><span data-ttu-id="9b00a-102">ISymUnmanagedWriter2, interface</span><span class="sxs-lookup"><span data-stu-id="9b00a-102">ISymUnmanagedWriter2 Interface</span></span>

<span data-ttu-id="9b00a-103">Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables.</span><span class="sxs-lookup"><span data-stu-id="9b00a-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="9b00a-104">Cette interface étend l’interface [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9b00a-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b00a-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9b00a-105">Methods</span></span>  
  
|<span data-ttu-id="9b00a-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="9b00a-106">Method</span></span>|<span data-ttu-id="9b00a-107">Description</span><span class="sxs-lookup"><span data-stu-id="9b00a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b00a-108">DefineConstant2, méthode</span><span class="sxs-lookup"><span data-stu-id="9b00a-108">DefineConstant2 Method</span></span>](isymunmanagedwriter2-defineconstant2-method.md)|<span data-ttu-id="9b00a-109">Définit un nom pour une valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="9b00a-109">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="9b00a-110">DefineGlobalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="9b00a-110">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)|<span data-ttu-id="9b00a-111">Définit une variable globale unique.</span><span class="sxs-lookup"><span data-stu-id="9b00a-111">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="9b00a-112">DefineLocalVariable2, méthode</span><span class="sxs-lookup"><span data-stu-id="9b00a-112">DefineLocalVariable2 Method</span></span>](isymunmanagedwriter2-definelocalvariable2-method.md)|<span data-ttu-id="9b00a-113">Définit une variable unique dans la portée lexicale actuelle.</span><span class="sxs-lookup"><span data-stu-id="9b00a-113">Defines a single variable in the current lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b00a-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9b00a-114">Requirements</span></span>  

 <span data-ttu-id="9b00a-115">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9b00a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b00a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b00a-116">See also</span></span>

- [<span data-ttu-id="9b00a-117">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="9b00a-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="9b00a-118">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="9b00a-118">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="9b00a-119">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="9b00a-119">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
