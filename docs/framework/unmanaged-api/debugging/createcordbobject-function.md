---
title: Fonction CreateCordbObject
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: 2716adcc8c79c8003202561ea2011c2469a6bc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179235"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="b5437-102">Fonction CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="b5437-102">CreateCordbObject Function</span></span>
<span data-ttu-id="b5437-103">Crée une interface de débogage ([ICorDebug](icordebug-interface.md)) qui fournit des fonctionnalités pour instantanér une session de débogage gérée sur un processus à distance.</span><span class="sxs-lookup"><span data-stu-id="b5437-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5437-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5437-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5437-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5437-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="b5437-106">[in] Version de débogage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="b5437-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="b5437-107">Ce paramètre doit être CorDebugVersion_2_0 pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="b5437-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="b5437-108">[out] Pointeur à un pointeur à un objet qui sera jeté à une interface [ICorDebug](icordebug-interface.md) et retourné.</span><span class="sxs-lookup"><span data-stu-id="b5437-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5437-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b5437-109">Return Value</span></span>  
 <span data-ttu-id="b5437-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b5437-110">S_OK</span></span>  
 <span data-ttu-id="b5437-111">Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.</span><span class="sxs-lookup"><span data-stu-id="b5437-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="b5437-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b5437-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="b5437-113">`ppCordb` est null ou `iDebuggerVersion` n'est pas CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="b5437-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="b5437-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b5437-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b5437-115">Impossible d'allouer suffisamment de mémoire pour `ppCordb`.</span><span class="sxs-lookup"><span data-stu-id="b5437-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="b5437-116">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="b5437-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b5437-117">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="b5437-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5437-118">Notes </span><span class="sxs-lookup"><span data-stu-id="b5437-118">Remarks</span></span>  
 <span data-ttu-id="b5437-119">[L’interface ICorDebug](icordebug-interface.md) qui `ppCordb` est retournée est l’interface de débogage de haut niveau pour tous les services de débogage gérés.</span><span class="sxs-lookup"><span data-stu-id="b5437-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5437-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b5437-120">Requirements</span></span>  
 <span data-ttu-id="b5437-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5437-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5437-122">**En-tête:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="b5437-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b5437-123">**Bibliothèque:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b5437-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b5437-124">**Versions cadre .NET:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b5437-124">**.NET Framework Versions:** 3.5 SP1</span></span>
