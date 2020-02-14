---
title: Diagnostic d'erreurs avec les Assistants Débogage managé
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
ms.openlocfilehash: 712fbbe9e0ad291385e8eef321c5e8a2fa092a5d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216554"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="d0cac-102">Diagnostiquer les erreurs avec les assistants débogage managés</span><span class="sxs-lookup"><span data-stu-id="d0cac-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="d0cac-103">Les Assistants Débogage managé sont des aides au débogage qui fonctionnent conjointement avec le Common Language Runtime (CLR) pour fournir des informations sur l'état d'exécution.</span><span class="sxs-lookup"><span data-stu-id="d0cac-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="d0cac-104">Les Assistants génèrent des messages d'information sur les événements du runtime que vous ne pouvez pas intercepter en temps normal.</span><span class="sxs-lookup"><span data-stu-id="d0cac-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="d0cac-105">Vous pouvez utiliser les Assistants Débogage managé pour isoler les bogues d'application difficiles à déceler qui se produisent pendant les phases de transition entre un code managé et un code non managé.</span><span class="sxs-lookup"><span data-stu-id="d0cac-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="d0cac-106">Vous pouvez [activer ou désactiver](#enable-and-disable-mdas) tous les Assistants Débogage managé en ajoutant une clé au registre Windows ou en définissant une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="d0cac-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="d0cac-107">Vous pouvez activer des Assistants Débogage managé spécifiques à l'aide de paramètres de configuration d'application.</span><span class="sxs-lookup"><span data-stu-id="d0cac-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="d0cac-108">Vous pouvez définir des paramètres de configuration supplémentaires pour certains Assistants Débogage managé dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="d0cac-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="d0cac-109">Comme ces fichiers de configuration sont analysés au chargement du runtime, vous devez activer l'Assistant Débogage managé avant que l'application managée ne démarre.</span><span class="sxs-lookup"><span data-stu-id="d0cac-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="d0cac-110">Vous ne pouvez pas l'activer pour les applications qui ont déjà démarré.</span><span class="sxs-lookup"><span data-stu-id="d0cac-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="d0cac-111">Le tableau suivant répertorie les MDA fournis avec l' .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="d0cac-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="d0cac-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="d0cac-112">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="d0cac-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="d0cac-113">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="d0cac-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="d0cac-114">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="d0cac-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="d0cac-115">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="d0cac-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="d0cac-116">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="d0cac-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="d0cac-117">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="d0cac-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="d0cac-118">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="d0cac-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="d0cac-119">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="d0cac-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="d0cac-120">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="d0cac-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="d0cac-121">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="d0cac-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="d0cac-122">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="d0cac-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="d0cac-123">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="d0cac-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="d0cac-124">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="d0cac-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="d0cac-125">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="d0cac-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="d0cac-126">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="d0cac-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="d0cac-127">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="d0cac-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="d0cac-128">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="d0cac-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="d0cac-129">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="d0cac-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="d0cac-130">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="d0cac-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="d0cac-131">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="d0cac-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="d0cac-132">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="d0cac-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="d0cac-133">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="d0cac-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="d0cac-134">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="d0cac-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="d0cac-135">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="d0cac-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="d0cac-136">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="d0cac-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="d0cac-137">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="d0cac-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="d0cac-138">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="d0cac-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="d0cac-139">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="d0cac-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="d0cac-140">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="d0cac-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="d0cac-141">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="d0cac-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="d0cac-142">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="d0cac-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="d0cac-143">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="d0cac-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="d0cac-144">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="d0cac-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="d0cac-145">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="d0cac-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="d0cac-146">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="d0cac-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="d0cac-147">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="d0cac-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="d0cac-148">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="d0cac-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="d0cac-149">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="d0cac-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="d0cac-150">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="d0cac-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="d0cac-151">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="d0cac-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="d0cac-152">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="d0cac-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="d0cac-153">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="d0cac-154">Par défaut, le .NET Framework active une partie des Assistants Débogage managé pour tous les débogueurs managés.</span><span class="sxs-lookup"><span data-stu-id="d0cac-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="d0cac-155">Vous pouvez afficher l’ensemble par défaut dans Visual Studio en choisissant **Windows** > les **paramètres d’exception** dans le menu **Déboguer** , puis en développant la liste **Assistants Débogage managé** .</span><span class="sxs-lookup"><span data-stu-id="d0cac-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Fenêtre Paramètres d’exception dans Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="d0cac-157">Activer et désactiver les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="d0cac-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="d0cac-158">Vous pouvez activer et désactiver les Assistants Débogage managé en utilisant une clé de Registre, une variable d'environnement et des paramètres de configuration d'application.</span><span class="sxs-lookup"><span data-stu-id="d0cac-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="d0cac-159">Vous devez activer la clé de Registre ou la variable d'environnement pour utiliser les paramètres de configuration d'application.</span><span class="sxs-lookup"><span data-stu-id="d0cac-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="d0cac-160">Au lieu de désactiver les MDA, vous pouvez empêcher Visual Studio d’afficher la boîte de dialogue Assistant Débogage managé chaque fois qu’une notification MDA est reçue.</span><span class="sxs-lookup"><span data-stu-id="d0cac-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="d0cac-161">Pour ce faire, choisissez **Windows** > les paramètres d’exception dans le menu **Déboguer** , développez la liste **assistants débogage managés** , puis activez ou désactivez la case à cocher **arrêter la levée en cas** d' **exception** pour l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="d0cac-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="d0cac-162">Clé de Registre</span><span class="sxs-lookup"><span data-stu-id="d0cac-162">Registry Key</span></span>

<span data-ttu-id="d0cac-163">Pour activer les MDA, ajoutez le **\\HKEY_LOCAL_MACHINE \Software\Microsoft.** Sous-clé NETFramework\MDA (type REG_SZ, valeur 1) dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="d0cac-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="d0cac-164">Copiez l’exemple suivant dans un fichier texte nommé *MDAEnable. reg*. Ouvrez l’éditeur du Registre Windows (RegEdit. exe), puis, dans le menu **fichier** , choisissez **Importer**.</span><span class="sxs-lookup"><span data-stu-id="d0cac-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="d0cac-165">Sélectionnez le fichier *MDAEnable. reg* pour activer les MDA sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d0cac-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="d0cac-166">La définition de la sous-clé sur la valeur de chaîne **1** (pas la valeur DWORD **1**) active la lecture des paramètres MDA à partir du fichier *applicationName. suffixe*. MDA. config.</span><span class="sxs-lookup"><span data-stu-id="d0cac-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="d0cac-167">Par exemple, le fichier de configuration MDA pour le bloc-notes est nommé Notepad. exe. MDA. config.</span><span class="sxs-lookup"><span data-stu-id="d0cac-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="d0cac-168">Si l'ordinateur exécute une application 32 bits sur un système d'exploitation 64 bits, la clé MDA doit être définie comme suit :</span><span class="sxs-lookup"><span data-stu-id="d0cac-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="d0cac-169">Pour plus d’informations, consultez [paramètres de configuration spécifiques](#application-specific-configuration-settings) à l’application.</span><span class="sxs-lookup"><span data-stu-id="d0cac-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="d0cac-170">Le paramétrage du Registre peut être remplacé par la variable d'environnement COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="d0cac-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="d0cac-171">Pour plus d’informations, consultez [variable d’environnement](#environment-variable) .</span><span class="sxs-lookup"><span data-stu-id="d0cac-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="d0cac-172">Pour désactiver les MDA, définissez la sous-clé de l’Assistant Débogage managé sur **0** (zéro) à l’aide de l’éditeur du Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="d0cac-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="d0cac-173">Par défaut, certains Assistants Débogage managé sont activés quand vous exécutez une application qui est attachée à un débogueur, même sans que la clé de Registre soit ajoutée.</span><span class="sxs-lookup"><span data-stu-id="d0cac-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="d0cac-174">Vous pouvez désactiver ces assistants en exécutant le fichier *MDADisable. reg* comme décrit précédemment dans cette section.</span><span class="sxs-lookup"><span data-stu-id="d0cac-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="d0cac-175">Variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="d0cac-175">Environment Variable</span></span>

<span data-ttu-id="d0cac-176">L'activation des Assistants Débogage managé peut également être contrôlée par la variable d'environnement COMPLUS_MDA, qui remplace la clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="d0cac-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="d0cac-177">La chaîne COMPLUS_MDA est une liste de noms d'Assistant Débogage managé ou d'autres chaînes de contrôle spéciales séparés par des points-virgules et sans distinction minuscules/majuscules.</span><span class="sxs-lookup"><span data-stu-id="d0cac-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="d0cac-178">Démarrer sous un débogueur managé ou non managé active par défaut un ensemble d'Assistants Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="d0cac-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="d0cac-179">Pour ce faire, la valeur de la variable d'environnement ou de la clé de Registre doit être implicitement ajoutée au début de la liste délimitée par des points-virgules qui répertorie les Assistants Débogage managé activés par défaut sous les débogueurs.</span><span class="sxs-lookup"><span data-stu-id="d0cac-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="d0cac-180">Les chaînes de contrôle spéciales sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d0cac-180">The special control strings are the following:</span></span>

- <span data-ttu-id="d0cac-181">`0` : désactive tous les Assistants Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="d0cac-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="d0cac-182">`1` : lit les paramètres d’Assistant Débogage managé dans le fichier *nom_application*.mda.config.</span><span class="sxs-lookup"><span data-stu-id="d0cac-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="d0cac-183">`managedDebugger` : active explicitement tous les Assistants Débogage managé qui sont implicitement activés quand un exécutable managé est démarré sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="d0cac-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="d0cac-184">`unmanagedDebugger` : active explicitement tous les Assistants Débogage managé qui sont implicitement activés quand un exécutable non managé est démarré sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="d0cac-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="d0cac-185">En cas de conflit de paramètres, les paramètres les plus récents remplacent les paramètres antérieurs :</span><span class="sxs-lookup"><span data-stu-id="d0cac-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="d0cac-186">`COMPLUS_MDA=0` désactive tous les Assistants Débogage managé, y compris ceux qui sont implicitement activés sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="d0cac-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="d0cac-187">`COMPLUS_MDA=gcUnmanagedToManaged` active `gcUnmanagedToManaged` outre tout Assistant Débogage managé implicitement activé sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="d0cac-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="d0cac-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` active `gcUnmanagedToManaged`, mais désactive tout Assistant Débogage managé implicitement activé sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="d0cac-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="d0cac-189">Paramètres de configuration spécifiques à l’application</span><span class="sxs-lookup"><span data-stu-id="d0cac-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="d0cac-190">Vous pouvez activer, désactiver et configurer certains Assistants séparément dans le fichier de configuration d'Assistant Débogage managé propre à l'application.</span><span class="sxs-lookup"><span data-stu-id="d0cac-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="d0cac-191">Vous ne pouvez utiliser un fichier de configuration d'application pour configurer des Assistants Débogage managé que si la clé de Registre MDA ou la variable d'environnement COMPLUS_MDA est définie.</span><span class="sxs-lookup"><span data-stu-id="d0cac-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="d0cac-192">En règle générale, le fichier de configuration d'application se trouve dans le même répertoire que le fichier exécutable (.exe) de l'application.</span><span class="sxs-lookup"><span data-stu-id="d0cac-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="d0cac-193">Le nom de fichier prend la forme *applicationName*. MDA. config ; par exemple, Notepad. exe. MDA. config. Les assistants qui sont activés dans le fichier de configuration de l’application peuvent avoir des attributs ou des éléments conçus spécifiquement pour contrôler le comportement de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="d0cac-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="d0cac-194">L’exemple suivant montre comment activer et configurer le [marshaling](marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="d0cac-194">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

<span data-ttu-id="d0cac-195">L’Assistant Débogage managé `Marshaling` émet des informations sur le type managé qui est marshalé en un type non managé pour chaque transition de code managé vers un code non managé dans l’application.</span><span class="sxs-lookup"><span data-stu-id="d0cac-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="d0cac-196">L’Assistant Débogage managé `Marshaling` peut également filtrer les noms des champs de méthode et de structure fournis dans les éléments enfants **methodFilter** et **fieldFilter** , respectivement.</span><span class="sxs-lookup"><span data-stu-id="d0cac-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="d0cac-197">L’exemple suivant montre comment activer plusieurs Assistants Débogage managé à l’aide de leurs paramètres par défaut :</span><span class="sxs-lookup"><span data-stu-id="d0cac-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> <span data-ttu-id="d0cac-198">Quand vous spécifiez plusieurs Assistants dans un fichier de configuration, vous devez les répertorier dans l'ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="d0cac-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="d0cac-199">Par exemple, pour activer les Assistants Débogage managé `virtualCERCall` et `invalidCERCall`, vous devez ajouter l'entrée `<invalidCERCall />` avant l'entrée `<virtualCERCall />`.</span><span class="sxs-lookup"><span data-stu-id="d0cac-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="d0cac-200">Si vous n'indiquez pas les entrées dans l'ordre alphabétique, vous obtenez un message d'exception non gérée liée à un fichier de configuration non valide.</span><span class="sxs-lookup"><span data-stu-id="d0cac-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="d0cac-201">Exceptions MDA</span><span class="sxs-lookup"><span data-stu-id="d0cac-201">MDA exceptions</span></span>

<span data-ttu-id="d0cac-202">Lorsqu’un Assistant Débogage managé est activé, il est actif même lorsque votre code ne s’exécute pas sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="d0cac-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="d0cac-203">Si un événement d'Assistant Débogage managé est déclenché en l'absence de débogueur, le message de l'événement est présenté dans une boîte de dialogue d'exception non gérée, bien qu'il ne s'agisse pas d'une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="d0cac-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="d0cac-204">Pour éviter l'affichage de la boîte de dialogue, supprimez les paramètres de désactivation de l'Assistant Débogage managé quand votre code ne s'exécute pas dans un environnement de débogage.</span><span class="sxs-lookup"><span data-stu-id="d0cac-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="d0cac-205">Lorsque votre code s’exécute dans l’environnement de développement intégré (IDE) de Visual Studio, vous pouvez éviter la boîte de dialogue d’exception qui s’affiche pour les événements MDA spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d0cac-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="d0cac-206">Pour ce faire, dans le menu **Déboguer** , choisissez **Windows** > **paramètres d’exception**.</span><span class="sxs-lookup"><span data-stu-id="d0cac-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="d0cac-207">Dans la fenêtre Paramètres d’exception, développez la liste **Assistants Débogage managé** , puis désactivez la case à cocher **arrêter la levée en cas** d' **exception** pour chaque MDA.</span><span class="sxs-lookup"><span data-stu-id="d0cac-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="d0cac-208">Vous pouvez également utiliser cette boîte de dialogue pour *activer* l’affichage des boîtes de dialogue d’exception d’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="d0cac-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="d0cac-209">Sortie de l'Assistant Débogage managé</span><span class="sxs-lookup"><span data-stu-id="d0cac-209">MDA Output</span></span>

<span data-ttu-id="d0cac-210">La sortie de l’Assistant Débogage managé est semblable à l’exemple suivant, qui montre la sortie de l’Assistant Débogage managé `PInvokeStackImbalance` :</span><span class="sxs-lookup"><span data-stu-id="d0cac-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="d0cac-211">**Un appel à la fonction PInvoke’MDATest ! MDATest. Program :: StdCall’a déséquilibré la pile. Cela est probablement dû au fait que la signature PInvoke managée ne correspond pas à la signature cible non managée. Vérifiez que la Convention d’appel et les paramètres de la signature PInvoke correspondent à la signature non managée cible.**</span><span class="sxs-lookup"><span data-stu-id="d0cac-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="d0cac-212">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0cac-212">See also</span></span>

- [<span data-ttu-id="d0cac-213">Débogage, traçage et profilage</span><span class="sxs-lookup"><span data-stu-id="d0cac-213">Debugging, Tracing, and Profiling</span></span>](index.md)
