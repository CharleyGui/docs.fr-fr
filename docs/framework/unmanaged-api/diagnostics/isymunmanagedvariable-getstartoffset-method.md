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
ms.openlocfilehash: 68d20c33c5ccd554554cae57ee55f6f51d5d980c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733306"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="45665-102">ISymUnmanagedVariable::GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="45665-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>

<span data-ttu-id="45665-103">Obtient le décalage de début de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="45665-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="45665-104">S’il s’agit d’une variable locale dans une étendue, le décalage de début se situe dans les décalages définis pour l’étendue.</span><span class="sxs-lookup"><span data-stu-id="45665-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45665-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45665-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45665-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="45665-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="45665-107">à Pointeur vers un `ULONG32` qui reçoit le décalage de début.</span><span class="sxs-lookup"><span data-stu-id="45665-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45665-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="45665-108">Return Value</span></span>  

 <span data-ttu-id="45665-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="45665-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45665-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="45665-110">Requirements</span></span>  

 <span data-ttu-id="45665-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="45665-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45665-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45665-112">See also</span></span>

- [<span data-ttu-id="45665-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="45665-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="45665-114">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="45665-114">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)
