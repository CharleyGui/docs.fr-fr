---
title: ISymUnmanagedDocument::GetLanguage, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
ms.openlocfilehash: 075d46b0bbc68add0203daf7430afb712c998fe0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700975"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="5b0f1-102">ISymUnmanagedDocument::GetLanguage, méthode</span><span class="sxs-lookup"><span data-stu-id="5b0f1-102">ISymUnmanagedDocument::GetLanguage Method</span></span>

<span data-ttu-id="5b0f1-103">Obtient l’identificateur de langue de ce document</span><span class="sxs-lookup"><span data-stu-id="5b0f1-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b0f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b0f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b0f1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5b0f1-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="5b0f1-106">à Pointeur vers une variable qui reçoit l’identificateur de langue.</span><span class="sxs-lookup"><span data-stu-id="5b0f1-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b0f1-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5b0f1-107">Return Value</span></span>  

 <span data-ttu-id="5b0f1-108">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="5b0f1-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0f1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b0f1-109">See also</span></span>

- [<span data-ttu-id="5b0f1-110">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="5b0f1-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
