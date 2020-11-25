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
ms.openlocfilehash: 37bf800f27754d1bf80aece962b7cbb85b1cbedc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712181"
---
# <a name="icordebugremotecreateprocessex-method"></a><span data-ttu-id="a7154-102">ICorDebugRemote::CreateProcessEx, méthode</span><span class="sxs-lookup"><span data-stu-id="a7154-102">ICorDebugRemote::CreateProcessEx Method</span></span>

<span data-ttu-id="a7154-103">Lance un processus sur un ordinateur distant sous le débogueur.</span><span class="sxs-lookup"><span data-stu-id="a7154-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7154-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7154-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a7154-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a7154-105">Parameters</span></span>  

 `pRemoteTarget`  
 <span data-ttu-id="a7154-106">dans Pointeur vers une [interface ICorDebugRemoteTarget](icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a7154-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="a7154-107">Utilisé pour déterminer l’ordinateur distant sur lequel le processus sera lancé.</span><span class="sxs-lookup"><span data-stu-id="a7154-107">Used to determine the remote machine on which the process will be launched.</span></span>  
  
 `lpApplicationName`  
 <span data-ttu-id="a7154-108">dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le module à exécuter par le processus lancé.</span><span class="sxs-lookup"><span data-stu-id="a7154-108">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="a7154-109">Le module est exécuté dans le contexte de sécurité du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="a7154-109">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="a7154-110">dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie la ligne de commande devant être exécutée par le processus lancé.</span><span class="sxs-lookup"><span data-stu-id="a7154-110">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="a7154-111">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="a7154-111">[in] Unused for remote debugging.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="a7154-112">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="a7154-112">[in] Unused for remote debugging.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="a7154-113">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="a7154-113">[in] Unused for remote debugging.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="a7154-114">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="a7154-114">[in] Unused for remote debugging.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="a7154-115">dans Pointeur vers un bloc d’environnement pour le nouveau processus.</span><span class="sxs-lookup"><span data-stu-id="a7154-115">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="a7154-116">dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le chemin d’accès complet au répertoire actif du processus.</span><span class="sxs-lookup"><span data-stu-id="a7154-116">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="a7154-117">Si ce paramètre a la valeur null, le nouveau processus aura le même lecteur et le même répertoire en cours que le processus appelant.</span><span class="sxs-lookup"><span data-stu-id="a7154-117">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="a7154-118">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="a7154-118">[in] Unused for remote debugging.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="a7154-119">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="a7154-119">[in] Unused for remote debugging.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="a7154-120">dans Non utilisé pour le débogage distant.</span><span class="sxs-lookup"><span data-stu-id="a7154-120">[in] Unused for remote debugging.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a7154-121">à Pointeur vers l’adresse d’un objet « interface ICorDebugProcess » qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="a7154-121">[out] A pointer to the address of a"ICorDebugProcess Interface" object that represents the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7154-122">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a7154-122">Return Value</span></span>  

 <span data-ttu-id="a7154-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7154-123">S_OK</span></span>  
 <span data-ttu-id="a7154-124">Le processus a été lancé sur l’ordinateur distant et a retourné une « interface ICorDebugProcess » pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="a7154-124">Successfully launched the process on the remote machine and returned an "ICorDebugProcess Interface" for debugging.</span></span>  
  
 <span data-ttu-id="a7154-125">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="a7154-125">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a7154-126">Impossible de lancer le processus sur l’ordinateur distant et de retourner une « interface ICorDebugProcess » pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="a7154-126">Unable to launch the process on the remote machine and return an "ICorDebugProcess Interface" for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7154-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="a7154-127">Remarks</span></span>  

 <span data-ttu-id="a7154-128">Le débogage en mode mixte n’est pas pris en charge dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a7154-128">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7154-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a7154-129">Requirements</span></span>  

 <span data-ttu-id="a7154-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7154-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7154-131">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="a7154-131">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="a7154-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7154-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7154-133">**Versions de .NET Framework :** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a7154-133">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7154-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7154-134">See also</span></span>

- [<span data-ttu-id="a7154-135">ICorDebugRemote, interface</span><span class="sxs-lookup"><span data-stu-id="a7154-135">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="a7154-136">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="a7154-136">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="a7154-137">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="a7154-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
