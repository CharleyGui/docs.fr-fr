---
title: INotifyConnection2::RegisterNotifySource, méthode
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: 1286dd970e437af0a8b607ed050ab4838f73a41f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720046"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="badb0-102">INotifyConnection2::RegisterNotifySource, méthode</span><span class="sxs-lookup"><span data-stu-id="badb0-102">INotifyConnection2::RegisterNotifySource Method</span></span>

<span data-ttu-id="badb0-103">Installe une source de notification spécifiée.</span><span class="sxs-lookup"><span data-stu-id="badb0-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="badb0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="badb0-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="badb0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="badb0-105">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="badb0-106">dans Spécifie l’objet à utiliser comme source de notification.</span><span class="sxs-lookup"><span data-stu-id="badb0-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="badb0-107">à Reçoit l’objet à utiliser en tant que récepteur de notifications.</span><span class="sxs-lookup"><span data-stu-id="badb0-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="badb0-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="badb0-108">Return Value</span></span>  

 <span data-ttu-id="badb0-109">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="badb0-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="badb0-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="badb0-110">Requirements</span></span>  

 <span data-ttu-id="badb0-111">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="badb0-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="badb0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="badb0-112">See also</span></span>

- [<span data-ttu-id="badb0-113">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="badb0-113">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="badb0-114">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="badb0-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="badb0-115">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="badb0-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="badb0-116">UnregisterNotifySource, méthode</span><span class="sxs-lookup"><span data-stu-id="badb0-116">UnregisterNotifySource Method</span></span>](inotifyconnection2-unregisternotifysource-method.md)
