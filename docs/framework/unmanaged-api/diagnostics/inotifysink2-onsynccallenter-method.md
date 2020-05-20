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
ms.openlocfilehash: 85f00698f42f120b209cca14f293a58ae4c65f6f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442031"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="0ff86-102">INotifySink2::OnSyncCallEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="0ff86-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="0ff86-103">Est appelé lors de l’entrée d’un appel.</span><span class="sxs-lookup"><span data-stu-id="0ff86-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ff86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ff86-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ff86-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0ff86-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="0ff86-106">dans ID de l’appel entré.</span><span class="sxs-lookup"><span data-stu-id="0ff86-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="0ff86-107">Consultez [call_id structure](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="0ff86-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="0ff86-108">dans Mémoire tampon d’appel.</span><span class="sxs-lookup"><span data-stu-id="0ff86-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="0ff86-109">dans Taille de la mémoire tampon d’appel, en octets.</span><span class="sxs-lookup"><span data-stu-id="0ff86-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ff86-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0ff86-110">Return Value</span></span>  
 <span data-ttu-id="0ff86-111">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="0ff86-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ff86-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="0ff86-112">Requirements</span></span>  
 <span data-ttu-id="0ff86-113">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="0ff86-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff86-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ff86-114">See also</span></span>

- [<span data-ttu-id="0ff86-115">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="0ff86-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="0ff86-116">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="0ff86-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="0ff86-117">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="0ff86-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
