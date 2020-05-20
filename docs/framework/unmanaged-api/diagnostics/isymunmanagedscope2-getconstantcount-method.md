---
title: ISymUnmanagedScope2::GetConstantCount, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: 88fc6b7d6076bca42050ca87533062557e6a7b50
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610949"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="2f07f-102">ISymUnmanagedScope2::GetConstantCount, méthode</span><span class="sxs-lookup"><span data-stu-id="2f07f-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="2f07f-103">Obtient le nombre des constantes définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="2f07f-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f07f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f07f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f07f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f07f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2f07f-106">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir les constantes.</span><span class="sxs-lookup"><span data-stu-id="2f07f-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f07f-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2f07f-107">Return Value</span></span>  
 <span data-ttu-id="2f07f-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="2f07f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f07f-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="2f07f-109">Requirements</span></span>  
 <span data-ttu-id="2f07f-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2f07f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f07f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f07f-111">See also</span></span>

- [<span data-ttu-id="2f07f-112">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="2f07f-112">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
