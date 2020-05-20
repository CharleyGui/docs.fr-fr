---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
ms.openlocfilehash: a81a5afeec8f97864e1772347c6575b9d09cb176
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614888"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="d264c-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount, méthode</span><span class="sxs-lookup"><span data-stu-id="d264c-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="d264c-103">Obtient le nombre d’informations de recherche de symboles.</span><span class="sxs-lookup"><span data-stu-id="d264c-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d264c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d264c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d264c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d264c-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="d264c-106">] out] pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les informations de recherche.</span><span class="sxs-lookup"><span data-stu-id="d264c-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d264c-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d264c-107">Return Value</span></span>  
 <span data-ttu-id="d264c-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d264c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d264c-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d264c-109">Requirements</span></span>  
 <span data-ttu-id="d264c-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d264c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d264c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d264c-111">See also</span></span>

- [<span data-ttu-id="d264c-112">ISymUnmanagedReaderSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="d264c-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)
