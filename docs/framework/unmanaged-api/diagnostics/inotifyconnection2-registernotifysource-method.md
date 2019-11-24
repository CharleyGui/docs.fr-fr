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
ms.openlocfilehash: 76514cfbd2e533f04c5139dbaef4429c12463106
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445475"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="c6ec8-102">INotifyConnection2::RegisterNotifySource, méthode</span><span class="sxs-lookup"><span data-stu-id="c6ec8-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="c6ec8-103">Installs a specified notification source.</span><span class="sxs-lookup"><span data-stu-id="c6ec8-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ec8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6ec8-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6ec8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c6ec8-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="c6ec8-106">[in] Specifies the object to be used as the notification source.</span><span class="sxs-lookup"><span data-stu-id="c6ec8-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="c6ec8-107">[out] Receives the object to be used as the notification sink.</span><span class="sxs-lookup"><span data-stu-id="c6ec8-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6ec8-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c6ec8-108">Return Value</span></span>  
 <span data-ttu-id="c6ec8-109">S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="c6ec8-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6ec8-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="c6ec8-110">Requirements</span></span>  
 <span data-ttu-id="c6ec8-111">**Header:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="c6ec8-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ec8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6ec8-112">See also</span></span>

- [<span data-ttu-id="c6ec8-113">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="c6ec8-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="c6ec8-114">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="c6ec8-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="c6ec8-115">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="c6ec8-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="c6ec8-116">UnregisterNotifySource, méthode</span><span class="sxs-lookup"><span data-stu-id="c6ec8-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
