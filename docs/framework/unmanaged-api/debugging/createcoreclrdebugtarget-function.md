---
title: CreateCoreClrDebugTarget, fonction
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
ms.openlocfilehash: a7fed8cb70785f0ccfcadf1e16181db303ac98e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789193"
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="f7936-102">CreateCoreClrDebugTarget, fonction</span><span class="sxs-lookup"><span data-stu-id="f7936-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="f7936-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span><span class="sxs-lookup"><span data-stu-id="f7936-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7936-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7936-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7936-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f7936-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="f7936-106">[in] Adresse IPv4 d'un ordinateur cible distant.</span><span class="sxs-lookup"><span data-stu-id="f7936-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="f7936-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span><span class="sxs-lookup"><span data-stu-id="f7936-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7936-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f7936-108">Return Value</span></span>  
 <span data-ttu-id="f7936-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7936-109">S_OK</span></span>  
 <span data-ttu-id="f7936-110">Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.</span><span class="sxs-lookup"><span data-stu-id="f7936-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="f7936-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f7936-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="f7936-112">Impossible d'allouer suffisamment de mémoire pour `ppTarget`.</span><span class="sxs-lookup"><span data-stu-id="f7936-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="f7936-113">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="f7936-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f7936-114">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="f7936-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7936-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f7936-115">Requirements</span></span>  
 <span data-ttu-id="f7936-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7936-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7936-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="f7936-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="f7936-118">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="f7936-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="f7936-119">**.NET Framework Versions:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f7936-119">**.NET Framework Versions:** 3.5 SP1</span></span>
