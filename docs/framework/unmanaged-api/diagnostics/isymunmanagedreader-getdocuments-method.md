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
ms.openlocfilehash: b8a3a74888a3caae03da6f88a003bd277939ae59
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615044"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="bb292-102">ISymUnmanagedReader::GetDocuments, méthode</span><span class="sxs-lookup"><span data-stu-id="bb292-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="bb292-103">Retourne un tableau de tous les documents définis dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="bb292-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb292-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb292-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb292-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bb292-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="bb292-106">[in] Taille du tableau `pDocs`.</span><span class="sxs-lookup"><span data-stu-id="bb292-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="bb292-107">à Pointeur vers une variable qui reçoit la longueur du tableau.</span><span class="sxs-lookup"><span data-stu-id="bb292-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="bb292-108">à Pointeur vers une variable qui reçoit le tableau de documents.</span><span class="sxs-lookup"><span data-stu-id="bb292-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb292-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bb292-109">Return Value</span></span>  
 <span data-ttu-id="bb292-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bb292-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb292-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="bb292-111">Requirements</span></span>  
 <span data-ttu-id="bb292-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bb292-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb292-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb292-113">See also</span></span>

- [<span data-ttu-id="bb292-114">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="bb292-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
