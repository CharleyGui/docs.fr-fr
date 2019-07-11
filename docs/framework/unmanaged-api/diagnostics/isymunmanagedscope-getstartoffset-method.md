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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34bcaf1ef00806e3883996804336bd22b9b634f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777845"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="aef13-102">ISymUnmanagedScope::GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="aef13-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="aef13-103">Obtient l’offset de début pour cette étendue.</span><span class="sxs-lookup"><span data-stu-id="aef13-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aef13-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aef13-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aef13-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="aef13-106">[out] Un pointeur vers un `ULONG32` qui contient l’offset de démarrage.</span><span class="sxs-lookup"><span data-stu-id="aef13-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aef13-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="aef13-107">Return Value</span></span>  
 <span data-ttu-id="aef13-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="aef13-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aef13-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aef13-109">Requirements</span></span>  
 <span data-ttu-id="aef13-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="aef13-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef13-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aef13-111">See also</span></span>

- [<span data-ttu-id="aef13-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="aef13-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="aef13-113">GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="aef13-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
