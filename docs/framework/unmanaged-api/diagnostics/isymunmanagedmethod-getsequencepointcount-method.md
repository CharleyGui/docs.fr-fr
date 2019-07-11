---
title: ISymUnmanagedMethod::GetSequencePointCount, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 22c45ff77c030dcbe87e5aa53284b2cace9849ab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759482"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="4b794-102">ISymUnmanagedMethod::GetSequencePointCount, méthode</span><span class="sxs-lookup"><span data-stu-id="4b794-102">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>
<span data-ttu-id="4b794-103">Obtient le nombre de points de séquence au sein de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="4b794-103">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b794-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b794-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b794-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4b794-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="4b794-106">[out] Un pointeur vers un `ULONG32` qui reçoit la taille de la mémoire tampon requise pour contenir les points de séquence.</span><span class="sxs-lookup"><span data-stu-id="4b794-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b794-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4b794-107">Return Value</span></span>  
 <span data-ttu-id="4b794-108">S_OK si la méthode réussit ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4b794-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b794-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4b794-109">Requirements</span></span>  
 <span data-ttu-id="4b794-110">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4b794-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b794-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b794-111">See also</span></span>

- [<span data-ttu-id="4b794-112">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="4b794-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
