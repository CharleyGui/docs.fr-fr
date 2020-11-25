---
title: ISymUnmanagedWriter::OpenMethod, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
ms.openlocfilehash: deb3a28ffb73754b4c03496a6a72325418f1a4fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722906"
---
# <a name="isymunmanagedwriteropenmethod-method"></a><span data-ttu-id="f463a-102">ISymUnmanagedWriter::OpenMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="f463a-102">ISymUnmanagedWriter::OpenMethod Method</span></span>

<span data-ttu-id="f463a-103">Ouvre une méthode dans laquelle les informations de symboles sont émises.</span><span class="sxs-lookup"><span data-stu-id="f463a-103">Opens a method into which symbol information is emitted.</span></span> <span data-ttu-id="f463a-104">La méthode donnée devient la méthode actuelle pour les appels pour définir des points de séquence, des paramètres et des étendues lexicales.</span><span class="sxs-lookup"><span data-stu-id="f463a-104">The given method becomes the current method for calls to define sequence points, parameters, and lexical scopes.</span></span> <span data-ttu-id="f463a-105">Il existe une portée lexicale implicite autour de la totalité de la méthode.</span><span class="sxs-lookup"><span data-stu-id="f463a-105">There is an implicit lexical scope around the entire method.</span></span> <span data-ttu-id="f463a-106">La réouverture d’une méthode précédemment fermée efface tous les symboles définis précédemment pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="f463a-106">Reopening a method that was previously closed erases any previously defined symbols for that method.</span></span> <span data-ttu-id="f463a-107">Il ne peut y avoir qu’une seule méthode ouverte à la fois.</span><span class="sxs-lookup"><span data-stu-id="f463a-107">There can be only one open method at a time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f463a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f463a-108">Syntax</span></span>  
  
```cpp  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f463a-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f463a-109">Parameters</span></span>  

 `method`  
 <span data-ttu-id="f463a-110">dans Jeton de métadonnées de la méthode à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="f463a-110">[in] The metadata token for the method to be opened.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f463a-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f463a-111">Return Value</span></span>  

 <span data-ttu-id="f463a-112">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f463a-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f463a-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f463a-113">Requirements</span></span>  

 <span data-ttu-id="f463a-114">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f463a-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f463a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f463a-115">See also</span></span>

- [<span data-ttu-id="f463a-116">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="f463a-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="f463a-117">CloseMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="f463a-117">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)
- [<span data-ttu-id="f463a-118">OpenMethod2, méthode</span><span class="sxs-lookup"><span data-stu-id="f463a-118">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)
