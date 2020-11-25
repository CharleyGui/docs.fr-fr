---
title: ISymUnmanagedConstant::GetValue, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 7a1c795f4a162699078e91bcaa274253169234e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732838"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="83844-102">ISymUnmanagedConstant::GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="83844-102">ISymUnmanagedConstant::GetValue Method</span></span>

<span data-ttu-id="83844-103"> Obtient la valeur de la constante.</span><span class="sxs-lookup"><span data-stu-id="83844-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83844-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83844-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83844-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83844-105">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="83844-106">à Pointeur vers une variable qui reçoit la valeur.</span><span class="sxs-lookup"><span data-stu-id="83844-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83844-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="83844-107">Return Value</span></span>  

 <span data-ttu-id="83844-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="83844-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83844-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="83844-109">Requirements</span></span>  

 <span data-ttu-id="83844-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="83844-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83844-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83844-111">See also</span></span>

- [<span data-ttu-id="83844-112">ISymUnmanagedConstant, interface</span><span class="sxs-lookup"><span data-stu-id="83844-112">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="83844-113">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="83844-113">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="83844-114">GetSignature, méthode</span><span class="sxs-lookup"><span data-stu-id="83844-114">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
