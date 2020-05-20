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
ms.openlocfilehash: 89be772ee3d8a6fc5acb74d5ebe6d3c691764f89
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441953"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="aa76f-102">ISymENCUnmanagedMethod::GetDocumentsForMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="aa76f-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="aa76f-103">Obtient les documents dans lesquels cette méthode contient des lignes.</span><span class="sxs-lookup"><span data-stu-id="aa76f-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa76f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa76f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa76f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aa76f-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="aa76f-106">dans Longueur de la mémoire tampon vers laquelle pointe `pcDocs` .</span><span class="sxs-lookup"><span data-stu-id="aa76f-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="aa76f-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir les documents.</span><span class="sxs-lookup"><span data-stu-id="aa76f-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="aa76f-108">dans Mémoire tampon qui contient les documents.</span><span class="sxs-lookup"><span data-stu-id="aa76f-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa76f-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="aa76f-109">Return Value</span></span>  
 <span data-ttu-id="aa76f-110">S_OK si la méthode est réussie ; Sinon, un code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="aa76f-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa76f-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="aa76f-111">Requirements</span></span>  
 <span data-ttu-id="aa76f-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="aa76f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa76f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa76f-113">See also</span></span>

- [<span data-ttu-id="aa76f-114">ISymENCUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="aa76f-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
