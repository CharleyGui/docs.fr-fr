---
title: ISymUnmanagedScope::GetMethod, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
ms.openlocfilehash: 75d5638a6f01ba9569a03e5255a7217371c9d177
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725935"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="5d75a-102">ISymUnmanagedScope::GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="5d75a-102">ISymUnmanagedScope::GetMethod Method</span></span>

<span data-ttu-id="5d75a-103">Obtient la méthode qui contient cette portée.</span><span class="sxs-lookup"><span data-stu-id="5d75a-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d75a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d75a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d75a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5d75a-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="5d75a-106">à Pointeur vers l’interface [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="5d75a-106">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d75a-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5d75a-107">Return Value</span></span>  

 <span data-ttu-id="5d75a-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5d75a-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d75a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5d75a-109">Requirements</span></span>  

 <span data-ttu-id="5d75a-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5d75a-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d75a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d75a-111">See also</span></span>

- [<span data-ttu-id="5d75a-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="5d75a-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
