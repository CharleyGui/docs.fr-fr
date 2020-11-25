---
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount, méthode
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
ms.openlocfilehash: 53897b6f964afb1f8ca95bc8f93c532e148ad129
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730511"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="3d635-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount, méthode</span><span class="sxs-lookup"><span data-stu-id="3d635-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>

<span data-ttu-id="3d635-103">Obtient le nombre de documents dans lesquels cette méthode contient des lignes.</span><span class="sxs-lookup"><span data-stu-id="3d635-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d635-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d635-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d635-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d635-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="3d635-106">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les documents.</span><span class="sxs-lookup"><span data-stu-id="3d635-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d635-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3d635-107">Return Value</span></span>  

 <span data-ttu-id="3d635-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="3d635-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d635-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3d635-109">Requirements</span></span>  

 <span data-ttu-id="3d635-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3d635-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d635-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d635-111">See also</span></span>

- [<span data-ttu-id="3d635-112">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="3d635-112">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
