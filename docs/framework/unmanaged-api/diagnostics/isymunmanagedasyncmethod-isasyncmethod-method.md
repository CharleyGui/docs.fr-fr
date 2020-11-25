---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod, méthode
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: af02aba1a0d390c103e8c6108f90b93fe2a98ff3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707150"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="9e3e1-102">ISymUnmanagedAsyncMethod::IsAsyncMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="9e3e1-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>

<span data-ttu-id="9e3e1-103">Vérifie si la méthode contient des informations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="9e3e1-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="9e3e1-104">Si cette méthode retourne `FALSE` , il n’est pas valide d’appeler d’autres méthodes dans cette interface.</span><span class="sxs-lookup"><span data-stu-id="9e3e1-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="9e3e1-105">Ils seront tous retournés `E_UNEXPECTED` dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="9e3e1-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e3e1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e3e1-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e3e1-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9e3e1-107">Parameters</span></span>  
  
|<span data-ttu-id="9e3e1-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="9e3e1-108">Parameter</span></span>|<span data-ttu-id="9e3e1-109">Description</span><span class="sxs-lookup"><span data-stu-id="9e3e1-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="9e3e1-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9e3e1-110">Return Value</span></span>  

 <span data-ttu-id="9e3e1-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="9e3e1-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e3e1-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9e3e1-112">Requirements</span></span>  

 <span data-ttu-id="9e3e1-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9e3e1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e3e1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e3e1-114">See also</span></span>

- [<span data-ttu-id="9e3e1-115">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="9e3e1-115">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
