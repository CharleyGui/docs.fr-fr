---
title: ISymUnmanagedVariable::GetAddressKind, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
ms.openlocfilehash: 093c5e3e64395c8946acd9201990d132e8111fc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610585"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="1416d-102">ISymUnmanagedVariable::GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="1416d-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="1416d-103">Obtient le type d’adresse de cette variable.</span><span class="sxs-lookup"><span data-stu-id="1416d-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1416d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1416d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1416d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1416d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1416d-106">à Pointeur vers un `ULONG32` qui reçoit la valeur.</span><span class="sxs-lookup"><span data-stu-id="1416d-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="1416d-107">Les valeurs possibles sont définies dans l’énumération [CorSymAddrKind,](corsymaddrkind-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1416d-107">The possible values are defined in the [CorSymAddrKind](corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1416d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1416d-108">Return Value</span></span>  
 <span data-ttu-id="1416d-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1416d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1416d-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="1416d-110">Requirements</span></span>  
 <span data-ttu-id="1416d-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1416d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1416d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1416d-112">See also</span></span>

- [<span data-ttu-id="1416d-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="1416d-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
