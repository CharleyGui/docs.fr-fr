---
title: ISymUnmanagedMethod::GetNamespace, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 676c968bb48e493f9a4514235fbc3246cf395228
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774652"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="eab4a-102">ISymUnmanagedMethod::GetNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="eab4a-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="eab4a-103">Obtient l’espace de noms dans lequel cette méthode est définie.</span><span class="sxs-lookup"><span data-stu-id="eab4a-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eab4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eab4a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eab4a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eab4a-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="eab4a-106">[out] Un pointeur qui est défini à retourné [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="eab4a-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eab4a-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="eab4a-107">Return Value</span></span>  
 <span data-ttu-id="eab4a-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="eab4a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eab4a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eab4a-109">Requirements</span></span>  
 <span data-ttu-id="eab4a-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eab4a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab4a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eab4a-111">See also</span></span>

- [<span data-ttu-id="eab4a-112">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="eab4a-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
