---
title: ISymUnmanagedConstant::GetName, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 924feaeb91b42404461ad5d276c0cb77279d4dc4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449275"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="f41f0-102">ISymUnmanagedConstant::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="f41f0-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="f41f0-103">Obtient le nom de la constante.</span><span class="sxs-lookup"><span data-stu-id="f41f0-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f41f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f41f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f41f0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f41f0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f41f0-106">dans Longueur de la mémoire tampon vers laquelle pointe le paramètre `szName`.</span><span class="sxs-lookup"><span data-stu-id="f41f0-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f41f0-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom, y compris la terminaison NULL.</span><span class="sxs-lookup"><span data-stu-id="f41f0-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="f41f0-108">à Mémoire tampon qui stocke le nom.</span><span class="sxs-lookup"><span data-stu-id="f41f0-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f41f0-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f41f0-109">Return Value</span></span>  
 <span data-ttu-id="f41f0-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="f41f0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f41f0-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f41f0-111">Requirements</span></span>  
 <span data-ttu-id="f41f0-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f41f0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f41f0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f41f0-113">See also</span></span>

- [<span data-ttu-id="f41f0-114">ISymUnmanagedConstant, interface</span><span class="sxs-lookup"><span data-stu-id="f41f0-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="f41f0-115">GetSignature, méthode</span><span class="sxs-lookup"><span data-stu-id="f41f0-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="f41f0-116">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="f41f0-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
