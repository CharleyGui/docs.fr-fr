---
title: ISymUnmanagedVariable::GetAddressField2, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
ms.openlocfilehash: 6256d052780b1c610e61267be2517954d722a42d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610598"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="82383-102">ISymUnmanagedVariable::GetAddressField2, méthode</span><span class="sxs-lookup"><span data-stu-id="82383-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="82383-103">Obtient le deuxième champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="82383-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="82383-104">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="82383-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82383-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82383-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82383-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82383-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="82383-107">à Pointeur vers un `ULONG32` qui reçoit le deuxième champ d’adresse.</span><span class="sxs-lookup"><span data-stu-id="82383-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82383-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="82383-108">Return Value</span></span>  
 <span data-ttu-id="82383-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="82383-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82383-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="82383-110">Requirements</span></span>  
 <span data-ttu-id="82383-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="82383-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82383-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82383-112">See also</span></span>

- [<span data-ttu-id="82383-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="82383-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="82383-114">GetAddressField1, méthode</span><span class="sxs-lookup"><span data-stu-id="82383-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="82383-115">GetAddressField3, méthode</span><span class="sxs-lookup"><span data-stu-id="82383-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="82383-116">GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="82383-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
