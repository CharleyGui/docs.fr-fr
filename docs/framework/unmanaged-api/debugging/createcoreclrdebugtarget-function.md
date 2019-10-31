---
title: Fonction CreateCoreClrDebugTarget
ms.date: 03/30/2017
api_name:
- CreateCorClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type:
- apiref
ms.openlocfilehash: d52757f82a950c382c7c8f2162630eda7d7795e7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132094"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="ca6a1-102">Fonction CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="ca6a1-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="ca6a1-103">Crée une connexion à un proxy du débogueur qui s’exécute sur un ordinateur distant et retourne un objet [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) qui peut être utilisé pour interroger les processus en cours d’exécution et les runtimes chargés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="ca6a1-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca6a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca6a1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca6a1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca6a1-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="ca6a1-106">[in] Adresse IPv4 d'un ordinateur cible distant.</span><span class="sxs-lookup"><span data-stu-id="ca6a1-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="ca6a1-107">à Pointeur vers un pointeur vers un objet [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) qui sera créé.</span><span class="sxs-lookup"><span data-stu-id="ca6a1-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca6a1-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ca6a1-108">Return Value</span></span>  
 <span data-ttu-id="ca6a1-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ca6a1-109">S_OK</span></span>  
 <span data-ttu-id="ca6a1-110">Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.</span><span class="sxs-lookup"><span data-stu-id="ca6a1-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="ca6a1-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ca6a1-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="ca6a1-112">Impossible d'allouer suffisamment de mémoire pour `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="ca6a1-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="ca6a1-113">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="ca6a1-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ca6a1-114">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="ca6a1-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca6a1-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="ca6a1-115">Requirements</span></span>  
 <span data-ttu-id="ca6a1-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca6a1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca6a1-117">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="ca6a1-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="ca6a1-118">**Bibliothèque :** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="ca6a1-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="ca6a1-119">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="ca6a1-119">**.NET Framework Versions:** 3.5 SP1</span></span>
