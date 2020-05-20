---
title: ISymUnmanagedScope::GetStartOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
ms.openlocfilehash: 071ad6c24804eecb0f2260d54c854f22ff997bc1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611014"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="5aaae-102">ISymUnmanagedScope::GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="5aaae-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="5aaae-103">Obtient le décalage de début pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="5aaae-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aaae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5aaae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aaae-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5aaae-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5aaae-106">à Pointeur vers un `ULONG32` qui contient l’offset de départ.</span><span class="sxs-lookup"><span data-stu-id="5aaae-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5aaae-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5aaae-107">Return Value</span></span>  
 <span data-ttu-id="5aaae-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5aaae-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aaae-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="5aaae-109">Requirements</span></span>  
 <span data-ttu-id="5aaae-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5aaae-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aaae-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5aaae-111">See also</span></span>

- [<span data-ttu-id="5aaae-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="5aaae-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="5aaae-113">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="5aaae-113">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)
