---
title: ISymUnmanagedAsyncMethod::IsAsyncMethod, méthode
ms.date: 03/30/2017
ms.assetid: 670a7653-dac6-4171-98ee-d669e3adf4b2
ms.openlocfilehash: 0ea4c21e9e6a49d7bbbad5e1853598c440cd6410
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129209"
---
# <a name="isymunmanagedasyncmethodisasyncmethod-method"></a><span data-ttu-id="fe2ad-102">ISymUnmanagedAsyncMethod::IsAsyncMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="fe2ad-102">ISymUnmanagedAsyncMethod::IsAsyncMethod Method</span></span>
<span data-ttu-id="fe2ad-103">Vérifie si la méthode contient des informations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="fe2ad-103">Checks if the method has async information or not.</span></span>  
  
 <span data-ttu-id="fe2ad-104">Si cette méthode retourne `FALSE`, il n’est pas valide d’appeler d’autres méthodes dans cette interface.</span><span class="sxs-lookup"><span data-stu-id="fe2ad-104">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="fe2ad-105">Elles retournent toutes `E_UNEXPECTED` dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="fe2ad-105">They will all return `E_UNEXPECTED` in this case.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe2ad-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe2ad-106">Syntax</span></span>  
  
```idl  
HRESULT IsAsyncMethod(    [out, retval] BOOL* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe2ad-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fe2ad-107">Parameters</span></span>  
  
|<span data-ttu-id="fe2ad-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="fe2ad-108">Parameter</span></span>|<span data-ttu-id="fe2ad-109">Description</span><span class="sxs-lookup"><span data-stu-id="fe2ad-109">Description</span></span>|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a><span data-ttu-id="fe2ad-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fe2ad-110">Return Value</span></span>  
 <span data-ttu-id="fe2ad-111">Retourne `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="fe2ad-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe2ad-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="fe2ad-112">Requirements</span></span>  
 <span data-ttu-id="fe2ad-113">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fe2ad-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe2ad-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe2ad-114">See also</span></span>

- [<span data-ttu-id="fe2ad-115">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="fe2ad-115">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
