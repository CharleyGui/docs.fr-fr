---
title: ISymUnmanagedScope::GetEndOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 4d6bd239a15bd196f840007af120cb062499f4c9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614849"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="72192-102">ISymUnmanagedScope::GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="72192-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="72192-103">Obtient l’offset de fin pour cette portée.</span><span class="sxs-lookup"><span data-stu-id="72192-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72192-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72192-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72192-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="72192-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="72192-106">à Pointeur vers un `ULONG32` qui reçoit le décalage de fin.</span><span class="sxs-lookup"><span data-stu-id="72192-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72192-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="72192-107">Return Value</span></span>  
 <span data-ttu-id="72192-108">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="72192-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72192-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="72192-109">Requirements</span></span>  
 <span data-ttu-id="72192-110">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="72192-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72192-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72192-111">See also</span></span>

- [<span data-ttu-id="72192-112">ISymUnmanagedScope, interface</span><span class="sxs-lookup"><span data-stu-id="72192-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="72192-113">GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="72192-113">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)
