---
title: ISymUnmanagedNamespace::GetVariables, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
ms.openlocfilehash: 98ed5556020b93fb1f31d1dde84690fc33092627
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448376"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="9be2e-102">ISymUnmanagedNamespace::GetVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="9be2e-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="9be2e-103">Returns all variables defined at global scope within this namespace.</span><span class="sxs-lookup"><span data-stu-id="9be2e-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9be2e-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9be2e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9be2e-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="9be2e-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span><span class="sxs-lookup"><span data-stu-id="9be2e-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="9be2e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span><span class="sxs-lookup"><span data-stu-id="9be2e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="9be2e-108">[out] A pointer to a buffer that contains the namespaces.</span><span class="sxs-lookup"><span data-stu-id="9be2e-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9be2e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9be2e-109">Return Value</span></span>  
 <span data-ttu-id="9be2e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="9be2e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9be2e-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="9be2e-111">Requirements</span></span>  
 <span data-ttu-id="9be2e-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9be2e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9be2e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9be2e-113">See also</span></span>

- [<span data-ttu-id="9be2e-114">ISymUnmanagedNamespace, interface</span><span class="sxs-lookup"><span data-stu-id="9be2e-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
