---
title: USER_THREAD, structure
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: 51db7a2b6464b562e09ce061991898a8d604ead1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437970"
---
# <a name="user_thread-structure"></a><span data-ttu-id="9933a-102">USER_THREAD, structure</span><span class="sxs-lookup"><span data-stu-id="9933a-102">USER_THREAD Structure</span></span>
<span data-ttu-id="9933a-103">Provides information to a debugger about a thread.</span><span class="sxs-lookup"><span data-stu-id="9933a-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="9933a-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="9933a-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9933a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9933a-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="9933a-106">Membres</span><span class="sxs-lookup"><span data-stu-id="9933a-106">Members</span></span>  
  
|<span data-ttu-id="9933a-107">Membre</span><span class="sxs-lookup"><span data-stu-id="9933a-107">Member</span></span>|<span data-ttu-id="9933a-108">Description</span><span class="sxs-lookup"><span data-stu-id="9933a-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="9933a-109">Address of thread buffer.</span><span class="sxs-lookup"><span data-stu-id="9933a-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="9933a-110">Length of thread buffer, in bytes.</span><span class="sxs-lookup"><span data-stu-id="9933a-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="9933a-111">Thread ID.</span><span class="sxs-lookup"><span data-stu-id="9933a-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9933a-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="9933a-112">Requirements</span></span>  
 <span data-ttu-id="9933a-113">**Header:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="9933a-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9933a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9933a-114">See also</span></span>

- [<span data-ttu-id="9933a-115">SetNotifyFilter, méthode</span><span class="sxs-lookup"><span data-stu-id="9933a-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="9933a-116">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="9933a-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
