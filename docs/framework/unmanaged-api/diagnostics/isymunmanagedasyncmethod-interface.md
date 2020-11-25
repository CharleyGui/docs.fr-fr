---
title: ISymUnmanagedAsyncMethod, interface
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 02b1866f2b9e89cdc8c8795f399ecc0c733c7202
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707163"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="dfe17-102">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="dfe17-102">ISymUnmanagedAsyncMethod Interface</span></span>

<span data-ttu-id="dfe17-103">Cette interface est le complément de lecture de l' [interface ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="dfe17-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfe17-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="dfe17-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="dfe17-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="dfe17-105">Methods</span></span>  

 <span data-ttu-id="dfe17-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="dfe17-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="dfe17-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="dfe17-107">Method</span></span>|<span data-ttu-id="dfe17-108">Description</span><span class="sxs-lookup"><span data-stu-id="dfe17-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dfe17-109">GetAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="dfe17-109">GetAsyncStepInfo Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="dfe17-110">Consultez [méthode defineasyncstepinfo,](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="dfe17-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="dfe17-111">GetAsyncStepInfoCount, méthode</span><span class="sxs-lookup"><span data-stu-id="dfe17-111">GetAsyncStepInfoCount Method</span></span>](isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="dfe17-112">Consultez [méthode defineasyncstepinfo,](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="dfe17-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="dfe17-113">GetCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="dfe17-113">GetCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="dfe17-114">Consultez [méthode definecatchhandleriloffset,](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="dfe17-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="dfe17-115">GetKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="dfe17-115">GetKickoffMethod Method</span></span>](isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="dfe17-116">Consultez [méthode definekickoffmethod,](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="dfe17-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="dfe17-117">HasCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="dfe17-117">HasCatchHandlerILOffset Method</span></span>](isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="dfe17-118">Consultez [méthode definecatchhandleriloffset,](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="dfe17-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="dfe17-119">IsAsyncMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="dfe17-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="dfe17-120">Vérifie si la méthode contient des informations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="dfe17-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="dfe17-121">Si cette méthode retourne `FALSE` , il n’est pas valide d’appeler d’autres méthodes dans cette interface.</span><span class="sxs-lookup"><span data-stu-id="dfe17-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="dfe17-122">Ils seront tous retournés `E_UNEXPECTED` dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="dfe17-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dfe17-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dfe17-123">Requirements</span></span>  

 <span data-ttu-id="dfe17-124">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dfe17-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfe17-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfe17-125">See also</span></span>

- [<span data-ttu-id="dfe17-126">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="dfe17-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
