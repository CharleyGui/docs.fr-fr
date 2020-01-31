---
title: ICorDebug::CreateProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
ms.openlocfilehash: cb16bae2dfe151d04c40269a8e6872ecb49b4269
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789014"
---
# <a name="icordebugcreateprocess-method"></a><span data-ttu-id="cda98-102">ICorDebug::CreateProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="cda98-102">ICorDebug::CreateProcess Method</span></span>
<span data-ttu-id="cda98-103">Lance un processus et son thread principal sous le contrôle du débogueur.</span><span class="sxs-lookup"><span data-stu-id="cda98-103">Launches a process and its primary thread under the control of the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cda98-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateProcess (  
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
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cda98-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="cda98-105">Parameters</span></span>  
 `lpApplicationName`  
 <span data-ttu-id="cda98-106">dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le module à exécuter par le processus lancé.</span><span class="sxs-lookup"><span data-stu-id="cda98-106">[in] Pointer to a null-terminated string that specifies the module to be executed by the launched process.</span></span> <span data-ttu-id="cda98-107">Le module est exécuté dans le contexte de sécurité du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="cda98-107">The module is executed in the security context of the calling process.</span></span>  
  
 `lpCommandLine`  
 <span data-ttu-id="cda98-108">dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie la ligne de commande devant être exécutée par le processus lancé.</span><span class="sxs-lookup"><span data-stu-id="cda98-108">[in] Pointer to a null-terminated string that specifies the command line to be executed by the launched process.</span></span> <span data-ttu-id="cda98-109">Le nom de l’application (par exemple, « SomeApp. exe ») doit être le premier argument.</span><span class="sxs-lookup"><span data-stu-id="cda98-109">The application name (for example, "SomeApp.exe") must be the first argument.</span></span>  
  
 `lpProcessAttributes`  
 <span data-ttu-id="cda98-110">dans Pointeur vers une structure de `SECURITY_ATTRIBUTES` Win32 qui spécifie le descripteur de sécurité pour le processus.</span><span class="sxs-lookup"><span data-stu-id="cda98-110">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the process.</span></span> <span data-ttu-id="cda98-111">Si `lpProcessAttributes` a la valeur null, le processus obtient un descripteur de sécurité par défaut.</span><span class="sxs-lookup"><span data-stu-id="cda98-111">If `lpProcessAttributes` is null, the process gets a default security descriptor.</span></span>  
  
 `lpThreadAttributes`  
 <span data-ttu-id="cda98-112">dans Pointeur vers une structure de `SECURITY_ATTRIBUTES` Win32 qui spécifie le descripteur de sécurité pour le thread principal du processus.</span><span class="sxs-lookup"><span data-stu-id="cda98-112">[in] Pointer to a Win32 `SECURITY_ATTRIBUTES` structure that specifies the security descriptor for the primary thread of the process.</span></span> <span data-ttu-id="cda98-113">Si `lpThreadAttributes` a la valeur null, le thread obtient un descripteur de sécurité par défaut.</span><span class="sxs-lookup"><span data-stu-id="cda98-113">If `lpThreadAttributes` is null, the thread gets a default security descriptor.</span></span>  
  
 `bInheritHandles`  
 <span data-ttu-id="cda98-114">dans Affectez la valeur `true` pour indiquer que chaque handle pouvant être hérité dans le processus appelant est hérité par le processus lancé, ou `false` pour indiquer que les handles ne sont pas hérités.</span><span class="sxs-lookup"><span data-stu-id="cda98-114">[in] Set to `true` to indicate that each inheritable handle in the calling process is inherited by the launched process, or `false` to indicate that the handles are not inherited.</span></span> <span data-ttu-id="cda98-115">Les handles hérités ont la même valeur et les mêmes droits d’accès que les handles d’origine.</span><span class="sxs-lookup"><span data-stu-id="cda98-115">The inherited handles have the same value and access rights as the original handles.</span></span>  
  
 `dwCreationFlags`  
 <span data-ttu-id="cda98-116">dans Combinaison d’opérations de bits des [indicateurs de création de processus Win32](/windows/win32/procthread/process-creation-flags) qui contrôlent la classe de priorité et le comportement du processus lancé.</span><span class="sxs-lookup"><span data-stu-id="cda98-116">[in] A bitwise combination of the [Win32 Process Creation Flags](/windows/win32/procthread/process-creation-flags) that control the priority class and the behavior of the launched process.</span></span>  
  
 `lpEnvironment`  
 <span data-ttu-id="cda98-117">dans Pointeur vers un bloc d’environnement pour le nouveau processus.</span><span class="sxs-lookup"><span data-stu-id="cda98-117">[in] Pointer to an environment block for the new process.</span></span>  
  
 `lpCurrentDirectory`  
 <span data-ttu-id="cda98-118">dans Pointeur vers une chaîne se terminant par un caractère null qui spécifie le chemin d’accès complet au répertoire actif du processus.</span><span class="sxs-lookup"><span data-stu-id="cda98-118">[in] Pointer to a null-terminated string that specifies the full path to the current directory for the process.</span></span> <span data-ttu-id="cda98-119">Si ce paramètre a la valeur null, le nouveau processus aura le même lecteur et le même répertoire en cours que le processus appelant.</span><span class="sxs-lookup"><span data-stu-id="cda98-119">If this parameter is null, the new process will have the same current drive and directory as the calling process.</span></span>  
  
 `lpStartupInfo`  
 <span data-ttu-id="cda98-120">dans Pointeur vers une structure de `STARTUPINFOW` Win32 qui spécifie la station Windows, le bureau, les handles standard et l’apparence de la fenêtre principale pour le processus lancé.</span><span class="sxs-lookup"><span data-stu-id="cda98-120">[in] Pointer to a Win32 `STARTUPINFOW` structure that specifies the window station, desktop, standard handles, and appearance of the main window for the launched process.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="cda98-121">dans Pointeur vers une structure de `PROCESS_INFORMATION` Win32 qui spécifie les informations d’identification sur le processus à lancer.</span><span class="sxs-lookup"><span data-stu-id="cda98-121">[in] Pointer to a Win32 `PROCESS_INFORMATION` structure that specifies the identification information about the process to be launched.</span></span>  
  
 `debuggingFlags`  
 <span data-ttu-id="cda98-122">dans Valeur de l’énumération CorDebugCreateProcessFlags, qui spécifie les options de débogage.</span><span class="sxs-lookup"><span data-stu-id="cda98-122">[in] A value of the CorDebugCreateProcessFlags enumeration that specifies the debugging options.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="cda98-123">à Pointeur vers l’adresse d’un objet ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="cda98-123">[out] A pointer to the address of a ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cda98-124">Notes</span><span class="sxs-lookup"><span data-stu-id="cda98-124">Remarks</span></span>  
 <span data-ttu-id="cda98-125">Les paramètres de cette méthode sont les mêmes que ceux de la méthode de `CreateProcess` Win32.</span><span class="sxs-lookup"><span data-stu-id="cda98-125">The parameters of this method are the same as those of the Win32 `CreateProcess` method.</span></span>  
  
 <span data-ttu-id="cda98-126">Pour activer le débogage en mode mixte non managé, définissez `dwCreationFlags` sur DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span><span class="sxs-lookup"><span data-stu-id="cda98-126">To enable unmanaged mixed-mode debugging, set `dwCreationFlags` to DEBUG_PROCESS &#124; DEBUG_ONLY_THIS_PROCESS.</span></span> <span data-ttu-id="cda98-127">Si vous souhaitez utiliser uniquement le débogage managé, ne définissez pas ces indicateurs.</span><span class="sxs-lookup"><span data-stu-id="cda98-127">If you want to use only managed debugging, do not set these flags.</span></span>  
  
 <span data-ttu-id="cda98-128">Si le débogueur et le processus à déboguer (le processus attaché) partagent une console unique, et si le débogage d’interopérabilité est utilisé, il est possible que le processus attaché contienne des verrous de console et s’arrête à un événement de débogage.</span><span class="sxs-lookup"><span data-stu-id="cda98-128">If the debugger and the process to be debugged (the attached process) share a single console, and if interop debugging is used, it is possible for the attached process to hold console locks and stop at a debug event.</span></span> <span data-ttu-id="cda98-129">Le débogueur bloquera alors toute tentative d’utilisation de la console.</span><span class="sxs-lookup"><span data-stu-id="cda98-129">The debugger will then block any attempt to use the console.</span></span> <span data-ttu-id="cda98-130">Pour éviter ce problème, définissez l’indicateur CREATE_NEW_CONSOLE dans le paramètre `dwCreationFlags`.</span><span class="sxs-lookup"><span data-stu-id="cda98-130">To avoid this problem, set the CREATE_NEW_CONSOLE flag in the `dwCreationFlags` parameter.</span></span>  
  
 <span data-ttu-id="cda98-131">Le débogage d’interopérabilité n’est pas pris en charge sur les plateformes Win9x et non-x86, telles que les plateformes basées sur IA-64 et AMD64.</span><span class="sxs-lookup"><span data-stu-id="cda98-131">Interop debugging is not supported on Win9x and non-x86 platforms such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cda98-132">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="cda98-132">Requirements</span></span>  
 <span data-ttu-id="cda98-133">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cda98-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cda98-134">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cda98-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cda98-135">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cda98-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cda98-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cda98-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cda98-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cda98-137">See also</span></span>

- [<span data-ttu-id="cda98-138">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="cda98-138">ICorDebug Interface</span></span>](icordebug-interface.md)
