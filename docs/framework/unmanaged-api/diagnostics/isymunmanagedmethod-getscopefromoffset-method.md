---
title: ISymUnmanagedMethod::GetScopeFromOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: cf2784ce0ac6e614e75a341660808b9fe03ada0e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699441"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="2e501-102">ISymUnmanagedMethod::GetScopeFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="2e501-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>

<span data-ttu-id="2e501-103">Obtient la portée lexicale la plus englobante dans cette méthode qui englobe l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="2e501-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="2e501-104">Cela peut être utilisé pour démarrer des recherches de variables locales.</span><span class="sxs-lookup"><span data-stu-id="2e501-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e501-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e501-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e501-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2e501-106">Parameters</span></span>  

 `offset`  
 <span data-ttu-id="2e501-107">dans `ULONG` Qui contient l’offset.</span><span class="sxs-lookup"><span data-stu-id="2e501-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2e501-108">à Pointeur qui a pour valeur l’interface [ISymUnmanagedScope](isymunmanagedscope-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="2e501-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e501-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2e501-109">Return Value</span></span>  

 <span data-ttu-id="2e501-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2e501-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e501-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2e501-111">Requirements</span></span>  

 <span data-ttu-id="2e501-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2e501-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e501-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e501-113">See also</span></span>

- [<span data-ttu-id="2e501-114">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="2e501-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
