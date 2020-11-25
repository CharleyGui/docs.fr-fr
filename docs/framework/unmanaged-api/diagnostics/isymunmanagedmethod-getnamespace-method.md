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
ms.openlocfilehash: 7e26c272ee1ecf03f7d2a347cf7ca2cc3efa2122
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699558"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="1ca2b-102">ISymUnmanagedMethod::GetNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="1ca2b-102">ISymUnmanagedMethod::GetNamespace Method</span></span>

<span data-ttu-id="1ca2b-103">Obtient l’espace de noms dans lequel cette méthode est définie.</span><span class="sxs-lookup"><span data-stu-id="1ca2b-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ca2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ca2b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ca2b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1ca2b-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="1ca2b-106">à Pointeur défini sur l’interface [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="1ca2b-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ca2b-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1ca2b-107">Return Value</span></span>  

 <span data-ttu-id="1ca2b-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1ca2b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ca2b-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1ca2b-109">Requirements</span></span>  

 <span data-ttu-id="1ca2b-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1ca2b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca2b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ca2b-111">See also</span></span>

- [<span data-ttu-id="1ca2b-112">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="1ca2b-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
