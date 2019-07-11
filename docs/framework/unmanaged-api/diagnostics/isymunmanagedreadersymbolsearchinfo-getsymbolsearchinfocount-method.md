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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1a72f76f1cd6f6571eaebff3a8046de8dcd3d74
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751457"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="185db-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount, méthode</span><span class="sxs-lookup"><span data-stu-id="185db-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="185db-103">Obtient le nombre des informations de la recherche de symbole.</span><span class="sxs-lookup"><span data-stu-id="185db-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="185db-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="185db-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="185db-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="185db-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="185db-106">] out] pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les informations de recherche.</span><span class="sxs-lookup"><span data-stu-id="185db-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="185db-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="185db-107">Return Value</span></span>  
 <span data-ttu-id="185db-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="185db-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="185db-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="185db-109">Requirements</span></span>  
 <span data-ttu-id="185db-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="185db-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="185db-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="185db-111">See also</span></span>

- [<span data-ttu-id="185db-112">ISymUnmanagedReaderSymbolSearchInfo, interface</span><span class="sxs-lookup"><span data-stu-id="185db-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)
