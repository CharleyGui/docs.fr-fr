---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
ms.openlocfilehash: 319ba58b5d012cbc0f9ddac0b83e5f3ae2ae062a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446169"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="e02c6-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength, méthode</span><span class="sxs-lookup"><span data-stu-id="e02c6-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="e02c6-103">Obtient la longueur du chemin d’accès de recherche.</span><span class="sxs-lookup"><span data-stu-id="e02c6-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e02c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e02c6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e02c6-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="e02c6-106">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir la longueur du chemin d’accès de recherche.</span><span class="sxs-lookup"><span data-stu-id="e02c6-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e02c6-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e02c6-107">Return Value</span></span>  
 <span data-ttu-id="e02c6-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e02c6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e02c6-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e02c6-109">Requirements</span></span>  
 <span data-ttu-id="e02c6-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e02c6-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02c6-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e02c6-111">See also</span></span>

- [<span data-ttu-id="e02c6-112">ISymUnmanagedSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="e02c6-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
