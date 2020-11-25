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
ms.openlocfilehash: a931c15b1c4a9f099d11c43edd324cfcc2793090
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722269"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="0e232-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT, méthode</span><span class="sxs-lookup"><span data-stu-id="0e232-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>

<span data-ttu-id="0e232-103">Obtient le HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0e232-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e232-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e232-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e232-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e232-105">Parameters</span></span>  

 `phr`  
 <span data-ttu-id="0e232-106">à Pointeur vers le HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0e232-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e232-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="0e232-107">Return Value</span></span>  

 <span data-ttu-id="0e232-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0e232-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e232-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e232-109">Requirements</span></span>  

 <span data-ttu-id="0e232-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0e232-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e232-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e232-111">See also</span></span>

- [<span data-ttu-id="0e232-112">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="0e232-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
