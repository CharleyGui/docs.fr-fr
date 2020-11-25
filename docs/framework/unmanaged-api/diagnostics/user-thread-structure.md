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
ms.openlocfilehash: 409651aa69e957418ad46f61e1bd57add0eb10a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722893"
---
# <a name="user_thread-structure"></a><span data-ttu-id="e2617-102">USER_THREAD, structure</span><span class="sxs-lookup"><span data-stu-id="e2617-102">USER_THREAD Structure</span></span>

<span data-ttu-id="e2617-103">Fournit des informations à un débogueur à propos d’un thread.</span><span class="sxs-lookup"><span data-stu-id="e2617-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="e2617-104">Pour plus d’informations, consultez la méthode [INotifySource2 :: SetNotifyFilter,](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e2617-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2617-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2617-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="e2617-106">Membres</span><span class="sxs-lookup"><span data-stu-id="e2617-106">Members</span></span>  
  
|<span data-ttu-id="e2617-107">Membre</span><span class="sxs-lookup"><span data-stu-id="e2617-107">Member</span></span>|<span data-ttu-id="e2617-108">Description</span><span class="sxs-lookup"><span data-stu-id="e2617-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="e2617-109">Adresse de la mémoire tampon de thread.</span><span class="sxs-lookup"><span data-stu-id="e2617-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="e2617-110">Longueur de la mémoire tampon de thread, en octets.</span><span class="sxs-lookup"><span data-stu-id="e2617-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="e2617-111">ID de thread.</span><span class="sxs-lookup"><span data-stu-id="e2617-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2617-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e2617-112">Requirements</span></span>  

 <span data-ttu-id="e2617-113">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="e2617-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2617-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2617-114">See also</span></span>

- [<span data-ttu-id="e2617-115">SetNotifyFilter, méthode</span><span class="sxs-lookup"><span data-stu-id="e2617-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="e2617-116">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="e2617-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
