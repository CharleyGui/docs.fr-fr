---
title: INotifySource2::SetNotifyFilter, méthode
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 99bce831405d722f1f1ca0ae56e60f95f2d905e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719929"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="9a3fb-102">INotifySource2::SetNotifyFilter, méthode</span><span class="sxs-lookup"><span data-stu-id="9a3fb-102">INotifySource2::SetNotifyFilter Method</span></span>

<span data-ttu-id="9a3fb-103">Affecte un filtre de notification à utiliser avec cette source.</span><span class="sxs-lookup"><span data-stu-id="9a3fb-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a3fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a3fb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a3fb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a3fb-105">Parameters</span></span>  

 `in_NotifyFilter`  
 <span data-ttu-id="9a3fb-106">dans Combinaison d’opérations de bits des valeurs d’énumération [notify_filter](notify-filter-enumeration.md) qui identifient les rappels pour l’API du débogueur.</span><span class="sxs-lookup"><span data-stu-id="9a3fb-106">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="9a3fb-107">dans Pointeur vers une structure [USER_THREAD](user-thread-structure.md) qui identifie des threads pour l’API du débogueur.</span><span class="sxs-lookup"><span data-stu-id="9a3fb-107">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a3fb-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9a3fb-108">Return Value</span></span>  

 <span data-ttu-id="9a3fb-109">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="9a3fb-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a3fb-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9a3fb-110">Requirements</span></span>  

 <span data-ttu-id="9a3fb-111">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="9a3fb-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a3fb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a3fb-112">See also</span></span>

- [<span data-ttu-id="9a3fb-113">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="9a3fb-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="9a3fb-114">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="9a3fb-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="9a3fb-115">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="9a3fb-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
