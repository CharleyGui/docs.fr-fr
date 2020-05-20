---
title: ISymUnmanagedScope::GetParent, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
ms.openlocfilehash: 95ae081d61200e4fd020609a4d23783f265d2cc6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615356"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="769df-102">ISymUnmanagedScope::GetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="769df-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="769df-103">Obtient la portée parente de cette portée.</span><span class="sxs-lookup"><span data-stu-id="769df-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="769df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="769df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="769df-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="769df-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="769df-106">à Pointeur vers l’interface [ISymUnmanagedScope](isymunmanagedscope-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="769df-106">[out] A pointer to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="769df-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="769df-107">Return Value</span></span>  
 <span data-ttu-id="769df-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="769df-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="769df-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="769df-109">Requirements</span></span>  
 <span data-ttu-id="769df-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="769df-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769df-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="769df-111">See also</span></span>

- [<span data-ttu-id="769df-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="769df-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="769df-113">GetChildren, méthode</span><span class="sxs-lookup"><span data-stu-id="769df-113">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)
