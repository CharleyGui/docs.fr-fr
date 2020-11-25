---
title: ISymUnmanagedVariable::GetEndOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: cf4179f839b62409d5b2185f3e11e8e732c29187
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721866"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="653e2-102">ISymUnmanagedVariable::GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="653e2-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>

<span data-ttu-id="653e2-103">Obtient le décalage de fin de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="653e2-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="653e2-104">S’il s’agit d’une variable locale dans une étendue, le décalage de fin se situe dans les offsets définis pour l’étendue.</span><span class="sxs-lookup"><span data-stu-id="653e2-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="653e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="653e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="653e2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="653e2-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="653e2-107">à Pointeur vers un `ULONG32` qui reçoit le décalage de fin.</span><span class="sxs-lookup"><span data-stu-id="653e2-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="653e2-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="653e2-108">Return Value</span></span>  

 <span data-ttu-id="653e2-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="653e2-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="653e2-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="653e2-110">Requirements</span></span>  

 <span data-ttu-id="653e2-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="653e2-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653e2-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="653e2-112">See also</span></span>

- [<span data-ttu-id="653e2-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="653e2-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="653e2-114">GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="653e2-114">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)
