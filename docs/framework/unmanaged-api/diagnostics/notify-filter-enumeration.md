---
title: NOTIFY_FILTER, énumération
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
ms.openlocfilehash: 92e40dbe8892d48dba1c54d9cd16faa409440b24
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438118"
---
# <a name="notify_filter-enumeration"></a><span data-ttu-id="92f8c-102">NOTIFY_FILTER, énumération</span><span class="sxs-lookup"><span data-stu-id="92f8c-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="92f8c-103">Identifies callbacks for debugger functions.</span><span class="sxs-lookup"><span data-stu-id="92f8c-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="92f8c-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="92f8c-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f8c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92f8c-105">Syntax</span></span>  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="92f8c-106">Membres</span><span class="sxs-lookup"><span data-stu-id="92f8c-106">Members</span></span>  
  
|<span data-ttu-id="92f8c-107">Membre</span><span class="sxs-lookup"><span data-stu-id="92f8c-107">Member</span></span>|<span data-ttu-id="92f8c-108">Description</span><span class="sxs-lookup"><span data-stu-id="92f8c-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="92f8c-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span><span class="sxs-lookup"><span data-stu-id="92f8c-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="92f8c-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span><span class="sxs-lookup"><span data-stu-id="92f8c-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="92f8c-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span><span class="sxs-lookup"><span data-stu-id="92f8c-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="92f8c-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span><span class="sxs-lookup"><span data-stu-id="92f8c-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="92f8c-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span><span class="sxs-lookup"><span data-stu-id="92f8c-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="92f8c-114">Activates all existing and future notifications.</span><span class="sxs-lookup"><span data-stu-id="92f8c-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="92f8c-115">Indicates that no notification methods should be invoked.</span><span class="sxs-lookup"><span data-stu-id="92f8c-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92f8c-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="92f8c-116">Requirements</span></span>  
 <span data-ttu-id="92f8c-117">**Header:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="92f8c-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f8c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92f8c-118">See also</span></span>

- [<span data-ttu-id="92f8c-119">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="92f8c-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
