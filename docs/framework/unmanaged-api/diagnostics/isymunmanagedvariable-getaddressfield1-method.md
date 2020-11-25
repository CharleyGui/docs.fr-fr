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
ms.openlocfilehash: e3ea3c0fd65750d52c0cfb10edbe18b1512f724b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729016"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="906a3-102">ISymUnmanagedVariable::GetAddressField1, méthode</span><span class="sxs-lookup"><span data-stu-id="906a3-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>

<span data-ttu-id="906a3-103">Obtient le premier champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="906a3-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="906a3-104">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="906a3-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906a3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="906a3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="906a3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="906a3-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="906a3-107">à Pointeur vers un `ULONG32` qui reçoit le premier champ d’adresse.</span><span class="sxs-lookup"><span data-stu-id="906a3-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="906a3-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="906a3-108">Return Value</span></span>  

 <span data-ttu-id="906a3-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="906a3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="906a3-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="906a3-110">Requirements</span></span>  

 <span data-ttu-id="906a3-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="906a3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906a3-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="906a3-112">See also</span></span>

- [<span data-ttu-id="906a3-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="906a3-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="906a3-114">GetAddressField2, méthode</span><span class="sxs-lookup"><span data-stu-id="906a3-114">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="906a3-115">GetAddressField3, méthode</span><span class="sxs-lookup"><span data-stu-id="906a3-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="906a3-116">GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="906a3-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
