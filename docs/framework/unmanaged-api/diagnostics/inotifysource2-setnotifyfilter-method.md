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
ms.openlocfilehash: 7ba9f68e102696da107b5cb782c76cb55ed95ee6
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441966"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="fd68d-102">INotifySource2::SetNotifyFilter, méthode</span><span class="sxs-lookup"><span data-stu-id="fd68d-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="fd68d-103">Affecte un filtre de notification à utiliser avec cette source.</span><span class="sxs-lookup"><span data-stu-id="fd68d-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd68d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd68d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd68d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fd68d-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="fd68d-106">dans Combinaison d’opérations de bits des valeurs d’énumération [notify_filter](notify-filter-enumeration.md) qui identifient les rappels pour l’API du débogueur.</span><span class="sxs-lookup"><span data-stu-id="fd68d-106">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="fd68d-107">dans Pointeur vers une structure [USER_THREAD](user-thread-structure.md) qui identifie des threads pour l’API du débogueur.</span><span class="sxs-lookup"><span data-stu-id="fd68d-107">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd68d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="fd68d-108">Return Value</span></span>  
 <span data-ttu-id="fd68d-109">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="fd68d-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd68d-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="fd68d-110">Requirements</span></span>  
 <span data-ttu-id="fd68d-111">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="fd68d-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd68d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd68d-112">See also</span></span>

- [<span data-ttu-id="fd68d-113">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="fd68d-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="fd68d-114">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="fd68d-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="fd68d-115">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="fd68d-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
