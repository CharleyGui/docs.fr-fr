---
title: ISymUnmanagedReader::GetDocuments, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fad7fae41fed70d996fcaaa7a7cdf69403b6094
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763354"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="0adaa-102">ISymUnmanagedReader::GetDocuments, méthode</span><span class="sxs-lookup"><span data-stu-id="0adaa-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="0adaa-103">Retourne un tableau de tous les documents définis dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="0adaa-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0adaa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0adaa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0adaa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0adaa-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="0adaa-106">[in] Taille du tableau `pDocs`.</span><span class="sxs-lookup"><span data-stu-id="0adaa-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="0adaa-107">[out] Pointeur vers une variable qui reçoit la longueur du tableau.</span><span class="sxs-lookup"><span data-stu-id="0adaa-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="0adaa-108">[out] Pointeur vers une variable qui reçoit le tableau de documents.</span><span class="sxs-lookup"><span data-stu-id="0adaa-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0adaa-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0adaa-109">Return Value</span></span>  
 <span data-ttu-id="0adaa-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0adaa-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0adaa-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0adaa-111">Requirements</span></span>  
 <span data-ttu-id="0adaa-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0adaa-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0adaa-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0adaa-113">See also</span></span>

- [<span data-ttu-id="0adaa-114">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="0adaa-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
