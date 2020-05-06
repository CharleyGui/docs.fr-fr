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
ms.openlocfilehash: 2c41e7db32ee8557a6c03217b95fd5b040655c70
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860926"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="30002-102">Structure CoreClrDebugRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="30002-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="30002-103">Représente une instance du Common Language Runtime (CLR) qui est chargée dans un processus sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="30002-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30002-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30002-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="30002-105">Membres</span><span class="sxs-lookup"><span data-stu-id="30002-105">Members</span></span>  
  
|<span data-ttu-id="30002-106">Membre</span><span class="sxs-lookup"><span data-stu-id="30002-106">Member</span></span>|<span data-ttu-id="30002-107">Description</span><span class="sxs-lookup"><span data-stu-id="30002-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="30002-108">Identificateur de runtime affecté par le proxy de débogage distant en cours d'exécution sur l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="30002-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30002-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="30002-109">Requirements</span></span>  
 <span data-ttu-id="30002-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30002-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30002-111">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="30002-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="30002-112">**Bibliothèque :** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="30002-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="30002-113">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="30002-113">**.NET Framework Versions:** 3.5 SP1</span></span>
