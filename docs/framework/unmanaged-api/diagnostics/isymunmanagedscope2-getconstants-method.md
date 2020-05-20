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
ms.openlocfilehash: f558d209d13fae93bd3a6f5e0e653afb91371a6a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615330"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="5e7ed-102">ISymUnmanagedScope2::GetConstants, méthode</span><span class="sxs-lookup"><span data-stu-id="5e7ed-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="5e7ed-103">Obtient les constantes locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e7ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e7ed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e7ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e7ed-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="5e7ed-106">dans Longueur de la mémoire tampon vers laquelle `pcConstants` pointe le paramètre.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="5e7ed-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir les constantes.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="5e7ed-108">à Mémoire tampon qui stocke les constantes.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e7ed-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5e7ed-109">Return Value</span></span>  
 <span data-ttu-id="5e7ed-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="5e7ed-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e7ed-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="5e7ed-111">Requirements</span></span>  
 <span data-ttu-id="5e7ed-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5e7ed-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e7ed-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e7ed-113">See also</span></span>

- [<span data-ttu-id="5e7ed-114">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="5e7ed-114">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)
