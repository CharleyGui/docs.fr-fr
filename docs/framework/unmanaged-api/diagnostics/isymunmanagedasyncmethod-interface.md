---
title: ISymUnmanagedAsyncMethod, interface
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 448ed719331469dce8f15500f14d5c1b0707ecf7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504450"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="af612-102">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="af612-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="af612-103">Cette interface est le complément de lecture de l' [interface ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="af612-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af612-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af612-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="af612-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="af612-105">Methods</span></span>  
 <span data-ttu-id="af612-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="af612-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="af612-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="af612-107">Method</span></span>|<span data-ttu-id="af612-108">Description</span><span class="sxs-lookup"><span data-stu-id="af612-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af612-109">GetAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="af612-109">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="af612-110">Consultez [méthode defineasyncstepinfo,](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="af612-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="af612-111">GetAsyncStepInfoCount, méthode</span><span class="sxs-lookup"><span data-stu-id="af612-111">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="af612-112">Consultez [méthode defineasyncstepinfo,](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="af612-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="af612-113">GetCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="af612-113">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="af612-114">Consultez [méthode definecatchhandleriloffset,](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="af612-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="af612-115">GetKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="af612-115">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="af612-116">Consultez [méthode definekickoffmethod,](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="af612-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="af612-117">HasCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="af612-117">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="af612-118">Consultez [méthode definecatchhandleriloffset,](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="af612-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="af612-119">IsAsyncMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="af612-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="af612-120">Vérifie si la méthode contient des informations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="af612-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="af612-121">Si cette méthode retourne `FALSE` , il n’est pas valide d’appeler d’autres méthodes dans cette interface.</span><span class="sxs-lookup"><span data-stu-id="af612-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="af612-122">Ils seront tous retournés `E_UNEXPECTED` dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="af612-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af612-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="af612-123">Requirements</span></span>  
 <span data-ttu-id="af612-124">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="af612-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af612-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af612-125">See also</span></span>

- [<span data-ttu-id="af612-126">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="af612-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
