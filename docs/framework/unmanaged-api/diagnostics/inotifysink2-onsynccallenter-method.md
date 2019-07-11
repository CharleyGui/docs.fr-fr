---
title: INotifySink2::OnSyncCallEnter, méthode
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5fc8b3e6432475468f1012313c95ddd2e22e026
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736259"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="ca225-102">INotifySink2::OnSyncCallEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="ca225-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="ca225-103">Est appelé lors de la saisie d’un appel.</span><span class="sxs-lookup"><span data-stu-id="ca225-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca225-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca225-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca225-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca225-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="ca225-106">[in] ID de l’appel en cours de saisie.</span><span class="sxs-lookup"><span data-stu-id="ca225-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="ca225-107">Consultez [call_id, Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="ca225-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="ca225-108">[in] Mémoire tampon d’appel.</span><span class="sxs-lookup"><span data-stu-id="ca225-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="ca225-109">[in] Taille de la mémoire tampon de l’appel, en octets.</span><span class="sxs-lookup"><span data-stu-id="ca225-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca225-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ca225-110">Return Value</span></span>  
 <span data-ttu-id="ca225-111">S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="ca225-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca225-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ca225-112">Requirements</span></span>  
 <span data-ttu-id="ca225-113">**En-tête :** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="ca225-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca225-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca225-114">See also</span></span>

- [<span data-ttu-id="ca225-115">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="ca225-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="ca225-116">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="ca225-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="ca225-117">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="ca225-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
