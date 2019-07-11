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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b329d096a23df673de038036fa5ea196cbe0eac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736075"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="55150-102">ISymENCUnmanagedMethod::GetDocumentsForMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="55150-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="55150-103">Obtient les documents de cette méthode a des lignes.</span><span class="sxs-lookup"><span data-stu-id="55150-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55150-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55150-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55150-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="55150-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="55150-106">[in] La longueur de la mémoire tampon vers laquelle pointe `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="55150-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="55150-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir les documents.</span><span class="sxs-lookup"><span data-stu-id="55150-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="55150-108">[in] La mémoire tampon qui contient les documents.</span><span class="sxs-lookup"><span data-stu-id="55150-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55150-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="55150-109">Return Value</span></span>  
 <span data-ttu-id="55150-110">S_OK si la méthode réussit ; Sinon, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="55150-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55150-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="55150-111">Requirements</span></span>  
 <span data-ttu-id="55150-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="55150-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55150-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55150-113">See also</span></span>

- [<span data-ttu-id="55150-114">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="55150-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
