---
title: ISymUnmanagedVariable::GetAddressField1, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
ms.openlocfilehash: 253fd17178c03bc0c4d8ea031888a404ad56f876
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615278"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="2c379-102">ISymUnmanagedVariable::GetAddressField1, méthode</span><span class="sxs-lookup"><span data-stu-id="2c379-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="2c379-103">Obtient le premier champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="2c379-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="2c379-104">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="2c379-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c379-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c379-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c379-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c379-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2c379-107">à Pointeur vers un `ULONG32` qui reçoit le premier champ d’adresse.</span><span class="sxs-lookup"><span data-stu-id="2c379-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c379-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2c379-108">Return Value</span></span>  
 <span data-ttu-id="2c379-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2c379-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c379-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="2c379-110">Requirements</span></span>  
 <span data-ttu-id="2c379-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2c379-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c379-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c379-112">See also</span></span>

- [<span data-ttu-id="2c379-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="2c379-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="2c379-114">GetAddressField2, méthode</span><span class="sxs-lookup"><span data-stu-id="2c379-114">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="2c379-115">GetAddressField3, méthode</span><span class="sxs-lookup"><span data-stu-id="2c379-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="2c379-116">GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="2c379-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
