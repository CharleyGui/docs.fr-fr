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
ms.openlocfilehash: 5bd94cb851d4bb044d4ce03b97d6342a2c9652e4
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441316"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="78a45-102">ISymUnmanagedDispose::Destroy, méthode</span><span class="sxs-lookup"><span data-stu-id="78a45-102">ISymUnmanagedDispose::Destroy Method</span></span>
<span data-ttu-id="78a45-103">Force l’objet sous-jacent à libérer toutes les références internes et à retourner un échec sur les appels de méthode suivants.</span><span class="sxs-lookup"><span data-stu-id="78a45-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78a45-104">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="78a45-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="78a45-105">Return Value</span></span>  
 <span data-ttu-id="78a45-106">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="78a45-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78a45-107">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="78a45-107">Requirements</span></span>  
 <span data-ttu-id="78a45-108">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="78a45-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a45-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78a45-109">See also</span></span>

- [<span data-ttu-id="78a45-110">ISymUnmanagedDispose, interface</span><span class="sxs-lookup"><span data-stu-id="78a45-110">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)
