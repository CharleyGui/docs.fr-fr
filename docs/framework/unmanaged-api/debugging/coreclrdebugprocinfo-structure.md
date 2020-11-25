---
title: Structure CoreClrDebugProcInfo
ms.date: 03/30/2017
api_name:
- CoreClrDebugProcInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type:
- apiref
ms.openlocfilehash: 5996393fd1a0504f9c3d3f9f07aa0e3d886a0787
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719695"
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="509a5-102">Structure CoreClrDebugProcInfo</span><span class="sxs-lookup"><span data-stu-id="509a5-102">CoreClrDebugProcInfo Structure</span></span>

<span data-ttu-id="509a5-103">Représente un processus qui s'exécute sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="509a5-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="509a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="509a5-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="509a5-105">Membres</span><span class="sxs-lookup"><span data-stu-id="509a5-105">Members</span></span>  
  
|<span data-ttu-id="509a5-106">Membre</span><span class="sxs-lookup"><span data-stu-id="509a5-106">Member</span></span>|<span data-ttu-id="509a5-107">Description</span><span class="sxs-lookup"><span data-stu-id="509a5-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="509a5-108">Identificateur de processus affecté par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="509a5-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="509a5-109">Identificateur de processus affecté par le proxy de débogage distant en cours d'exécution sur l'ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="509a5-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="509a5-110">Cet identificateur est moins souvent recyclé que l'identificateur de système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="509a5-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="509a5-111">Ligne de commande du processus.</span><span class="sxs-lookup"><span data-stu-id="509a5-111">Command-line of the process.</span></span> <span data-ttu-id="509a5-112">Ce membre peut être tronqué.</span><span class="sxs-lookup"><span data-stu-id="509a5-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="509a5-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="509a5-113">Requirements</span></span>  

 <span data-ttu-id="509a5-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="509a5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="509a5-115">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="509a5-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="509a5-116">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="509a5-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="509a5-117">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="509a5-117">**.NET Framework Versions:** 3.5 SP1</span></span>
