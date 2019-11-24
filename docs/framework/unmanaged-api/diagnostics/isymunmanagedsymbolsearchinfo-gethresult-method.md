---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
ms.openlocfilehash: 21f6cf18ee7d883e1792b597e08724946f53eda9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446188"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="182c8-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT, méthode</span><span class="sxs-lookup"><span data-stu-id="182c8-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="182c8-103">Gets the HRESULT.</span><span class="sxs-lookup"><span data-stu-id="182c8-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="182c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="182c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="182c8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="182c8-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="182c8-106">[out] A pointer to the HRESULT.</span><span class="sxs-lookup"><span data-stu-id="182c8-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="182c8-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="182c8-107">Return Value</span></span>  
 <span data-ttu-id="182c8-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="182c8-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="182c8-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="182c8-109">Requirements</span></span>  
 <span data-ttu-id="182c8-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="182c8-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="182c8-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="182c8-111">See also</span></span>

- [<span data-ttu-id="182c8-112">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="182c8-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
