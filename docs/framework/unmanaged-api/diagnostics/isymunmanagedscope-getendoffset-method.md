---
title: ISymUnmanagedScope::GetEndOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 14e747e81e467019d464212e75513bdf98344916
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678361"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="78816-102">ISymUnmanagedScope::GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="78816-102">ISymUnmanagedScope::GetEndOffset Method</span></span>

<span data-ttu-id="78816-103">Obtient l’offset de fin pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="78816-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78816-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78816-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78816-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78816-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="78816-106">à Pointeur vers un `ULONG32` qui reçoit le décalage de fin.</span><span class="sxs-lookup"><span data-stu-id="78816-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78816-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="78816-107">Return Value</span></span>  

 <span data-ttu-id="78816-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="78816-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78816-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="78816-109">Requirements</span></span>  

 <span data-ttu-id="78816-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="78816-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78816-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78816-111">See also</span></span>

- [<span data-ttu-id="78816-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="78816-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="78816-113">GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="78816-113">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)
