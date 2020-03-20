---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod, méthode
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
ms.openlocfilehash: 97f0d81c389ffd0bd8a69df2ca39322d726f98bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176628"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="cc9ec-102">ISymENCUnmanagedMethod::GetDocumentsForMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="cc9ec-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="cc9ec-103">Obtient les documents que cette méthode a des lignes dans.</span><span class="sxs-lookup"><span data-stu-id="cc9ec-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc9ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc9ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc9ec-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cc9ec-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="cc9ec-106">[dans] La longueur du tampon `pcDocs`pointé par .</span><span class="sxs-lookup"><span data-stu-id="cc9ec-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="cc9ec-107">[out] Un pointeur `ULONG32` à un qui reçoit la taille, en caractères, de la mémoire tampon nécessaire pour contenir les documents.</span><span class="sxs-lookup"><span data-stu-id="cc9ec-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="cc9ec-108">[dans] Le tampon qui contient les documents.</span><span class="sxs-lookup"><span data-stu-id="cc9ec-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc9ec-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cc9ec-109">Return Value</span></span>  
 <span data-ttu-id="cc9ec-110">S_OK si la méthode réussit; autrement, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="cc9ec-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc9ec-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cc9ec-111">Requirements</span></span>  
 <span data-ttu-id="cc9ec-112">**En-tête:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cc9ec-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc9ec-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc9ec-113">See also</span></span>

- [<span data-ttu-id="cc9ec-114">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="cc9ec-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
