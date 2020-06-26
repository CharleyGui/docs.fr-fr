---
title: Diagnostic d'erreurs avec les Assistants de débogage managés
description: Diagnostiquez les erreurs dans .NET avec les assistants débogage managés. Les MDA sont des aides au débogage qui fonctionnent conjointement avec le CLR pour fournir des informations d’état d’exécution.
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
ms.openlocfilehash: ac6fdc09fb057cc55659ce076d37ab96fe2354d1
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416094"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="22a70-104">Diagnostiquer les erreurs avec les assistants débogage managés</span><span class="sxs-lookup"><span data-stu-id="22a70-104">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="22a70-105">Les Assistants Débogage managé sont des aides au débogage qui fonctionnent conjointement avec le Common Language Runtime (CLR) pour fournir des informations sur l'état d'exécution.</span><span class="sxs-lookup"><span data-stu-id="22a70-105">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="22a70-106">Les Assistants génèrent des messages d'information sur les événements du runtime que vous ne pouvez pas intercepter en temps normal.</span><span class="sxs-lookup"><span data-stu-id="22a70-106">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="22a70-107">Vous pouvez utiliser les Assistants Débogage managé pour isoler les bogues d'application difficiles à déceler qui se produisent pendant les phases de transition entre un code managé et un code non managé.</span><span class="sxs-lookup"><span data-stu-id="22a70-107">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="22a70-108">Vous pouvez [activer ou désactiver](#enable-and-disable-mdas) tous les Assistants Débogage managé en ajoutant une clé au registre Windows ou en définissant une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="22a70-108">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="22a70-109">Vous pouvez activer des Assistants Débogage managé spécifiques à l'aide de paramètres de configuration d'application.</span><span class="sxs-lookup"><span data-stu-id="22a70-109">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="22a70-110">Vous pouvez définir des paramètres de configuration supplémentaires pour certains Assistants Débogage managé dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="22a70-110">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="22a70-111">Comme ces fichiers de configuration sont analysés au chargement du runtime, vous devez activer l'Assistant Débogage managé avant que l'application managée ne démarre.</span><span class="sxs-lookup"><span data-stu-id="22a70-111">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="22a70-112">Vous ne pouvez pas l'activer pour les applications qui ont déjà démarré.</span><span class="sxs-lookup"><span data-stu-id="22a70-112">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="22a70-113">Le tableau suivant répertorie les MDA fournis avec l' .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="22a70-113">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="22a70-114">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="22a70-114">asynchronousThreadAbort</span></span>](asynchronousthreadabort-mda.md)|[<span data-ttu-id="22a70-115">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="22a70-115">bindingFailure</span></span>](bindingfailure-mda.md)|
|[<span data-ttu-id="22a70-116">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="22a70-116">callbackOnCollectedDelegate</span></span>](callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="22a70-117">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="22a70-117">contextSwitchDeadlock</span></span>](contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="22a70-118">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="22a70-118">dangerousThreadingAPI</span></span>](dangerousthreadingapi-mda.md)|[<span data-ttu-id="22a70-119">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="22a70-119">dateTimeInvalidLocalFormat</span></span>](datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="22a70-120">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="22a70-120">dirtyCastAndCallOnInterface</span></span>](dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="22a70-121">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="22a70-121">disconnectedContext</span></span>](disconnectedcontext-mda.md)|
|[<span data-ttu-id="22a70-122">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="22a70-122">dllMainReturnsFalse</span></span>](dllmainreturnsfalse-mda.md)|[<span data-ttu-id="22a70-123">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="22a70-123">exceptionSwallowedOnCallFromCom</span></span>](exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="22a70-124">failedQI</span><span class="sxs-lookup"><span data-stu-id="22a70-124">failedQI</span></span>](failedqi-mda.md)|[<span data-ttu-id="22a70-125">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="22a70-125">fatalExecutionEngineError</span></span>](fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="22a70-126">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="22a70-126">gcManagedToUnmanaged</span></span>](gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="22a70-127">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="22a70-127">gcUnmanagedToManaged</span></span>](gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="22a70-128">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="22a70-128">illegalPrepareConstrainedRegion</span></span>](illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="22a70-129">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="22a70-129">invalidApartmentStateChange</span></span>](invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="22a70-130">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="22a70-130">invalidCERCall</span></span>](invalidcercall-mda.md)|[<span data-ttu-id="22a70-131">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="22a70-131">invalidFunctionPointerInDelegate</span></span>](invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="22a70-132">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="22a70-132">invalidGCHandleCookie</span></span>](invalidgchandlecookie-mda.md)|[<span data-ttu-id="22a70-133">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="22a70-133">invalidIUnknown</span></span>](invalidiunknown-mda.md)|
|[<span data-ttu-id="22a70-134">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="22a70-134">invalidMemberDeclaration</span></span>](invalidmemberdeclaration-mda.md)|[<span data-ttu-id="22a70-135">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="22a70-135">invalidOverlappedToPinvoke</span></span>](invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="22a70-136">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="22a70-136">invalidVariant</span></span>](invalidvariant-mda.md)|[<span data-ttu-id="22a70-137">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="22a70-137">jitCompilationStart</span></span>](jitcompilationstart-mda.md)|
|[<span data-ttu-id="22a70-138">loaderLock</span><span class="sxs-lookup"><span data-stu-id="22a70-138">loaderLock</span></span>](loaderlock-mda.md)|[<span data-ttu-id="22a70-139">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="22a70-139">loadFromContext</span></span>](loadfromcontext-mda.md)|
|[<span data-ttu-id="22a70-140">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="22a70-140">marshalCleanupError</span></span>](marshalcleanuperror-mda.md)|[<span data-ttu-id="22a70-141">marshaling</span><span class="sxs-lookup"><span data-stu-id="22a70-141">marshaling</span></span>](marshaling-mda.md)|
|[<span data-ttu-id="22a70-142">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="22a70-142">memberInfoCacheCreation</span></span>](memberinfocachecreation-mda.md)|[<span data-ttu-id="22a70-143">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="22a70-143">moduloObjectHashcode</span></span>](moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="22a70-144">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="22a70-144">nonComVisibleBaseClass</span></span>](noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="22a70-145">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="22a70-145">notMarshalable</span></span>](notmarshalable-mda.md)|
|[<span data-ttu-id="22a70-146">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="22a70-146">openGenericCERCall</span></span>](opengenericcercall-mda.md)|[<span data-ttu-id="22a70-147">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="22a70-147">overlappedFreeError</span></span>](overlappedfreeerror-mda.md)|
|[<span data-ttu-id="22a70-148">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="22a70-148">pInvokeLog</span></span>](pinvokelog-mda.md)|[<span data-ttu-id="22a70-149">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="22a70-149">pInvokeStackImbalance</span></span>](pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="22a70-150">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="22a70-150">raceOnRCWCleanup</span></span>](raceonrcwcleanup-mda.md)|[<span data-ttu-id="22a70-151">réentrance</span><span class="sxs-lookup"><span data-stu-id="22a70-151">reentrancy</span></span>](reentrancy-mda.md)|
|[<span data-ttu-id="22a70-152">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="22a70-152">releaseHandleFailed</span></span>](releasehandlefailed-mda.md)|[<span data-ttu-id="22a70-153">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="22a70-153">reportAvOnComRelease</span></span>](reportavoncomrelease-mda.md)|
|[<span data-ttu-id="22a70-154">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="22a70-154">streamWriterBufferedDataLost</span></span>](streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="22a70-155">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="22a70-155">virtualCERCall</span></span>](virtualcercall-mda.md)|

<span data-ttu-id="22a70-156">Par défaut, le .NET Framework active une partie des Assistants Débogage managé pour tous les débogueurs managés.</span><span class="sxs-lookup"><span data-stu-id="22a70-156">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="22a70-157">Vous pouvez afficher l’ensemble par défaut dans Visual Studio en **Windows**choisissant  >  **paramètres des exceptions** Windows dans le menu **Déboguer** , puis en développant la liste **assistants de débogage managés** .</span><span class="sxs-lookup"><span data-stu-id="22a70-157">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![Fenêtre Paramètres d’exception dans Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="22a70-159">Activer et désactiver les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="22a70-159">Enable and Disable MDAs</span></span>

<span data-ttu-id="22a70-160">Vous pouvez activer et désactiver les Assistants Débogage managé en utilisant une clé de Registre, une variable d'environnement et des paramètres de configuration d'application.</span><span class="sxs-lookup"><span data-stu-id="22a70-160">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="22a70-161">Vous devez activer la clé de Registre ou la variable d'environnement pour utiliser les paramètres de configuration d'application.</span><span class="sxs-lookup"><span data-stu-id="22a70-161">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="22a70-162">Au lieu de désactiver les MDA, vous pouvez empêcher Visual Studio d’afficher la boîte de dialogue Assistant Débogage managé chaque fois qu’une notification MDA est reçue.</span><span class="sxs-lookup"><span data-stu-id="22a70-162">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="22a70-163">Pour ce faire, choisissez **Windows**  >  **paramètres des exceptions** Windows dans le menu **Déboguer** , développez la liste **Assistants Débogage managé** , puis activez ou désactivez la case à cocher **arrêter la levée en cas** d’exception pour le MDA individuel.</span><span class="sxs-lookup"><span data-stu-id="22a70-163">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="22a70-164">Clé de Registre</span><span class="sxs-lookup"><span data-stu-id="22a70-164">Registry Key</span></span>

<span data-ttu-id="22a70-165">Pour activer les MDA, ajoutez la \*\*HKEY_LOCAL_MACHINE \Software\Microsoft \\ . \*\*Sous-clé NETFramework\MDA (type REG_SZ, valeur 1) dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="22a70-165">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="22a70-166">Copiez l’exemple suivant dans un fichier texte nommé *MDAEnable. reg*. Ouvrez l’éditeur du Registre Windows (RegEdit.exe) et, dans le menu **fichier** , choisissez **Importer**.</span><span class="sxs-lookup"><span data-stu-id="22a70-166">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="22a70-167">Sélectionnez le fichier *MDAEnable. reg* pour activer les MDA sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="22a70-167">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="22a70-168">La définition de la sous-clé sur la valeur de chaîne **1** (pas la valeur DWORD **1**) active la lecture des paramètres MDA à partir du fichier *applicationName. suffix*.mda.config.</span><span class="sxs-lookup"><span data-stu-id="22a70-168">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="22a70-169">Par exemple, le fichier de configuration MDA pour le bloc-notes est nommé notepad.exe.mda.config.</span><span class="sxs-lookup"><span data-stu-id="22a70-169">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="22a70-170">Si l'ordinateur exécute une application 32 bits sur un système d'exploitation 64 bits, la clé MDA doit être définie comme suit :</span><span class="sxs-lookup"><span data-stu-id="22a70-170">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="22a70-171">Pour plus d’informations, consultez [paramètres de configuration spécifiques](#application-specific-configuration-settings) à l’application.</span><span class="sxs-lookup"><span data-stu-id="22a70-171">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="22a70-172">Le paramétrage du Registre peut être remplacé par la variable d'environnement COMPLUS_MDA.</span><span class="sxs-lookup"><span data-stu-id="22a70-172">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="22a70-173">Pour plus d’informations, consultez [variable d’environnement](#environment-variable) .</span><span class="sxs-lookup"><span data-stu-id="22a70-173">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="22a70-174">Pour désactiver les MDA, définissez la sous-clé de l’Assistant Débogage managé sur **0** (zéro) à l’aide de l’éditeur du Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="22a70-174">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="22a70-175">Par défaut, certains Assistants Débogage managé sont activés quand vous exécutez une application qui est attachée à un débogueur, même sans que la clé de Registre soit ajoutée.</span><span class="sxs-lookup"><span data-stu-id="22a70-175">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="22a70-176">Vous pouvez désactiver ces assistants en exécutant le fichier *MDADisable. reg* comme décrit précédemment dans cette section.</span><span class="sxs-lookup"><span data-stu-id="22a70-176">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="22a70-177">Variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="22a70-177">Environment Variable</span></span>

<span data-ttu-id="22a70-178">L'activation des Assistants Débogage managé peut également être contrôlée par la variable d'environnement COMPLUS_MDA, qui remplace la clé de Registre.</span><span class="sxs-lookup"><span data-stu-id="22a70-178">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="22a70-179">La chaîne COMPLUS_MDA est une liste de noms d'Assistant Débogage managé ou d'autres chaînes de contrôle spéciales séparés par des points-virgules et sans distinction minuscules/majuscules.</span><span class="sxs-lookup"><span data-stu-id="22a70-179">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="22a70-180">Démarrer sous un débogueur managé ou non managé active par défaut un ensemble d'Assistants Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="22a70-180">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="22a70-181">Pour ce faire, la valeur de la variable d'environnement ou de la clé de Registre doit être implicitement ajoutée au début de la liste délimitée par des points-virgules qui répertorie les Assistants Débogage managé activés par défaut sous les débogueurs.</span><span class="sxs-lookup"><span data-stu-id="22a70-181">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="22a70-182">Les chaînes de contrôle spéciales sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="22a70-182">The special control strings are the following:</span></span>

- <span data-ttu-id="22a70-183">`0` : désactive tous les Assistants Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="22a70-183">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="22a70-184">`1` : lit les paramètres d’Assistant Débogage managé dans le fichier *nom_application*.mda.config.</span><span class="sxs-lookup"><span data-stu-id="22a70-184">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="22a70-185">`managedDebugger` : active explicitement tous les Assistants Débogage managé qui sont implicitement activés quand un exécutable managé est démarré sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="22a70-185">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="22a70-186">`unmanagedDebugger` : active explicitement tous les Assistants Débogage managé qui sont implicitement activés quand un exécutable non managé est démarré sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="22a70-186">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="22a70-187">En cas de conflit de paramètres, les paramètres les plus récents remplacent les paramètres antérieurs :</span><span class="sxs-lookup"><span data-stu-id="22a70-187">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="22a70-188">`COMPLUS_MDA=0` désactive tous les Assistants Débogage managé, y compris ceux qui sont implicitement activés sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="22a70-188">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="22a70-189">`COMPLUS_MDA=gcUnmanagedToManaged` active `gcUnmanagedToManaged` outre tout Assistant Débogage managé implicitement activé sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="22a70-189">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="22a70-190">`COMPLUS_MDA=0;gcUnmanagedToManaged` active `gcUnmanagedToManaged`, mais désactive tout Assistant Débogage managé implicitement activé sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="22a70-190">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="22a70-191">Paramètres de configuration spécifiques à l’application</span><span class="sxs-lookup"><span data-stu-id="22a70-191">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="22a70-192">Vous pouvez activer, désactiver et configurer certains Assistants séparément dans le fichier de configuration d'Assistant Débogage managé propre à l'application.</span><span class="sxs-lookup"><span data-stu-id="22a70-192">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="22a70-193">Vous ne pouvez utiliser un fichier de configuration d'application pour configurer des Assistants Débogage managé que si la clé de Registre MDA ou la variable d'environnement COMPLUS_MDA est définie.</span><span class="sxs-lookup"><span data-stu-id="22a70-193">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="22a70-194">En règle générale, le fichier de configuration d'application se trouve dans le même répertoire que le fichier exécutable (.exe) de l'application.</span><span class="sxs-lookup"><span data-stu-id="22a70-194">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="22a70-195">Le nom de fichier prend la forme *ApplicationName*.mda.config ; par exemple, notepad.exe.mda.config. Les assistants qui sont activés dans le fichier de configuration de l’application peuvent avoir des attributs ou des éléments conçus spécifiquement pour contrôler le comportement de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="22a70-195">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="22a70-196">L’exemple suivant montre comment activer et configurer le [marshaling](marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="22a70-196">The following example shows how to enable and configure the [marshaling](marshaling-mda.md):</span></span>

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

<span data-ttu-id="22a70-197">L’Assistant Débogage managé `Marshaling` émet des informations sur le type managé qui est marshalé en un type non managé pour chaque transition de code managé vers un code non managé dans l’application.</span><span class="sxs-lookup"><span data-stu-id="22a70-197">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="22a70-198">L' `Marshaling` Assistant Débogage managé peut également filtrer les noms des champs de méthode et de structure fournis dans les éléments enfants **methodFilter** et **fieldFilter** , respectivement.</span><span class="sxs-lookup"><span data-stu-id="22a70-198">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="22a70-199">L’exemple suivant montre comment activer plusieurs Assistants Débogage managé à l’aide de leurs paramètres par défaut :</span><span class="sxs-lookup"><span data-stu-id="22a70-199">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

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
> <span data-ttu-id="22a70-200">Quand vous spécifiez plusieurs Assistants dans un fichier de configuration, vous devez les répertorier dans l'ordre alphabétique.</span><span class="sxs-lookup"><span data-stu-id="22a70-200">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="22a70-201">Par exemple, pour activer les Assistants Débogage managé `virtualCERCall` et `invalidCERCall`, vous devez ajouter l'entrée `<invalidCERCall />` avant l'entrée `<virtualCERCall />`.</span><span class="sxs-lookup"><span data-stu-id="22a70-201">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="22a70-202">Si vous n'indiquez pas les entrées dans l'ordre alphabétique, vous obtenez un message d'exception non gérée liée à un fichier de configuration non valide.</span><span class="sxs-lookup"><span data-stu-id="22a70-202">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="22a70-203">Exceptions MDA</span><span class="sxs-lookup"><span data-stu-id="22a70-203">MDA exceptions</span></span>

<span data-ttu-id="22a70-204">Lorsqu’un Assistant Débogage managé est activé, il est actif même lorsque votre code ne s’exécute pas sous un débogueur.</span><span class="sxs-lookup"><span data-stu-id="22a70-204">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="22a70-205">Si un événement d'Assistant Débogage managé est déclenché en l'absence de débogueur, le message de l'événement est présenté dans une boîte de dialogue d'exception non gérée, bien qu'il ne s'agisse pas d'une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="22a70-205">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="22a70-206">Pour éviter l'affichage de la boîte de dialogue, supprimez les paramètres de désactivation de l'Assistant Débogage managé quand votre code ne s'exécute pas dans un environnement de débogage.</span><span class="sxs-lookup"><span data-stu-id="22a70-206">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="22a70-207">Lorsque votre code s’exécute dans l’environnement de développement intégré (IDE) de Visual Studio, vous pouvez éviter la boîte de dialogue d’exception qui s’affiche pour les événements MDA spécifiques.</span><span class="sxs-lookup"><span data-stu-id="22a70-207">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="22a70-208">Pour ce faire, dans le menu **Déboguer** , choisissez **Windows**  >  **paramètres d’exception**Windows.</span><span class="sxs-lookup"><span data-stu-id="22a70-208">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="22a70-209">Dans la fenêtre Paramètres d’exception, développez la liste **Assistants Débogage managé** , puis désactivez la case à cocher **arrêter la levée en cas** d' **exception** pour chaque MDA.</span><span class="sxs-lookup"><span data-stu-id="22a70-209">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="22a70-210">Vous pouvez également utiliser cette boîte de dialogue pour *activer* l’affichage des boîtes de dialogue d’exception d’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="22a70-210">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="22a70-211">Sortie de l'Assistant Débogage managé</span><span class="sxs-lookup"><span data-stu-id="22a70-211">MDA Output</span></span>

<span data-ttu-id="22a70-212">La sortie de l’Assistant Débogage managé est semblable à l’exemple suivant, qui montre la sortie de l' `PInvokeStackImbalance` Assistant Débogage managé :</span><span class="sxs-lookup"><span data-stu-id="22a70-212">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="22a70-213">**Un appel à la fonction PInvoke’MDATest ! MDATest. Program :: StdCall’a déséquilibré la pile. Cela est probablement dû au fait que la signature PInvoke managée ne correspond pas à la signature cible non managée. Vérifiez que la Convention d’appel et les paramètres de la signature PInvoke correspondent à la signature non managée cible.**</span><span class="sxs-lookup"><span data-stu-id="22a70-213">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="22a70-214">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22a70-214">See also</span></span>

- [<span data-ttu-id="22a70-215">Débogage, traçage et profilage</span><span class="sxs-lookup"><span data-stu-id="22a70-215">Debugging, Tracing, and Profiling</span></span>](index.md)
