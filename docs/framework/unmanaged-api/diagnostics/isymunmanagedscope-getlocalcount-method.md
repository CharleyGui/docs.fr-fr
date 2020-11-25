---
title: ISymUnmanagedScope::GetLocalCount, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 07c41e9d80b1703e86ae06525d64bf166ef2cf8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717550"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="1476e-102">ISymUnmanagedScope::GetLocalCount, méthode</span><span class="sxs-lookup"><span data-stu-id="1476e-102">ISymUnmanagedScope::GetLocalCount Method</span></span>

<span data-ttu-id="1476e-103">Obtient le nombre de variables locales définies dans cette portée.</span><span class="sxs-lookup"><span data-stu-id="1476e-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1476e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1476e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1476e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1476e-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="1476e-106">à Pointeur vers un `ULONG32` qui reçoit le nombre de variables locales.</span><span class="sxs-lookup"><span data-stu-id="1476e-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1476e-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="1476e-107">Return Value</span></span>  

 <span data-ttu-id="1476e-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="1476e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1476e-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1476e-109">Requirements</span></span>  

 <span data-ttu-id="1476e-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1476e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1476e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1476e-111">See also</span></span>

- [<span data-ttu-id="1476e-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="1476e-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
