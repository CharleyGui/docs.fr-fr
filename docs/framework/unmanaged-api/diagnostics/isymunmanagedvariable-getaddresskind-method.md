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
ms.openlocfilehash: 4d2de38e5e506873a6db262dcec19c7af9d8a0d0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446091"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="75844-102">ISymUnmanagedVariable::GetAddressKind, méthode</span><span class="sxs-lookup"><span data-stu-id="75844-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="75844-103">Obtient le type d’adresse de cette variable.</span><span class="sxs-lookup"><span data-stu-id="75844-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75844-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75844-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75844-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="75844-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="75844-106">à Pointeur vers un `ULONG32` qui reçoit la valeur.</span><span class="sxs-lookup"><span data-stu-id="75844-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="75844-107">Les valeurs possibles sont définies dans l’énumération [CorSymAddrKind,](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="75844-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75844-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="75844-108">Return Value</span></span>  
 <span data-ttu-id="75844-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="75844-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75844-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="75844-110">Requirements</span></span>  
 <span data-ttu-id="75844-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="75844-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75844-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75844-112">See also</span></span>

- [<span data-ttu-id="75844-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="75844-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
