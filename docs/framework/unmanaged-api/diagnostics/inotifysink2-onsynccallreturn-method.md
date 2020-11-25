---
title: INotifySink2::OnSyncCallReturn, méthode
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
ms.openlocfilehash: fe2db3df688f91ec6e1aadd8cc3bb43726e5c30f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719955"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="c8f61-102">INotifySink2::OnSyncCallReturn, méthode</span><span class="sxs-lookup"><span data-stu-id="c8f61-102">INotifySink2::OnSyncCallReturn Method</span></span>

<span data-ttu-id="c8f61-103">Est appelé quand un appel est retourné.</span><span class="sxs-lookup"><span data-stu-id="c8f61-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8f61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8f61-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8f61-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c8f61-105">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="c8f61-106">dans ID de l’appel retourné par.</span><span class="sxs-lookup"><span data-stu-id="c8f61-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="c8f61-107">Consultez [call_id structure](call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="c8f61-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="c8f61-108">dans Mémoire tampon d’appel.</span><span class="sxs-lookup"><span data-stu-id="c8f61-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="c8f61-109">dans Taille de la mémoire tampon d’appel, en octets.</span><span class="sxs-lookup"><span data-stu-id="c8f61-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8f61-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c8f61-110">Return Value</span></span>  

 <span data-ttu-id="c8f61-111">S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="c8f61-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8f61-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c8f61-112">Requirements</span></span>  

 <span data-ttu-id="c8f61-113">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="c8f61-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f61-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8f61-114">See also</span></span>

- [<span data-ttu-id="c8f61-115">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="c8f61-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="c8f61-116">INotifySource2, interface</span><span class="sxs-lookup"><span data-stu-id="c8f61-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="c8f61-117">INotifyConnection2, interface</span><span class="sxs-lookup"><span data-stu-id="c8f61-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
