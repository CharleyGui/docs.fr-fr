---
title: ISymUnmanagedScope::GetNamespaces, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d2c64d7ead2f7ce3d76b40f4fdc604506ee85561
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777889"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="b700b-102">ISymUnmanagedScope::GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="b700b-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="b700b-103">Obtient les espaces de noms qui sont utilisés dans cette étendue.</span><span class="sxs-lookup"><span data-stu-id="b700b-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b700b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b700b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b700b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b700b-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="b700b-106">[in] Taille du tableau `namespaces`.</span><span class="sxs-lookup"><span data-stu-id="b700b-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="b700b-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="b700b-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="b700b-108">[out] Tableau qui reçoit les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="b700b-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b700b-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b700b-109">Return Value</span></span>  
 <span data-ttu-id="b700b-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b700b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b700b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b700b-111">Requirements</span></span>  
 <span data-ttu-id="b700b-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b700b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b700b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b700b-113">See also</span></span>

- [<span data-ttu-id="b700b-114">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="b700b-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
