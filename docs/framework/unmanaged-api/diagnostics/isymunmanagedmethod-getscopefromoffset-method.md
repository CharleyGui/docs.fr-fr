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
ms.openlocfilehash: 4eefd019280f501a6ce194e5ce84388e32cc66e1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615135"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="3f4ee-102">ISymUnmanagedMethod::GetScopeFromOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="3f4ee-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="3f4ee-103">Obtient la portée lexicale la plus englobante dans cette méthode qui englobe l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="3f4ee-104">Cela peut être utilisé pour démarrer des recherches de variables locales.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f4ee-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f4ee-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f4ee-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f4ee-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="3f4ee-107">dans `ULONG`Qui contient l’offset.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="3f4ee-108">à Pointeur qui a pour valeur l’interface [ISymUnmanagedScope](isymunmanagedscope-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f4ee-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3f4ee-109">Return Value</span></span>  
 <span data-ttu-id="3f4ee-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3f4ee-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f4ee-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="3f4ee-111">Requirements</span></span>  
 <span data-ttu-id="3f4ee-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3f4ee-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f4ee-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f4ee-113">See also</span></span>

- [<span data-ttu-id="3f4ee-114">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="3f4ee-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
