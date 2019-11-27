---
title: CALL_ID, structure
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
ms.openlocfilehash: 8c606f67766334800444f39b115d90f65ecca13d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448598"
---
# <a name="call_id-structure"></a><span data-ttu-id="3e4c9-102">CALL_ID, structure</span><span class="sxs-lookup"><span data-stu-id="3e4c9-102">CALL_ID Structure</span></span>
<span data-ttu-id="3e4c9-103">Fournit des informations à un débogueur sur une fonction qui est appelée.</span><span class="sxs-lookup"><span data-stu-id="3e4c9-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="3e4c9-104">Pour plus d’informations, consultez l’interface [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3e4c9-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e4c9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e4c9-105">Syntax</span></span>  
  
```cpp  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="3e4c9-106">Membres</span><span class="sxs-lookup"><span data-stu-id="3e4c9-106">Members</span></span>  
  
|<span data-ttu-id="3e4c9-107">Membre</span><span class="sxs-lookup"><span data-stu-id="3e4c9-107">Member</span></span>|<span data-ttu-id="3e4c9-108">Description</span><span class="sxs-lookup"><span data-stu-id="3e4c9-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="3e4c9-109">Identifie l’ordinateur qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="3e4c9-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="3e4c9-110">Identifie le processeur de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3e4c9-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="3e4c9-111">Identifie le thread qui exécute l’appel.</span><span class="sxs-lookup"><span data-stu-id="3e4c9-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="3e4c9-112">Spécifie l’adresse de la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="3e4c9-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="3e4c9-113">Spécifie l’adresse de l’appel.</span><span class="sxs-lookup"><span data-stu-id="3e4c9-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="3e4c9-114">Identifie l’ordinateur qui exécutera l’appel.</span><span class="sxs-lookup"><span data-stu-id="3e4c9-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e4c9-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3e4c9-115">Requirements</span></span>  
 <span data-ttu-id="3e4c9-116">**En-tête :** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="3e4c9-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e4c9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e4c9-117">See also</span></span>

- [<span data-ttu-id="3e4c9-118">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="3e4c9-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="3e4c9-119">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="3e4c9-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
