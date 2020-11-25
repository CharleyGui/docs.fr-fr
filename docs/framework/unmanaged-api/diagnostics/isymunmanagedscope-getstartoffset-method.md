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
ms.openlocfilehash: 69b72ce66a203f403fcfe0fd4b4e728ece7397e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725870"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="358cb-102">ISymUnmanagedScope::GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="358cb-102">ISymUnmanagedScope::GetStartOffset Method</span></span>

<span data-ttu-id="358cb-103">Obtient le décalage de début pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="358cb-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="358cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="358cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="358cb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="358cb-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="358cb-106">à Pointeur vers un `ULONG32` qui contient l’offset de départ.</span><span class="sxs-lookup"><span data-stu-id="358cb-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="358cb-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="358cb-107">Return Value</span></span>  

 <span data-ttu-id="358cb-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="358cb-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="358cb-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="358cb-109">Requirements</span></span>  

 <span data-ttu-id="358cb-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="358cb-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358cb-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="358cb-111">See also</span></span>

- [<span data-ttu-id="358cb-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="358cb-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="358cb-113">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="358cb-113">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)
