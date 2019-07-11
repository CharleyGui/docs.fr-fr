---
title: ISymUnmanagedReader2::GetMethodsInDocument, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7fa192a8e8b8a876f672e36bb906a714b1266e2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736667"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="e5a8c-102">ISymUnmanagedReader2::GetMethodsInDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="e5a8c-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="e5a8c-103">Obtient toutes les méthodes ayant des informations de ligne dans le document fourni.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5a8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5a8c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5a8c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5a8c-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="e5a8c-106">[in] Pointeur vers le document.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="e5a8c-107">[in] Un `ULONG32` qui indique la taille de la `pRetVal` tableau.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="e5a8c-108">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les méthodes.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e5a8c-109">[out] Pointeur vers la mémoire tampon qui reçoit les méthodes.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5a8c-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e5a8c-110">Return Value</span></span>  
 <span data-ttu-id="e5a8c-111">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e5a8c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5a8c-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e5a8c-112">Requirements</span></span>  
 <span data-ttu-id="e5a8c-113">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e5a8c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5a8c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5a8c-114">See also</span></span>

- [<span data-ttu-id="e5a8c-115">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="e5a8c-115">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
