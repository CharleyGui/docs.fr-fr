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
ms.openlocfilehash: 68a0f9ec8793d465a6fa3b1cb6936eddd7be4c8f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615408"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="18989-102">ISymUnmanagedReader2::GetMethodsInDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="18989-102">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>
<span data-ttu-id="18989-103">Obtient toutes les méthodes qui ont des informations de ligne dans le document fourni.</span><span class="sxs-lookup"><span data-stu-id="18989-103">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18989-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18989-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18989-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="18989-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="18989-106">dans Pointeur vers le document.</span><span class="sxs-lookup"><span data-stu-id="18989-106">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="18989-107">dans `ULONG32`Qui indique la taille du `pRetVal` tableau.</span><span class="sxs-lookup"><span data-stu-id="18989-107">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="18989-108">à Pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les méthodes.</span><span class="sxs-lookup"><span data-stu-id="18989-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="18989-109">à Pointeur vers la mémoire tampon qui reçoit les méthodes.</span><span class="sxs-lookup"><span data-stu-id="18989-109">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18989-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="18989-110">Return Value</span></span>  
 <span data-ttu-id="18989-111">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="18989-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18989-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="18989-112">Requirements</span></span>  
 <span data-ttu-id="18989-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="18989-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18989-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18989-114">See also</span></span>

- [<span data-ttu-id="18989-115">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="18989-115">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
