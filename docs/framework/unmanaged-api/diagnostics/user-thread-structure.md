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
ms.openlocfilehash: 5144feab742bc5dac36563d701d81a699d0bb2f3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609441"
---
# <a name="user_thread-structure"></a><span data-ttu-id="77888-102">USER_THREAD, structure</span><span class="sxs-lookup"><span data-stu-id="77888-102">USER_THREAD Structure</span></span>
<span data-ttu-id="77888-103">Fournit des informations à un débogueur à propos d’un thread.</span><span class="sxs-lookup"><span data-stu-id="77888-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="77888-104">Pour plus d’informations, consultez la méthode [INotifySource2 :: SetNotifyFilter,](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="77888-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77888-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77888-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="77888-106">Membres</span><span class="sxs-lookup"><span data-stu-id="77888-106">Members</span></span>  
  
|<span data-ttu-id="77888-107">Membre</span><span class="sxs-lookup"><span data-stu-id="77888-107">Member</span></span>|<span data-ttu-id="77888-108">Description</span><span class="sxs-lookup"><span data-stu-id="77888-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="77888-109">Adresse de la mémoire tampon de thread.</span><span class="sxs-lookup"><span data-stu-id="77888-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="77888-110">Longueur de la mémoire tampon de thread, en octets.</span><span class="sxs-lookup"><span data-stu-id="77888-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="77888-111">ID de thread.</span><span class="sxs-lookup"><span data-stu-id="77888-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="77888-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="77888-112">Requirements</span></span>  
 <span data-ttu-id="77888-113">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="77888-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77888-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77888-114">See also</span></span>

- [<span data-ttu-id="77888-115">SetNotifyFilter, méthode</span><span class="sxs-lookup"><span data-stu-id="77888-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="77888-116">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="77888-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
