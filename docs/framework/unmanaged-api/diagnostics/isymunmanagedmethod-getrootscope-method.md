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
ms.openlocfilehash: 650a64e72b410cddfbee7dce676ddbb5a3b8b3d3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614446"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="7eaf0-102">ISymUnmanagedMethod::GetRootScope, méthode</span><span class="sxs-lookup"><span data-stu-id="7eaf0-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="7eaf0-103">Obtient la portée lexicale racine dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="7eaf0-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="7eaf0-104">Cette portée englobe la totalité de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7eaf0-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eaf0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eaf0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7eaf0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7eaf0-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7eaf0-107">à Pointeur qui a pour valeur l’interface [ISymUnmanagedScope](isymunmanagedscope-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="7eaf0-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7eaf0-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7eaf0-108">Return Value</span></span>  
 <span data-ttu-id="7eaf0-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7eaf0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eaf0-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="7eaf0-110">Requirements</span></span>  
 <span data-ttu-id="7eaf0-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7eaf0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eaf0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7eaf0-112">See also</span></span>

- [<span data-ttu-id="7eaf0-113">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="7eaf0-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
