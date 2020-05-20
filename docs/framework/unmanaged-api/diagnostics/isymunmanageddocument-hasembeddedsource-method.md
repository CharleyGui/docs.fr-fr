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
ms.openlocfilehash: d654f6d57bd784063fc7f87dd9767bdc27ad2776
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615577"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="7d799-102">ISymUnmanagedDocument::HasEmbeddedSource, méthode</span><span class="sxs-lookup"><span data-stu-id="7d799-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="7d799-103">Retourne `true` si la source du document est incorporée dans les symboles de débogage ; sinon, retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="7d799-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d799-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d799-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d799-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7d799-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7d799-106">à Pointeur vers une variable qui indique si le document a une source incorporée dans les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="7d799-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d799-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7d799-107">Return Value</span></span>  
 <span data-ttu-id="7d799-108">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="7d799-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d799-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d799-109">See also</span></span>

- [<span data-ttu-id="7d799-110">ISymUnmanagedDocument, interface</span><span class="sxs-lookup"><span data-stu-id="7d799-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
