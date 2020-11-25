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
ms.openlocfilehash: 69e05fc33b3489f535f1d051da0294fe59e11e00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708957"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="eee21-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="eee21-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>

<span data-ttu-id="eee21-103">Obtient les informations de recherche de symboles.</span><span class="sxs-lookup"><span data-stu-id="eee21-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eee21-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eee21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eee21-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="eee21-105">Parameters</span></span>  

 `cSearchInfo`  
 <span data-ttu-id="eee21-106">dans `ULONG32` Qui indique la taille de `rgpSearchInfo` .</span><span class="sxs-lookup"><span data-stu-id="eee21-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="eee21-107">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les informations de recherche.</span><span class="sxs-lookup"><span data-stu-id="eee21-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="eee21-108">à Pointeur défini sur l’interface [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) retournée.</span><span class="sxs-lookup"><span data-stu-id="eee21-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eee21-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="eee21-109">Return Value</span></span>  

 <span data-ttu-id="eee21-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="eee21-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eee21-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="eee21-111">Requirements</span></span>  

 <span data-ttu-id="eee21-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="eee21-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eee21-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eee21-113">See also</span></span>

- [<span data-ttu-id="eee21-114">ISymUnmanagedReaderSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="eee21-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
