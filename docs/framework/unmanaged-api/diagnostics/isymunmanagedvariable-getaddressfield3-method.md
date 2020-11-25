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
ms.openlocfilehash: 13746c4ac6322a401e547c1c7acc99c0eda9accf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723335"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="69f56-102">ISymUnmanagedVariable::GetAddressField3, méthode</span><span class="sxs-lookup"><span data-stu-id="69f56-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>

<span data-ttu-id="69f56-103">Obtient le troisième champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="69f56-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="69f56-104">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="69f56-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f56-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69f56-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69f56-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="69f56-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="69f56-107">à Pointeur vers un `ULONG32` qui reçoit le troisième champ d’adresse.</span><span class="sxs-lookup"><span data-stu-id="69f56-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69f56-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="69f56-108">Return Value</span></span>  

 <span data-ttu-id="69f56-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="69f56-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69f56-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="69f56-110">Requirements</span></span>  

 <span data-ttu-id="69f56-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="69f56-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f56-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69f56-112">See also</span></span>

- [<span data-ttu-id="69f56-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="69f56-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="69f56-114">GetAddressField1, méthode</span><span class="sxs-lookup"><span data-stu-id="69f56-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="69f56-115">GetAddressField2, méthode</span><span class="sxs-lookup"><span data-stu-id="69f56-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="69f56-116">GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="69f56-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
