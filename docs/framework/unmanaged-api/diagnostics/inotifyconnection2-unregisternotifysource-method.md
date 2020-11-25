---
title: INotifyConnection2::UnregisterNotifySource, méthode
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: 90220c2bfea683ff0472473e180c9e11ea568672
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720033"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="05391-102">INotifyConnection2::UnregisterNotifySource, méthode</span><span class="sxs-lookup"><span data-stu-id="05391-102">INotifyConnection2::UnregisterNotifySource Method</span></span>

<span data-ttu-id="05391-103">Supprime de la connexion un objet source de notification spécifié.</span><span class="sxs-lookup"><span data-stu-id="05391-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05391-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05391-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05391-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05391-105">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="05391-106">dans Objet de notification dont l’inscription doit être annulée.</span><span class="sxs-lookup"><span data-stu-id="05391-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05391-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="05391-107">Return Value</span></span>  

 <span data-ttu-id="05391-108">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="05391-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05391-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05391-109">Requirements</span></span>  

 <span data-ttu-id="05391-110">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="05391-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05391-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05391-111">See also</span></span>

- [<span data-ttu-id="05391-112">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="05391-112">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="05391-113">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="05391-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="05391-114">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="05391-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="05391-115">RegisterNotifySource, méthode</span><span class="sxs-lookup"><span data-stu-id="05391-115">RegisterNotifySource Method</span></span>](inotifyconnection2-registernotifysource-method.md)
