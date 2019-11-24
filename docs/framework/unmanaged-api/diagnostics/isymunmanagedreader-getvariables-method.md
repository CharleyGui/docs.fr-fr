---
title: ISymUnmanagedReader::GetVariables, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
ms.openlocfilehash: 4590d2734ea89bc1bc8a30db1c7ecac5effafd7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429761"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="e033d-102">ISymUnmanagedReader::GetVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="e033d-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="e033d-103">Returns a non-local variable, given its parent and name.</span><span class="sxs-lookup"><span data-stu-id="e033d-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e033d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e033d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e033d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e033d-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="e033d-106">[in] The parent of the variable.</span><span class="sxs-lookup"><span data-stu-id="e033d-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="e033d-107">[in] Taille du tableau `pVars`.</span><span class="sxs-lookup"><span data-stu-id="e033d-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="e033d-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span><span class="sxs-lookup"><span data-stu-id="e033d-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="e033d-109">[out] A pointer to the variable that receives the variables.</span><span class="sxs-lookup"><span data-stu-id="e033d-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e033d-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e033d-110">Return Value</span></span>  
 <span data-ttu-id="e033d-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="e033d-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e033d-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="e033d-112">Requirements</span></span>  
 <span data-ttu-id="e033d-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e033d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e033d-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e033d-114">See also</span></span>

- [<span data-ttu-id="e033d-115">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="e033d-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
