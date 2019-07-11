---
title: ISymUnmanagedMethod::GetRootScope, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8956d72d25f240eff653d3eefb92b68431f4e2ae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771771"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="9263f-102">ISymUnmanagedMethod::GetRootScope, méthode</span><span class="sxs-lookup"><span data-stu-id="9263f-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="9263f-103">Obtient la portée lexicale racine au sein de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9263f-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="9263f-104">Cette portée englobe la totalité de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9263f-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9263f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9263f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9263f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9263f-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="9263f-107">[out] Un pointeur qui est défini à retourné [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9263f-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9263f-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9263f-108">Return Value</span></span>  
 <span data-ttu-id="9263f-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="9263f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9263f-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9263f-110">Requirements</span></span>  
 <span data-ttu-id="9263f-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9263f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9263f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9263f-112">See also</span></span>

- [<span data-ttu-id="9263f-113">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="9263f-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
