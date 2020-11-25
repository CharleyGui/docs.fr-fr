---
title: ISymUnmanagedScope2::GetConstants, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: df42e58a9bb3bf00b3fa4df45086dc2219658e25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725844"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="22a9d-102">ISymUnmanagedScope2::GetConstants, méthode</span><span class="sxs-lookup"><span data-stu-id="22a9d-102">ISymUnmanagedScope2::GetConstants Method</span></span>

<span data-ttu-id="22a9d-103">Obtient les constantes locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="22a9d-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22a9d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22a9d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22a9d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="22a9d-105">Parameters</span></span>  

 `cConstants`  
 <span data-ttu-id="22a9d-106">dans Longueur de la mémoire tampon vers laquelle `pcConstants` pointe le paramètre.</span><span class="sxs-lookup"><span data-stu-id="22a9d-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="22a9d-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir les constantes.</span><span class="sxs-lookup"><span data-stu-id="22a9d-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="22a9d-108">à Mémoire tampon qui stocke les constantes.</span><span class="sxs-lookup"><span data-stu-id="22a9d-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22a9d-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="22a9d-109">Return Value</span></span>  

 <span data-ttu-id="22a9d-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="22a9d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22a9d-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="22a9d-111">Requirements</span></span>  

 <span data-ttu-id="22a9d-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="22a9d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a9d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22a9d-113">See also</span></span>

- [<span data-ttu-id="22a9d-114">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="22a9d-114">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
