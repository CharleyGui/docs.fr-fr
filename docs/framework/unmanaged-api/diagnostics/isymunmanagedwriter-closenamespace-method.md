---
title: ISymUnmanagedWriter::CloseNamespace, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
ms.openlocfilehash: 13a433157e0c92653edf234f1f1f885270196ffd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686408"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="7d0b7-102">ISymUnmanagedWriter::CloseNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="7d0b7-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>

<span data-ttu-id="7d0b7-103">Ferme l’espace de noms le plus récemment ouvert.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d0b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d0b7-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7d0b7-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7d0b7-105">Return Value</span></span>  

 <span data-ttu-id="7d0b7-106">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="7d0b7-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d0b7-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7d0b7-107">Requirements</span></span>  

 <span data-ttu-id="7d0b7-108">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7d0b7-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d0b7-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d0b7-109">See also</span></span>

- [<span data-ttu-id="7d0b7-110">ISymUnmanagedWriter, interface</span><span class="sxs-lookup"><span data-stu-id="7d0b7-110">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="7d0b7-111">OpenNamespace, méthode</span><span class="sxs-lookup"><span data-stu-id="7d0b7-111">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)
