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
ms.openlocfilehash: 340d2de09562ea9b767203a7fa839cdc6b729b3b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860890"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="4c13d-102">Fonction CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="4c13d-102">CreateCordbObject Function</span></span>
<span data-ttu-id="4c13d-103">Crée une interface de débogueur[ICorDebug](icordebug-interface.md)qui fournit des fonctionnalités pour instancier une session de débogage managée sur un processus distant.</span><span class="sxs-lookup"><span data-stu-id="4c13d-103">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c13d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c13d-104">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c13d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c13d-105">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="4c13d-106">[in] Version de débogage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="4c13d-106">[in] Debugger version of the target process.</span></span> <span data-ttu-id="4c13d-107">Ce paramètre doit être CorDebugVersion_2_0 pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="4c13d-107">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="4c13d-108">à Pointeur vers un pointeur vers un objet qui sera casté en interface [ICorDebug](icordebug-interface.md) et retourné.</span><span class="sxs-lookup"><span data-stu-id="4c13d-108">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c13d-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4c13d-109">Return Value</span></span>  
 <span data-ttu-id="4c13d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c13d-110">S_OK</span></span>  
 <span data-ttu-id="4c13d-111">Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.</span><span class="sxs-lookup"><span data-stu-id="4c13d-111">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="4c13d-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4c13d-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="4c13d-113">`ppCordb` est null ou `iDebuggerVersion` n'est pas CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="4c13d-113">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="4c13d-114">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4c13d-114">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="4c13d-115">Impossible d'allouer suffisamment de mémoire pour `ppCordb`.</span><span class="sxs-lookup"><span data-stu-id="4c13d-115">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="4c13d-116">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="4c13d-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4c13d-117">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="4c13d-117">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c13d-118">Notes </span><span class="sxs-lookup"><span data-stu-id="4c13d-118">Remarks</span></span>  
 <span data-ttu-id="4c13d-119">L’interface [ICorDebug](icordebug-interface.md) qui est retournée `ppCordb` dans est l’interface de débogage de niveau supérieur pour tous les services de débogage managés.</span><span class="sxs-lookup"><span data-stu-id="4c13d-119">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c13d-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4c13d-120">Requirements</span></span>  
 <span data-ttu-id="4c13d-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c13d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c13d-122">**En-tête :** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="4c13d-122">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="4c13d-123">**Bibliothèque :** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="4c13d-123">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="4c13d-124">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="4c13d-124">**.NET Framework Versions:** 3.5 SP1</span></span>
