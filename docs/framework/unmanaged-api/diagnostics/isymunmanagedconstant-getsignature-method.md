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
ms.openlocfilehash: 332d60418c744a9391c7c0afc20248c2239b090c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441618"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="a6e8c-102">ISymUnmanagedConstant::GetSignature, méthode</span><span class="sxs-lookup"><span data-stu-id="a6e8c-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="a6e8c-103">Obtient la signature de la constante.</span><span class="sxs-lookup"><span data-stu-id="a6e8c-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6e8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6e8c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6e8c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6e8c-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="a6e8c-106">dans Longueur de la mémoire tampon vers laquelle `pcSig` pointe le paramètre.</span><span class="sxs-lookup"><span data-stu-id="a6e8c-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="a6e8c-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir la signature.</span><span class="sxs-lookup"><span data-stu-id="a6e8c-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="a6e8c-108">à Mémoire tampon qui stocke la signature.</span><span class="sxs-lookup"><span data-stu-id="a6e8c-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6e8c-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a6e8c-109">Return Value</span></span>  
 <span data-ttu-id="a6e8c-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a6e8c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6e8c-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="a6e8c-111">Requirements</span></span>  
 <span data-ttu-id="a6e8c-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a6e8c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6e8c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6e8c-113">See also</span></span>

- [<span data-ttu-id="a6e8c-114">ISymUnmanagedConstant, interface</span><span class="sxs-lookup"><span data-stu-id="a6e8c-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="a6e8c-115">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="a6e8c-115">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="a6e8c-116">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="a6e8c-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
