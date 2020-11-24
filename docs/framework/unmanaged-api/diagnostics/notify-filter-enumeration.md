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
ms.openlocfilehash: 365bc0dc73b04d3afd171c40f336432f77552b6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690952"
---
# <a name="notify_filter-enumeration"></a><span data-ttu-id="a08e6-102">NOTIFY_FILTER, énumération</span><span class="sxs-lookup"><span data-stu-id="a08e6-102">NOTIFY_FILTER Enumeration</span></span>

<span data-ttu-id="a08e6-103">Identifie les rappels pour les fonctions du débogueur.</span><span class="sxs-lookup"><span data-stu-id="a08e6-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="a08e6-104">Pour plus d’informations, consultez la méthode [INotifySource2 :: SetNotifyFilter,](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a08e6-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a08e6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a08e6-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a08e6-106">Membres</span><span class="sxs-lookup"><span data-stu-id="a08e6-106">Members</span></span>  
  
|<span data-ttu-id="a08e6-107">Membre</span><span class="sxs-lookup"><span data-stu-id="a08e6-107">Member</span></span>|<span data-ttu-id="a08e6-108">Description</span><span class="sxs-lookup"><span data-stu-id="a08e6-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="a08e6-109">Indique que la méthode [INotifySink2 :: OnSyncCallOut,](inotifysink2-onsynccallout-method.md) doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="a08e6-109">Indicates that the [INotifySink2::OnSyncCallOut](inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="a08e6-110">Indique que la méthode [INotifySink2 :: OnSyncCallEnter,](inotifysink2-onsynccallenter-method.md) doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="a08e6-110">Indicates that the [INotifySink2::OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="a08e6-111">Indique que la méthode [INotifySink2 :: OnSyncCallExit,](inotifysink2-onsynccallexit-method.md) doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="a08e6-111">Indicates that the [INotifySink2::OnSyncCallExit](inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="a08e6-112">Indique que la méthode [INotifySink2 :: OnSyncCallReturn,](inotifysink2-onsynccallreturn-method.md) doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="a08e6-112">Indicates that the [INotifySink2::OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="a08e6-113">Indique que toutes les méthodes [INotifySink2](inotifysink2-interface.md) doivent être appelées.</span><span class="sxs-lookup"><span data-stu-id="a08e6-113">Indicates that all of the [INotifySink2](inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="a08e6-114">Active toutes les notifications existantes et futures.</span><span class="sxs-lookup"><span data-stu-id="a08e6-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="a08e6-115">Indique qu’aucune méthode de notification ne doit être appelée.</span><span class="sxs-lookup"><span data-stu-id="a08e6-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a08e6-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a08e6-116">Requirements</span></span>  

 <span data-ttu-id="a08e6-117">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="a08e6-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a08e6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a08e6-118">See also</span></span>

- [<span data-ttu-id="a08e6-119">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="a08e6-119">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
