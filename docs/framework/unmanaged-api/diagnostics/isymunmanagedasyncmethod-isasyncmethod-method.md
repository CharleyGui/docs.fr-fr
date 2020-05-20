---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod, méthode
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 91b4c2688dadf12fa4a835a662622267d7831cf8
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441797"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="344eb-102">ISymUnmanagedAsyncMethod::IsAsyncMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="344eb-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="344eb-103">Vérifie si la méthode contient des informations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="344eb-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="344eb-104">Si cette méthode retourne `FALSE` , il n’est pas valide d’appeler d’autres méthodes dans cette interface.</span><span class="sxs-lookup"><span data-stu-id="344eb-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="344eb-105">Ils seront tous retournés `E_UNEXPECTED` dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="344eb-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="344eb-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="344eb-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="344eb-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="344eb-107">Parameters</span></span>  
  
|<span data-ttu-id="344eb-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="344eb-108">Parameter</span></span>|<span data-ttu-id="344eb-109">Description</span><span class="sxs-lookup"><span data-stu-id="344eb-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="344eb-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="344eb-110">Return Value</span></span>  
 <span data-ttu-id="344eb-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="344eb-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="344eb-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="344eb-112">Requirements</span></span>  
 <span data-ttu-id="344eb-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="344eb-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344eb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="344eb-114">See also</span></span>

- [<span data-ttu-id="344eb-115">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="344eb-115">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)
