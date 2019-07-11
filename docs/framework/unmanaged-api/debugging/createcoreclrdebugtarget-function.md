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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbcf6c842e7eee55609a9ea2a25cda4360f8dc95
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739289"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="de404-102">Fonction CreateCoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="de404-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="de404-103">Crée une connexion à un proxy de débogueur qui s’exécute sur un ordinateur distant et retourne un [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objet qui peut être utilisé pour interroger les processus en cours d’exécution et les runtimes chargés sur l’ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="de404-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de404-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de404-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de404-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="de404-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="de404-106">[in] Adresse IPv4 d'un ordinateur cible distant.</span><span class="sxs-lookup"><span data-stu-id="de404-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="de404-107">[out] Pointeur vers un pointeur vers un [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) objet sera créé.</span><span class="sxs-lookup"><span data-stu-id="de404-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de404-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="de404-108">Return Value</span></span>  
 <span data-ttu-id="de404-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="de404-109">S_OK</span></span>  
 <span data-ttu-id="de404-110">Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.</span><span class="sxs-lookup"><span data-stu-id="de404-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="de404-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="de404-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="de404-112">Impossible d'allouer suffisamment de mémoire pour `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="de404-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="de404-113">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="de404-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="de404-114">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="de404-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de404-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="de404-115">Requirements</span></span>  
 <span data-ttu-id="de404-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de404-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de404-117">**En-tête :** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="de404-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="de404-118">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="de404-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="de404-119">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="de404-119">**.NET Framework Versions:** 3.5 SP1</span></span>
