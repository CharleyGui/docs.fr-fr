---
title: ISymUnmanagedVariable::GetStartOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
ms.openlocfilehash: f2996349fd2bf1765a3de5b67d3296a25b1eaa5e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610364"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="21d25-102">ISymUnmanagedVariable::GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="21d25-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="21d25-103">Obtient le décalage de début de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="21d25-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="21d25-104">S’il s’agit d’une variable locale dans une étendue, le décalage de début se situe dans les décalages définis pour l’étendue.</span><span class="sxs-lookup"><span data-stu-id="21d25-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21d25-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21d25-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21d25-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21d25-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="21d25-107">à Pointeur vers un `ULONG32` qui reçoit le décalage de début.</span><span class="sxs-lookup"><span data-stu-id="21d25-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21d25-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="21d25-108">Return Value</span></span>  
 <span data-ttu-id="21d25-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="21d25-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21d25-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="21d25-110">Requirements</span></span>  
 <span data-ttu-id="21d25-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="21d25-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d25-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21d25-112">See also</span></span>

- [<span data-ttu-id="21d25-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="21d25-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="21d25-114">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="21d25-114">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)
