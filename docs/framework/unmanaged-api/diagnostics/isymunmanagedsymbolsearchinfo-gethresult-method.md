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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b32865e0ac9d8a4a049db5d7ed6179879342c10a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778107"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="5d5b3-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT, méthode</span><span class="sxs-lookup"><span data-stu-id="5d5b3-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="5d5b3-103">Obtient le HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d5b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d5b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d5b3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5d5b3-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="5d5b3-106">[out] Pointeur vers la valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d5b3-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5d5b3-107">Return Value</span></span>  
 <span data-ttu-id="5d5b3-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5d5b3-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d5b3-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5d5b3-109">Requirements</span></span>  
 <span data-ttu-id="5d5b3-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5d5b3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5b3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d5b3-111">See also</span></span>

- [<span data-ttu-id="5d5b3-112">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="5d5b3-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
