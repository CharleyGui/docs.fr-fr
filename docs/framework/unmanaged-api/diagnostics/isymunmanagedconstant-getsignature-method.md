---
title: ISymUnmanagedConstant::GetSignature, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5d479e9f55cf7d7a13fef99f302bfd8d9d89d47f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776946"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="12542-102">ISymUnmanagedConstant::GetSignature, méthode</span><span class="sxs-lookup"><span data-stu-id="12542-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="12542-103">Obtient la signature de la constante.</span><span class="sxs-lookup"><span data-stu-id="12542-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12542-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12542-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12542-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12542-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="12542-106">[in] La longueur de la mémoire tampon qui le `pcSig` paramètre pointe vers.</span><span class="sxs-lookup"><span data-stu-id="12542-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="12542-107">[out] Un pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir la signature.</span><span class="sxs-lookup"><span data-stu-id="12542-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="12542-108">[out] La mémoire tampon qui stocke la signature.</span><span class="sxs-lookup"><span data-stu-id="12542-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12542-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="12542-109">Return Value</span></span>  
 <span data-ttu-id="12542-110">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="12542-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12542-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="12542-111">Requirements</span></span>  
 <span data-ttu-id="12542-112">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="12542-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12542-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12542-113">See also</span></span>

- [<span data-ttu-id="12542-114">ISymUnmanagedConstant, interface</span><span class="sxs-lookup"><span data-stu-id="12542-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="12542-115">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="12542-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="12542-116">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="12542-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
