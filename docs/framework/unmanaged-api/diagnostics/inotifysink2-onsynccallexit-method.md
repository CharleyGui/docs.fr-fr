---
title: INotifySink2::OnSyncCallExit, méthode
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallExit
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallExit
helpviewer_keywords:
- INotifySink2::OnSyncCallExit method [.NET Framework debugging]
- OnSyncCallExit method [.NET Framework debugging]
ms.assetid: d9d7600e-a8f5-443a-96de-67d26e130f2d
topic_type:
- apiref
ms.openlocfilehash: 03b8afc1276dae6244bcf12bd0bc78c2fa5380bb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448682"
---
# <a name="inotifysink2onsynccallexit-method"></a><span data-ttu-id="76fb4-102">INotifySink2::OnSyncCallExit, méthode</span><span class="sxs-lookup"><span data-stu-id="76fb4-102">INotifySink2::OnSyncCallExit Method</span></span>
<span data-ttu-id="76fb4-103">Est appelé lors de la sortie d’un appel.</span><span class="sxs-lookup"><span data-stu-id="76fb4-103">Gets invoked when exiting a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76fb4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76fb4-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallExit  
(  
    [in]  CALL_ID   in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*    out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76fb4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="76fb4-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="76fb4-106">dans ID de l’appel en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="76fb4-106">[in] ID of the call being exited.</span></span> <span data-ttu-id="76fb4-107">Consultez [call_id structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="76fb4-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="76fb4-108">à Mémoire tampon d’appel.</span><span class="sxs-lookup"><span data-stu-id="76fb4-108">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="76fb4-109">à Taille de la mémoire tampon d’appel, en octets.</span><span class="sxs-lookup"><span data-stu-id="76fb4-109">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76fb4-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="76fb4-110">Return Value</span></span>  
 <span data-ttu-id="76fb4-111">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="76fb4-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76fb4-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="76fb4-112">Requirements</span></span>  
 <span data-ttu-id="76fb4-113">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="76fb4-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76fb4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76fb4-114">See also</span></span>

- [<span data-ttu-id="76fb4-115">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="76fb4-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="76fb4-116">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="76fb4-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="76fb4-117">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="76fb4-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
