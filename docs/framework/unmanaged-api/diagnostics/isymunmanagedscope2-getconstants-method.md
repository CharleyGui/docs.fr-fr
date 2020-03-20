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
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176615"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="053c0-102">ISymUnmanagedScope2::GetConstants, méthode</span><span class="sxs-lookup"><span data-stu-id="053c0-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="053c0-103">Obtient les constantes locales définies dans ce champ d’application.</span><span class="sxs-lookup"><span data-stu-id="053c0-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="053c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="053c0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="053c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="053c0-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="053c0-106">[dans] La longueur du tampon `pcConstants` que le paramètre indique.</span><span class="sxs-lookup"><span data-stu-id="053c0-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="053c0-107">[out] Un pointeur `ULONG32` à un qui reçoit la taille, en caractères, de la mémoire tampon nécessaire pour contenir les constantes.</span><span class="sxs-lookup"><span data-stu-id="053c0-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="053c0-108">[out] Le tampon qui stocke les constantes.</span><span class="sxs-lookup"><span data-stu-id="053c0-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="053c0-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="053c0-109">Return Value</span></span>  
 <span data-ttu-id="053c0-110">S_OK si la méthode réussit; autrement, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="053c0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="053c0-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="053c0-111">Requirements</span></span>  
 <span data-ttu-id="053c0-112">**En-tête:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="053c0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="053c0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="053c0-113">See also</span></span>

- [<span data-ttu-id="053c0-114">ISymUnmanagedScope2, interface</span><span class="sxs-lookup"><span data-stu-id="053c0-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
