---
title: ISymUnmanagedAsyncMethod, interface
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: 0b8adba9dbffbdc47bb526cef9aad3ffa4b48065
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129225"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="ae2d2-102">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="ae2d2-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="ae2d2-103">Cette interface est le complément de lecture de l' [interface ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ae2d2-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae2d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae2d2-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="ae2d2-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ae2d2-105">Methods</span></span>  
 <span data-ttu-id="ae2d2-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ae2d2-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="ae2d2-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="ae2d2-107">Method</span></span>|<span data-ttu-id="ae2d2-108">Description</span><span class="sxs-lookup"><span data-stu-id="ae2d2-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae2d2-109">GetAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="ae2d2-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="ae2d2-110">Consultez [méthode defineasyncstepinfo,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="ae2d2-110">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="ae2d2-111">GetAsyncStepInfoCount, méthode</span><span class="sxs-lookup"><span data-stu-id="ae2d2-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="ae2d2-112">Consultez [méthode defineasyncstepinfo,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="ae2d2-112">See [DefineAsyncStepInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="ae2d2-113">GetCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="ae2d2-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="ae2d2-114">Consultez [méthode definecatchhandleriloffset,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="ae2d2-114">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="ae2d2-115">GetKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="ae2d2-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="ae2d2-116">Consultez [méthode definekickoffmethod,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="ae2d2-116">See [DefineKickoffMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="ae2d2-117">HasCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="ae2d2-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="ae2d2-118">Consultez [méthode definecatchhandleriloffset,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="ae2d2-118">See [DefineCatchHandlerILOffset Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="ae2d2-119">IsAsyncMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="ae2d2-119">IsAsyncMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="ae2d2-120">Vérifie si la méthode contient des informations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="ae2d2-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="ae2d2-121">Si cette méthode retourne `FALSE`, il n’est pas valide d’appeler d’autres méthodes dans cette interface.</span><span class="sxs-lookup"><span data-stu-id="ae2d2-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="ae2d2-122">Elles retournent toutes `E_UNEXPECTED` dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="ae2d2-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae2d2-123">spécifications</span><span class="sxs-lookup"><span data-stu-id="ae2d2-123">Requirements</span></span>  
 <span data-ttu-id="ae2d2-124">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ae2d2-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2d2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae2d2-125">See also</span></span>

- [<span data-ttu-id="ae2d2-126">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="ae2d2-126">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
