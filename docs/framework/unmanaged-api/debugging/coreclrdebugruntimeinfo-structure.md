---
title: Structure CoreClrDebugRuntimeInfo
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b58832e110f67a54d3bd57a7284b2e26e43d6bf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739409"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="053dd-102">Structure CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="053dd-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="053dd-103">Représente une instance du Common Language Runtime (CLR) qui est chargée dans un processus sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="053dd-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="053dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="053dd-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="053dd-105">Membres</span><span class="sxs-lookup"><span data-stu-id="053dd-105">Members</span></span>  
  
|<span data-ttu-id="053dd-106">Membre</span><span class="sxs-lookup"><span data-stu-id="053dd-106">Member</span></span>|<span data-ttu-id="053dd-107">Description</span><span class="sxs-lookup"><span data-stu-id="053dd-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="053dd-108">Identificateur de runtime affecté par le proxy de débogage distant en cours d'exécution sur l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="053dd-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="053dd-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="053dd-109">Requirements</span></span>  
 <span data-ttu-id="053dd-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="053dd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="053dd-111">**En-tête :** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="053dd-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="053dd-112">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="053dd-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="053dd-113">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="053dd-113">**.NET Framework Versions:** 3.5 SP1</span></span>
