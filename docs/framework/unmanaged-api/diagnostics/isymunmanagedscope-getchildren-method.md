---
title: ISymUnmanagedScope::GetChildren, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: 8f3c83a7a89553ba600f3e0e368eec0ddd0350e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727606"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="6481d-102">ISymUnmanagedScope::GetChildren, méthode</span><span class="sxs-lookup"><span data-stu-id="6481d-102">ISymUnmanagedScope::GetChildren Method</span></span>

<span data-ttu-id="6481d-103">Obtient les enfants de cette portée.</span><span class="sxs-lookup"><span data-stu-id="6481d-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6481d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6481d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6481d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6481d-105">Parameters</span></span>  

 `cChildren`  
 <span data-ttu-id="6481d-106">dans `ULONG32` Qui indique la taille du `children` tableau.</span><span class="sxs-lookup"><span data-stu-id="6481d-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="6481d-107">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les enfants.</span><span class="sxs-lookup"><span data-stu-id="6481d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="6481d-108">à Tableau d’enfants retourné.</span><span class="sxs-lookup"><span data-stu-id="6481d-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6481d-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6481d-109">Return Value</span></span>  

 <span data-ttu-id="6481d-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6481d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6481d-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6481d-111">Requirements</span></span>  

 <span data-ttu-id="6481d-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6481d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6481d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6481d-113">See also</span></span>

- [<span data-ttu-id="6481d-114">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="6481d-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="6481d-115">GetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="6481d-115">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)
