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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2823c018ff22607052cb9a298f69dbd0c4fe2c23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769502"
---
# <a name="callid-structure"></a><span data-ttu-id="6afb5-102">CALL_ID, structure</span><span class="sxs-lookup"><span data-stu-id="6afb5-102">CALL_ID Structure</span></span>
<span data-ttu-id="6afb5-103">Fournit des informations à un débogueur sur une fonction qui est appelée.</span><span class="sxs-lookup"><span data-stu-id="6afb5-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="6afb5-104">Consultez le [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="6afb5-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6afb5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6afb5-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="6afb5-106">Membres</span><span class="sxs-lookup"><span data-stu-id="6afb5-106">Members</span></span>  
  
|<span data-ttu-id="6afb5-107">Membre</span><span class="sxs-lookup"><span data-stu-id="6afb5-107">Member</span></span>|<span data-ttu-id="6afb5-108">Description</span><span class="sxs-lookup"><span data-stu-id="6afb5-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="6afb5-109">Identifie l’ordinateur qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="6afb5-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="6afb5-110">Identifie le processeur de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6afb5-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="6afb5-111">Identifie le thread qui exécute l’appel.</span><span class="sxs-lookup"><span data-stu-id="6afb5-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="6afb5-112">Spécifie l’adresse de la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="6afb5-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="6afb5-113">Spécifie l’adresse de l’appel.</span><span class="sxs-lookup"><span data-stu-id="6afb5-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="6afb5-114">Identifie l’ordinateur qui exécute l’appel.</span><span class="sxs-lookup"><span data-stu-id="6afb5-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6afb5-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6afb5-115">Requirements</span></span>  
 <span data-ttu-id="6afb5-116">**En-tête :** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="6afb5-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6afb5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6afb5-117">See also</span></span>

- [<span data-ttu-id="6afb5-118">INotifySink2, interface</span><span class="sxs-lookup"><span data-stu-id="6afb5-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="6afb5-119">Structures du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="6afb5-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
