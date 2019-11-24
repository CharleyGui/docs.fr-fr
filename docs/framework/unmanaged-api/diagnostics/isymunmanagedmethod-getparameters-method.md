---
title: ISymUnmanagedMethod::GetParameters, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
ms.openlocfilehash: 9e8139a822c877e70731e18ae5a75b83e6b7578e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448955"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="e8825-102">ISymUnmanagedMethod::GetParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="e8825-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="e8825-103">Gets the parameters for this method.</span><span class="sxs-lookup"><span data-stu-id="e8825-103">Gets the parameters for this method.</span></span> <span data-ttu-id="e8825-104">The parameters are returned in the order in which they are defined within the method's signature.</span><span class="sxs-lookup"><span data-stu-id="e8825-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8825-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8825-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8825-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8825-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="e8825-107">[in] Taille du tableau `params`.</span><span class="sxs-lookup"><span data-stu-id="e8825-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="e8825-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span><span class="sxs-lookup"><span data-stu-id="e8825-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="e8825-109">[out] A pointer to the buffer that receives the parameters.</span><span class="sxs-lookup"><span data-stu-id="e8825-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8825-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e8825-110">Return Value</span></span>  
 <span data-ttu-id="e8825-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="e8825-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8825-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="e8825-112">Requirements</span></span>  
 <span data-ttu-id="e8825-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e8825-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8825-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8825-114">See also</span></span>

- [<span data-ttu-id="e8825-115">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="e8825-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
