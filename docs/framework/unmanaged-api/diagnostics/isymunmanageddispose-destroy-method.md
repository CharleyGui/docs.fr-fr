---
title: ISymUnmanagedDispose::Destroy, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
ms.openlocfilehash: 6a31026f5b1669c0c29762048dc2c5c1c7bbb6a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732825"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="f623c-102">ISymUnmanagedDispose::Destroy, méthode</span><span class="sxs-lookup"><span data-stu-id="f623c-102">ISymUnmanagedDispose::Destroy Method</span></span>

<span data-ttu-id="f623c-103">Force l’objet sous-jacent à libérer toutes les références internes et à retourner un échec sur les appels de méthode suivants.</span><span class="sxs-lookup"><span data-stu-id="f623c-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f623c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f623c-104">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f623c-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f623c-105">Return Value</span></span>  

 <span data-ttu-id="f623c-106">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f623c-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f623c-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f623c-107">Requirements</span></span>  

 <span data-ttu-id="f623c-108">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f623c-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f623c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f623c-109">See also</span></span>

- [<span data-ttu-id="f623c-110">ISymUnmanagedDispose, interface</span><span class="sxs-lookup"><span data-stu-id="f623c-110">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)
