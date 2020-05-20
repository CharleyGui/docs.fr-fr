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
ms.openlocfilehash: b20e18d5f4314a0ab1442ac7bd5c6514e4db85d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609480"
---
# <a name="notify_filter-enumeration"></a><span data-ttu-id="22496-102">NOTIFY_FILTER, énumération</span><span class="sxs-lookup"><span data-stu-id="22496-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="22496-103">Identifie les rappels pour les fonctions du débogueur.</span><span class="sxs-lookup"><span data-stu-id="22496-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="22496-104">Pour plus d’informations, consultez la méthode [INotifySource2 :: SetNotifyFilter,](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="22496-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22496-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22496-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="22496-106">Membres</span><span class="sxs-lookup"><span data-stu-id="22496-106">Members</span></span>  
  
|<span data-ttu-id="22496-107">Membre</span><span class="sxs-lookup"><span data-stu-id="22496-107">Member</span></span>|<span data-ttu-id="22496-108">Description</span><span class="sxs-lookup"><span data-stu-id="22496-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="22496-109">Indique que la méthode [INotifySink2 :: OnSyncCallOut,](inotifysink2-onsynccallout-method.md) doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="22496-109">Indicates that the [INotifySink2::OnSyncCallOut](inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="22496-110">Indique que la méthode [INotifySink2 :: OnSyncCallEnter,](inotifysink2-onsynccallenter-method.md) doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="22496-110">Indicates that the [INotifySink2::OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="22496-111">Indique que la méthode [INotifySink2 :: OnSyncCallExit,](inotifysink2-onsynccallexit-method.md) doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="22496-111">Indicates that the [INotifySink2::OnSyncCallExit](inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="22496-112">Indique que la méthode [INotifySink2 :: OnSyncCallReturn,](inotifysink2-onsynccallreturn-method.md) doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="22496-112">Indicates that the [INotifySink2::OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="22496-113">Indique que toutes les méthodes [INotifySink2](inotifysink2-interface.md) doivent être appelées.</span><span class="sxs-lookup"><span data-stu-id="22496-113">Indicates that all of the [INotifySink2](inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="22496-114">Active toutes les notifications existantes et futures.</span><span class="sxs-lookup"><span data-stu-id="22496-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="22496-115">Indique qu’aucune méthode de notification ne doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="22496-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="22496-116">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="22496-116">Requirements</span></span>  
 <span data-ttu-id="22496-117">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="22496-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22496-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22496-118">See also</span></span>

- [<span data-ttu-id="22496-119">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="22496-119">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
