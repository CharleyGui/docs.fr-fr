---
title: ISymUnmanagedWriter3::Commit, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.Commit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::Commit
helpviewer_keywords:
- Commit method, ISymUnmanagedWriter3 interface [.NET Framework debugging]
- ISymUnmanagedWriter3::Commit method [.NET Framework debugging]
ms.assetid: f6961922-46ec-4d2c-8369-85f880731f37
topic_type:
- apiref
ms.openlocfilehash: 394832d6144509717d2f79a78afaff50ad81c01d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683301"
---
# <a name="isymunmanagedwriter3commit-method"></a><span data-ttu-id="27aa7-102">ISymUnmanagedWriter3::Commit, méthode</span><span class="sxs-lookup"><span data-stu-id="27aa7-102">ISymUnmanagedWriter3::Commit Method</span></span>

<span data-ttu-id="27aa7-103">Valide les modifications écrites jusqu’à présent dans le flux.</span><span class="sxs-lookup"><span data-stu-id="27aa7-103">Commits the changes written so far to the stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27aa7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27aa7-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit();  
```  
  
## <a name="return-value"></a><span data-ttu-id="27aa7-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="27aa7-105">Return Value</span></span>  

 <span data-ttu-id="27aa7-106">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="27aa7-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27aa7-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="27aa7-107">Requirements</span></span>  

 <span data-ttu-id="27aa7-108">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="27aa7-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27aa7-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27aa7-109">See also</span></span>

- [<span data-ttu-id="27aa7-110">ISymUnmanagedWriter3, interface</span><span class="sxs-lookup"><span data-stu-id="27aa7-110">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
