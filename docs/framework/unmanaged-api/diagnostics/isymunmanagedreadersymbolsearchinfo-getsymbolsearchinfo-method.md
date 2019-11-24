---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
ms.openlocfilehash: 402b5b4bc9734be59ff342a4f86f2c4a1ed23b5f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446410"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="2c94c-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="2c94c-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="2c94c-103">Obtient les informations de recherche de symboles.</span><span class="sxs-lookup"><span data-stu-id="2c94c-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c94c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c94c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c94c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c94c-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="2c94c-106">dans `ULONG32` qui indique la taille de `rgpSearchInfo`.</span><span class="sxs-lookup"><span data-stu-id="2c94c-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="2c94c-107">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les informations de recherche.</span><span class="sxs-lookup"><span data-stu-id="2c94c-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="2c94c-108">à Pointeur défini sur l’interface [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="2c94c-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c94c-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2c94c-109">Return Value</span></span>  
 <span data-ttu-id="2c94c-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2c94c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c94c-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2c94c-111">Requirements</span></span>  
 <span data-ttu-id="2c94c-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2c94c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c94c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c94c-113">See also</span></span>

- [<span data-ttu-id="2c94c-114">ISymUnmanagedReaderSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="2c94c-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
