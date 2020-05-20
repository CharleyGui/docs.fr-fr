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
ms.openlocfilehash: 9dcd8282adf200932e86c950bee0b073780ce02d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615304"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="8e102-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT, méthode</span><span class="sxs-lookup"><span data-stu-id="8e102-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="8e102-103">Obtient le HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8e102-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e102-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e102-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e102-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8e102-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="8e102-106">à Pointeur vers le HRESULT.</span><span class="sxs-lookup"><span data-stu-id="8e102-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e102-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8e102-107">Return Value</span></span>  
 <span data-ttu-id="8e102-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="8e102-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e102-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="8e102-109">Requirements</span></span>  
 <span data-ttu-id="8e102-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8e102-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e102-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e102-111">See also</span></span>

- [<span data-ttu-id="8e102-112">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="8e102-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)
