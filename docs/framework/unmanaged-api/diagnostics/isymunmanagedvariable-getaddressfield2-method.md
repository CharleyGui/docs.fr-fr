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
ms.openlocfilehash: 858341d5b8b1b3ecbe9dd5bd39a38f9cfd0d08dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714170"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="c4a5c-102">ISymUnmanagedVariable::GetAddressField2, méthode</span><span class="sxs-lookup"><span data-stu-id="c4a5c-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>

<span data-ttu-id="c4a5c-103">Obtient le deuxième champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="c4a5c-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="c4a5c-104">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="c4a5c-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4a5c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4a5c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4a5c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4a5c-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="c4a5c-107">à Pointeur vers un `ULONG32` qui reçoit le deuxième champ d’adresse.</span><span class="sxs-lookup"><span data-stu-id="c4a5c-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4a5c-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c4a5c-108">Return Value</span></span>  

 <span data-ttu-id="c4a5c-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c4a5c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4a5c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c4a5c-110">Requirements</span></span>  

 <span data-ttu-id="c4a5c-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c4a5c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4a5c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4a5c-112">See also</span></span>

- [<span data-ttu-id="c4a5c-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="c4a5c-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="c4a5c-114">GetAddressField1, méthode</span><span class="sxs-lookup"><span data-stu-id="c4a5c-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="c4a5c-115">GetAddressField3, méthode</span><span class="sxs-lookup"><span data-stu-id="c4a5c-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="c4a5c-116">GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="c4a5c-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
