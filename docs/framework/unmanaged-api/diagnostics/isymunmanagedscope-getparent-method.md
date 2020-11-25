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
ms.openlocfilehash: db7fb5f2c1b5d1fa8be1328852ca4402538396f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725896"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="86729-102">ISymUnmanagedScope::GetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="86729-102">ISymUnmanagedScope::GetParent Method</span></span>

<span data-ttu-id="86729-103">Obtient la portée parente de cette portée.</span><span class="sxs-lookup"><span data-stu-id="86729-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86729-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86729-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86729-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="86729-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="86729-106">à Pointeur vers l’interface [ISymUnmanagedScope](isymunmanagedscope-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="86729-106">[out] A pointer to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86729-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="86729-107">Return Value</span></span>  

 <span data-ttu-id="86729-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="86729-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86729-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="86729-109">Requirements</span></span>  

 <span data-ttu-id="86729-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="86729-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86729-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86729-111">See also</span></span>

- [<span data-ttu-id="86729-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="86729-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="86729-113">GetChildren, méthode</span><span class="sxs-lookup"><span data-stu-id="86729-113">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)
