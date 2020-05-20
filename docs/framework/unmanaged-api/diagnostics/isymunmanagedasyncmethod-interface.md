---
title: ISymUnmanagedAsyncMethod, interface
ms.date: 03/30/2017
ms.assetid: f2de5224-fd91-45de-9e58-bc600c6d22f1
ms.openlocfilehash: fef1af75587b889afad9cb5b93d0cd722294006b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441810"
---
# <a name="isymunmanagedasyncmethod-interface"></a><span data-ttu-id="e4502-102">ISymUnmanagedAsyncMethod, interface</span><span class="sxs-lookup"><span data-stu-id="e4502-102">ISymUnmanagedAsyncMethod Interface</span></span>
<span data-ttu-id="e4502-103">Cette interface est le complément de lecture de l' [interface ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e4502-103">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4502-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4502-104">Syntax</span></span>  
  
```idl  
[object,uuid(B20D55B3-532E-4906-87E7-25BD5734ABD2),pointer_default(unique)]interface ISymUnmanagedAsyncMethod : IUnknown  
```  
  
## <a name="methods"></a><span data-ttu-id="e4502-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e4502-105">Methods</span></span>  
 <span data-ttu-id="e4502-106">Cette interface contient les méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e4502-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="e4502-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="e4502-107">Method</span></span>|<span data-ttu-id="e4502-108">Description</span><span class="sxs-lookup"><span data-stu-id="e4502-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4502-109">GetAsyncStepInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="e4502-109">GetAsyncStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfo-method.md)|<span data-ttu-id="e4502-110">Consultez [méthode defineasyncstepinfo,](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4502-110">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="e4502-111">GetAsyncStepInfoCount, méthode</span><span class="sxs-lookup"><span data-stu-id="e4502-111">GetAsyncStepInfoCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getasyncstepinfocount-method.md)|<span data-ttu-id="e4502-112">Consultez [méthode defineasyncstepinfo,](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4502-112">See [DefineAsyncStepInfo Method](isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md).</span></span>|  
|[<span data-ttu-id="e4502-113">GetCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="e4502-113">GetCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getcatchhandleriloffset-method.md)|<span data-ttu-id="e4502-114">Consultez [méthode definecatchhandleriloffset,](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4502-114">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="e4502-115">GetKickoffMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="e4502-115">GetKickoffMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-getkickoffmethod-method.md)|<span data-ttu-id="e4502-116">Consultez [méthode definekickoffmethod,](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4502-116">See [DefineKickoffMethod Method](isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md).</span></span>|  
|[<span data-ttu-id="e4502-117">HasCatchHandlerILOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="e4502-117">HasCatchHandlerILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-hascatchhandleriloffset-method.md)|<span data-ttu-id="e4502-118">Consultez [méthode definecatchhandleriloffset,](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span><span class="sxs-lookup"><span data-stu-id="e4502-118">See [DefineCatchHandlerILOffset Method](isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).</span></span>|  
|[<span data-ttu-id="e4502-119">IsAsyncMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="e4502-119">IsAsyncMethod Method</span></span>](isymunmanagedasyncmethod-isasyncmethod-method.md)|<span data-ttu-id="e4502-120">Vérifie si la méthode contient des informations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="e4502-120">Checks if the method has async information or not.</span></span><br /><br /> <span data-ttu-id="e4502-121">Si cette méthode retourne `FALSE` , il n’est pas valide d’appeler d’autres méthodes dans cette interface.</span><span class="sxs-lookup"><span data-stu-id="e4502-121">If this method returns `FALSE` then it is invalid to call any other methods in this interface.</span></span> <span data-ttu-id="e4502-122">Ils seront tous retournés `E_UNEXPECTED` dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="e4502-122">They will all return `E_UNEXPECTED` in this case.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4502-123">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="e4502-123">Requirements</span></span>  
 <span data-ttu-id="e4502-124">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e4502-124">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4502-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4502-125">See also</span></span>

- [<span data-ttu-id="e4502-126">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="e4502-126">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
