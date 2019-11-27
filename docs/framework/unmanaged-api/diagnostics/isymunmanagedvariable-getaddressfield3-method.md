---
title: ISymUnmanagedVariable::GetAddressField3, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: 3bdc79a6b6d81f6f0998f052f8bea1bf8af55402
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446108"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="c55c5-102">ISymUnmanagedVariable::GetAddressField3, méthode</span><span class="sxs-lookup"><span data-stu-id="c55c5-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="c55c5-103">Obtient le troisième champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="c55c5-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="c55c5-104">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="c55c5-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c55c5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c55c5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c55c5-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c55c5-107">à Pointeur vers un `ULONG32` qui reçoit le troisième champ d’adresse.</span><span class="sxs-lookup"><span data-stu-id="c55c5-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c55c5-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c55c5-108">Return Value</span></span>  
 <span data-ttu-id="c55c5-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c55c5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c55c5-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c55c5-110">Requirements</span></span>  
 <span data-ttu-id="c55c5-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c55c5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55c5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c55c5-112">See also</span></span>

- [<span data-ttu-id="c55c5-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="c55c5-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="c55c5-114">GetAddressField1, méthode</span><span class="sxs-lookup"><span data-stu-id="c55c5-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="c55c5-115">GetAddressField2, méthode</span><span class="sxs-lookup"><span data-stu-id="c55c5-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="c55c5-116">GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="c55c5-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
