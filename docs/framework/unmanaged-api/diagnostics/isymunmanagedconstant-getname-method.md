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
ms.openlocfilehash: 2dd70693528904459a34689dbad944c65c971254
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441641"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="b6661-102">ISymUnmanagedConstant::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="b6661-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="b6661-103">Obtient le nom de la constante.</span><span class="sxs-lookup"><span data-stu-id="b6661-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6661-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6661-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6661-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6661-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b6661-106">dans Longueur de la mémoire tampon vers laquelle `szName` pointe le paramètre.</span><span class="sxs-lookup"><span data-stu-id="b6661-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b6661-107">à Pointeur vers un `ULONG32` qui reçoit la taille, en caractères, de la mémoire tampon requise pour contenir le nom, y compris l’arrêt null.</span><span class="sxs-lookup"><span data-stu-id="b6661-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="b6661-108">à Mémoire tampon qui stocke le nom.</span><span class="sxs-lookup"><span data-stu-id="b6661-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b6661-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b6661-109">Return Value</span></span>  
 <span data-ttu-id="b6661-110">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b6661-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6661-111">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="b6661-111">Requirements</span></span>  
 <span data-ttu-id="b6661-112">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b6661-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6661-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6661-113">See also</span></span>

- [<span data-ttu-id="b6661-114">ISymUnmanagedConstant, interface</span><span class="sxs-lookup"><span data-stu-id="b6661-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="b6661-115">GetSignature, méthode</span><span class="sxs-lookup"><span data-stu-id="b6661-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="b6661-116">GetValue, méthode</span><span class="sxs-lookup"><span data-stu-id="b6661-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
