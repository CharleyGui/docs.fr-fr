---
title: ICorDebugRemote::CreateProcessEx, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
ms.openlocfilehash: 4b2689f04228c9ecbbbb18531a0aefd3c40e3072
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377978"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="e32bb-102">ICorDebugRemote::CreateProcessEx, méthode</span><span class="sxs-lookup"><span data-stu-id="e32bb-102">ICorDebugRemote::CreateProcessEx Method</span></span>
<span data-ttu-id="e32bb-103">Lance un processus sur un ordinateur distant sous le débogueur.</span><span class="sxs-lookup"><span data-stu-id="e32bb-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e32bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e32bb-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e32bb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e32bb-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="e32bb-106">dans Pointeur vers une [interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e32bb-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="e32bb-107">Utilisé pour déterminer l’ordinateur distant sur lequel le processus sera lancé.</span><span class="sxs-lookup"><span data-stu-id="e32bb-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="e32bb-108">dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le module à exécuter par le processus lancé.</span><span class="sxs-lookup"><span data-stu-id="e32bb-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="e32bb-109">Le module est exécuté dans le contexte de sécurité du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="e32bb-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="e32bb-110">dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie la ligne de commande devant être exécutée par le processus lancé.</span><span class="sxs-lookup"><span data-stu-id="e32bb-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="e32bb-111">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="e32bb-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="e32bb-112">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="e32bb-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="e32bb-113">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="e32bb-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="e32bb-114">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="e32bb-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="e32bb-115">dans Pointeur vers un bloc d’environnement pour le nouveau processus.</span><span class="sxs-lookup"><span data-stu-id="e32bb-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="e32bb-116">dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le chemin d’accès complet au répertoire actif du processus.</span><span class="sxs-lookup"><span data-stu-id="e32bb-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="e32bb-117">Si ce paramètre a la valeur null, le nouveau processus aura le même lecteur et le même répertoire en cours que le processus appelant.</span><span class="sxs-lookup"><span data-stu-id="e32bb-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="e32bb-118">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="e32bb-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="e32bb-119">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="e32bb-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="e32bb-120">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="e32bb-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="e32bb-121">à Pointeur vers l’adresse d’un objet « interface ICorDebugProcess » qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="e32bb-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e32bb-122">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e32bb-122">Return Value</span></span>  
 <span data-ttu-id="e32bb-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="e32bb-123">S_OK</span></span>  
 <span data-ttu-id="e32bb-124">Le processus a été lancé sur l’ordinateur distant et a retourné une « interface ICorDebugProcess » pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="e32bb-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="e32bb-125">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="e32bb-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e32bb-126">Impossible de lancer le processus sur l’ordinateur distant et de retourner une « interface ICorDebugProcess » pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="e32bb-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e32bb-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="e32bb-127">Remarks</span></span>  
 <span data-ttu-id="e32bb-128">Le débogage en mode mixte n’est pas pris en charge dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="e32bb-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e32bb-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e32bb-129">Requirements</span></span>  
 <span data-ttu-id="e32bb-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e32bb-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e32bb-131">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="e32bb-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e32bb-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e32bb-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e32bb-133">**Versions de .NET Framework :** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="e32bb-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32bb-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e32bb-134">See also</span></span>

- [<span data-ttu-id="e32bb-135">ICorDebugRemote, interface</span><span class="sxs-lookup"><span data-stu-id="e32bb-135">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="e32bb-136">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="e32bb-136">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="e32bb-137">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e32bb-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
