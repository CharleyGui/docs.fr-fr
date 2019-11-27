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
ms.openlocfilehash: cea18fefa2d356cbb5857db5133b1086c38ac6ff
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449180"
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="6be68-102">ISymUnmanagedDocument::GetLanguage, méthode</span><span class="sxs-lookup"><span data-stu-id="6be68-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="6be68-103">Obtient l’identificateur de langue de ce document</span><span class="sxs-lookup"><span data-stu-id="6be68-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6be68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6be68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6be68-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6be68-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6be68-106">à Pointeur vers une variable qui reçoit l’identificateur de langue.</span><span class="sxs-lookup"><span data-stu-id="6be68-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6be68-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6be68-107">Return Value</span></span>  
 <span data-ttu-id="6be68-108">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="6be68-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be68-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6be68-109">See also</span></span>

- [<span data-ttu-id="6be68-110">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="6be68-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
