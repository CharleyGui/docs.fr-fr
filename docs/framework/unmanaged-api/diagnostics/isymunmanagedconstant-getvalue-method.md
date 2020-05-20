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
ms.openlocfilehash: 8e20d2e0f3d5cb6dc7444c8e78665b6c8b82d2de
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441472"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="31365-102">ISymUnmanagedConstant::GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="31365-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="31365-103"> Obtient la valeur de la constante.</span><span class="sxs-lookup"><span data-stu-id="31365-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31365-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31365-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31365-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31365-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="31365-106">à Pointeur vers une variable qui reçoit la valeur.</span><span class="sxs-lookup"><span data-stu-id="31365-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31365-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="31365-107">Return Value</span></span>  
 <span data-ttu-id="31365-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="31365-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31365-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="31365-109">Requirements</span></span>  
 <span data-ttu-id="31365-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="31365-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31365-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31365-111">See also</span></span>

- [<span data-ttu-id="31365-112">ISymUnmanagedConstant, interface</span><span class="sxs-lookup"><span data-stu-id="31365-112">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="31365-113">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="31365-113">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="31365-114">GetSignature, méthode</span><span class="sxs-lookup"><span data-stu-id="31365-114">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
