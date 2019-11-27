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
ms.openlocfilehash: 00be35e9a15349b8bca5f76b948b8477dd240888
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449242"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="ac955-102">ISymUnmanagedConstant::GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="ac955-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="ac955-103">Obtient la valeur de la constante.</span><span class="sxs-lookup"><span data-stu-id="ac955-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac955-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac955-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac955-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ac955-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="ac955-106">à Pointeur vers une variable qui reçoit la valeur.</span><span class="sxs-lookup"><span data-stu-id="ac955-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac955-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ac955-107">Return Value</span></span>  
 <span data-ttu-id="ac955-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ac955-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac955-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ac955-109">Requirements</span></span>  
 <span data-ttu-id="ac955-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ac955-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac955-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac955-111">See also</span></span>

- [<span data-ttu-id="ac955-112">ISymUnmanagedConstant, interface</span><span class="sxs-lookup"><span data-stu-id="ac955-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="ac955-113">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="ac955-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="ac955-114">GetSignature, méthode</span><span class="sxs-lookup"><span data-stu-id="ac955-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
