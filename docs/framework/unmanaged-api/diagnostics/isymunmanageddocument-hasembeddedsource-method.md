---
title: ISymUnmanagedDocument::HasEmbeddedSource, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
ms.openlocfilehash: 533d8a5481fe9ba7e7e65775229156a9cc3cf4d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449110"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="045c8-102">ISymUnmanagedDocument::HasEmbeddedSource, méthode</span><span class="sxs-lookup"><span data-stu-id="045c8-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="045c8-103">Retourne `true` si la source est incorporée dans le document dans les symboles de débogage ; Sinon, retourne `false`.</span><span class="sxs-lookup"><span data-stu-id="045c8-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="045c8-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="045c8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="045c8-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="045c8-106">à Pointeur vers une variable qui indique si le document a une source incorporée dans les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="045c8-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="045c8-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="045c8-107">Return Value</span></span>  
 <span data-ttu-id="045c8-108">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="045c8-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045c8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="045c8-109">See also</span></span>

- [<span data-ttu-id="045c8-110">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="045c8-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
