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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 463416165d2dbd7724d5cf0d29e40d8243ade34b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778319"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="12794-102">ISymUnmanagedVariable::GetAddressField2, méthode</span><span class="sxs-lookup"><span data-stu-id="12794-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="12794-103">Obtient le deuxième champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="12794-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="12794-104">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="12794-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12794-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12794-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12794-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12794-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="12794-107">[out] Un pointeur vers un `ULONG32` qui reçoit le deuxième champ d’adresse.</span><span class="sxs-lookup"><span data-stu-id="12794-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12794-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="12794-108">Return Value</span></span>  
 <span data-ttu-id="12794-109">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="12794-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12794-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="12794-110">Requirements</span></span>  
 <span data-ttu-id="12794-111">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="12794-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12794-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12794-112">See also</span></span>

- [<span data-ttu-id="12794-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="12794-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="12794-114">GetAddressField1, méthode</span><span class="sxs-lookup"><span data-stu-id="12794-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="12794-115">GetAddressField3, méthode</span><span class="sxs-lookup"><span data-stu-id="12794-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="12794-116">GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="12794-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
