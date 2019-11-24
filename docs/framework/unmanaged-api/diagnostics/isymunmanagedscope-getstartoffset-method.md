---
title: ISymUnmanagedScope::GetStartOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
ms.openlocfilehash: 9d1ee82f24e1908af1998e424006415af3134456
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446272"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="92fc0-102">ISymUnmanagedScope::GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="92fc0-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="92fc0-103">Gets the start offset for this scope.</span><span class="sxs-lookup"><span data-stu-id="92fc0-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92fc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92fc0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92fc0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="92fc0-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="92fc0-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span><span class="sxs-lookup"><span data-stu-id="92fc0-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92fc0-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="92fc0-107">Return Value</span></span>  
 <span data-ttu-id="92fc0-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="92fc0-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92fc0-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="92fc0-109">Requirements</span></span>  
 <span data-ttu-id="92fc0-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="92fc0-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92fc0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92fc0-111">See also</span></span>

- [<span data-ttu-id="92fc0-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="92fc0-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="92fc0-113">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="92fc0-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
