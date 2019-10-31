---
title: Fuslogvw.exe (Visionneuse du journal de liaison d’assembly)
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
ms.openlocfilehash: 2f0018dca6e5add2c5bc531103a4078307a8c8c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129847"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="47e39-102">Fuslogvw.exe (Visionneuse du journal de liaison d’assembly)</span><span class="sxs-lookup"><span data-stu-id="47e39-102">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>

<span data-ttu-id="47e39-103">La Visionneuse du journal de liaison d’assembly affiche des détails sur les liaisons d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="47e39-103">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="47e39-104">Ces informations vous permettent d'identifier les raisons pour lesquelles le .NET Framework ne parvient pas à trouver un assembly au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="47e39-104">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="47e39-105">Ces échecs résultent généralement d'un assembly déployé au mauvais emplacement, d'une image native qui n'est plus valide ou d'une incompatibilité entre les numéros de version ou les cultures.</span><span class="sxs-lookup"><span data-stu-id="47e39-105">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="47e39-106">L'échec de la localisation d'un assembly par le Common Language Runtime s'affiche d'ordinaire sous la forme de <xref:System.TypeLoadException> dans votre application.</span><span class="sxs-lookup"><span data-stu-id="47e39-106">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47e39-107">Vous devez exécuter fuslogvw.exe avec les droits d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="47e39-107">You must run fuslogvw.exe with administrator privileges.</span></span>

<span data-ttu-id="47e39-108">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47e39-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="47e39-109">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7) avec des informations d’identification d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="47e39-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="47e39-110">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="47e39-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="47e39-111">À l'invite de commandes, tapez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="47e39-111">At the command prompt, type the following:</span></span>

```console
fuslogvw
```

<span data-ttu-id="47e39-112">La visionneuse affiche une entrée pour chaque liaison d'assembly ayant échoué.</span><span class="sxs-lookup"><span data-stu-id="47e39-112">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="47e39-113">Pour chaque échec, la visionneuse décrit l'application qui a lancé la liaison, l'assembly concerné par la liaison (y compris le nom, la version, la culture et la clé publique), ainsi que la date et l'heure de l'échec.</span><span class="sxs-lookup"><span data-stu-id="47e39-113">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>

### <a name="to-change-the-log-location-view"></a><span data-ttu-id="47e39-114">Pour modifier l'affichage de l'emplacement du journal</span><span class="sxs-lookup"><span data-stu-id="47e39-114">To change the log location view</span></span>

1. <span data-ttu-id="47e39-115">Activez la case d’option **Par défaut** pour afficher les échecs de liaison pour tous les types d’applications.</span><span class="sxs-lookup"><span data-stu-id="47e39-115">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="47e39-116">Par défaut, les entrées de journal sont stockées dans des répertoires par utilisateur sur le disque dans le cache WinInet.</span><span class="sxs-lookup"><span data-stu-id="47e39-116">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>

2. <span data-ttu-id="47e39-117">Sélectionnez la case d’option **Personnalisé** pour afficher les échecs de liaison dans un répertoire personnalisé que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="47e39-117">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="47e39-118">Vous devez spécifier l’emplacement personnalisé dans lequel vous souhaitez que l’exécution stocke les journaux en affectant un nom de répertoire valide comme emplacement du journal personnalisé dans la boîte de dialogue **Paramètres du journal**.</span><span class="sxs-lookup"><span data-stu-id="47e39-118">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="47e39-119">Ce répertoire doit être propre et contenir uniquement les fichiers générés par le runtime.</span><span class="sxs-lookup"><span data-stu-id="47e39-119">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="47e39-120">S'il contient un exécutable qui génère un échec devant être enregistré dans le journal, ce dernier ne sera pas enregistré, car l'outil tente de créer un répertoire portant le même nom que l'exécutable.</span><span class="sxs-lookup"><span data-stu-id="47e39-120">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="47e39-121">En outre, toute tentative d'exécution d'un exécutable à partir de l'emplacement du journal échouera.</span><span class="sxs-lookup"><span data-stu-id="47e39-121">In addition, an attempt to run an executable from the log location will fail.</span></span>

    > [!NOTE]
    > <span data-ttu-id="47e39-122">L'emplacement des liaisons par défaut est préférable à l'emplacement des liaisons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="47e39-122">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="47e39-123">Le runtime stocke l’emplacement de liaison par défaut dans le cache WinInet et le nettoie par conséquent automatiquement. Si vous spécifiez un emplacement de liaison personnalisé, vous êtes chargé de le nettoyer.</span><span class="sxs-lookup"><span data-stu-id="47e39-123">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out. If you specify a custom bind location, you are responsible for cleaning it out.</span></span>

### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="47e39-124">Pour afficher des détails sur un échec spécifique</span><span class="sxs-lookup"><span data-stu-id="47e39-124">To view details about a specific failure</span></span>

1. <span data-ttu-id="47e39-125">Sélectionnez le nom de l'application de l'entrée souhaitée dans la visionneuse.</span><span class="sxs-lookup"><span data-stu-id="47e39-125">Select the application name of the desired entry in the viewer.</span></span>

2. <span data-ttu-id="47e39-126">Cliquez sur le bouton **Afficher le journal**.</span><span class="sxs-lookup"><span data-stu-id="47e39-126">Click the **View Log** button.</span></span> <span data-ttu-id="47e39-127">Vous pouvez également double-cliquer sur l'entrée sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="47e39-127">Alternately, you can double-click the selected entry.</span></span>

    <span data-ttu-id="47e39-128">L'outil affiche les détails suivants sur l'échec de la liaison sélectionné :</span><span class="sxs-lookup"><span data-stu-id="47e39-128">The tool displays the following details about the selected bind failure:</span></span>

    - <span data-ttu-id="47e39-129">La raison spécifique de l'échec de la liaison, telle que « fichier introuvable » ou « incompatibilité entre les versions »</span><span class="sxs-lookup"><span data-stu-id="47e39-129">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>

    - <span data-ttu-id="47e39-130">Des informations sur l'application qui a lancé la liaison, parmi lesquelles son nom, le répertoire racine de l'application (AppBase) et le cas échéant, une description du chemin de recherche privé</span><span class="sxs-lookup"><span data-stu-id="47e39-130">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>

    - <span data-ttu-id="47e39-131">L'identité de l'assembly recherché par l'outil</span><span class="sxs-lookup"><span data-stu-id="47e39-131">The identity of the assembly the tool is looking for.</span></span>

    - <span data-ttu-id="47e39-132">Une description des stratégies de version de l'application, de l'éditeur ou de l'administrateur qui ont été appliquées</span><span class="sxs-lookup"><span data-stu-id="47e39-132">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>

    - <span data-ttu-id="47e39-133">Si l’assembly a été trouvé dans le [Global Assembly Cache](../app-domains/gac.md)</span><span class="sxs-lookup"><span data-stu-id="47e39-133">Whether the assembly was found in the [global assembly cache](../app-domains/gac.md).</span></span>

    - <span data-ttu-id="47e39-134">Une liste de toutes les URL recherchées</span><span class="sxs-lookup"><span data-stu-id="47e39-134">A list of all probing URLs.</span></span>

<span data-ttu-id="47e39-135">L'exemple d'entrée de journal suivant montre des informations détaillées sur l'échec d'une liaison d'assembly.</span><span class="sxs-lookup"><span data-stu-id="47e39-135">The following sample log entry shows detailed information about a failed assembly bind.</span></span>

```output
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe
--- A detailed error log follows.

=== Pre-bind state information ===
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
 (Fully-specified)
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\
LOG: Initial PrivatePath = NULL
LOG: Dynamic Base = NULL
LOG: Cache Base = NULL
LOG: AppName = NULL
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
===

LOG: Processing DEVPATH.
LOG: DEVPATH is not set. Falling through to regular bind.
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.
LOG: All probing URLs attempted and failed.
```

### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="47e39-136">Pour supprimer une seule entrée du journal</span><span class="sxs-lookup"><span data-stu-id="47e39-136">To delete a single entry from the log</span></span>

1. <span data-ttu-id="47e39-137">Sélectionnez une entrée dans la visionneuse.</span><span class="sxs-lookup"><span data-stu-id="47e39-137">Select an entry in the viewer.</span></span>

2. <span data-ttu-id="47e39-138">Cliquez sur le bouton **Supprimer l’entrée**.</span><span class="sxs-lookup"><span data-stu-id="47e39-138">Click the **Delete Entry** button.</span></span>

### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="47e39-139">Pour supprimer toutes les entrées du journal</span><span class="sxs-lookup"><span data-stu-id="47e39-139">To delete all entries from the log</span></span>

- <span data-ttu-id="47e39-140">Cliquez sur le bouton **Supprimer tout**.</span><span class="sxs-lookup"><span data-stu-id="47e39-140">Click the **Delete All** button.</span></span>

### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="47e39-141">Pour actualiser l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="47e39-141">To refresh the user interface</span></span>

- <span data-ttu-id="47e39-142">Cliquez sur le bouton **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="47e39-142">Click the **Refresh** button.</span></span> <span data-ttu-id="47e39-143">La visionneuse ne détecte pas automatiquement les nouvelles entrées du journal pendant son exécution.</span><span class="sxs-lookup"><span data-stu-id="47e39-143">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="47e39-144">Vous devez utiliser le bouton **Actualiser** pour les afficher.</span><span class="sxs-lookup"><span data-stu-id="47e39-144">You must use the **Refresh** button to display them.</span></span>

### <a name="to-change-the-log-settings"></a><span data-ttu-id="47e39-145">Pour modifier les paramètres du journal</span><span class="sxs-lookup"><span data-stu-id="47e39-145">To change the log settings</span></span>

- <span data-ttu-id="47e39-146">Cliquez sur le bouton **Paramètres** pour ouvrir la boîte de dialogue **Paramètres du journal**.</span><span class="sxs-lookup"><span data-stu-id="47e39-146">Click the **Settings** button to open the **Log Settings** dialog.</span></span>

### <a name="to-view-the-about-dialog"></a><span data-ttu-id="47e39-147">Pour afficher la boîte de dialogue À propos de</span><span class="sxs-lookup"><span data-stu-id="47e39-147">To view the About dialog</span></span>

- <span data-ttu-id="47e39-148">Cliquez sur le bouton **À propos de**.</span><span class="sxs-lookup"><span data-stu-id="47e39-148">Click the **About** button.</span></span>

## <a name="binding-logs-for-native-images"></a><span data-ttu-id="47e39-149">Liaison de journaux pour des Images natives</span><span class="sxs-lookup"><span data-stu-id="47e39-149">Binding Logs for Native Images</span></span>

<span data-ttu-id="47e39-150">Par défaut, Fuslogvw.exe enregistre les demandes de liaison d'assembly normales.</span><span class="sxs-lookup"><span data-stu-id="47e39-150">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="47e39-151">Vous pouvez également enregistrer des liaisons d’assemblys pour les images natives qui ont été créées à l’aide de l’outil [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="47e39-151">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).</span></span>

#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="47e39-152">Pour enregistrer des liaisons d'assemblys pour les images natives</span><span class="sxs-lookup"><span data-stu-id="47e39-152">To log assembly binds for native images</span></span>

- <span data-ttu-id="47e39-153">Dans le groupe **Catégories de journaux**, activez la case d’option **Images natives**.</span><span class="sxs-lookup"><span data-stu-id="47e39-153">In the **Log Categories** group, select the **Native Images** option button.</span></span>

<span data-ttu-id="47e39-154">Le journal suivant affiche un échec provoqué par une dépendance qui n'existait pas au moment de la création de l'image native pour l'application.</span><span class="sxs-lookup"><span data-stu-id="47e39-154">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="47e39-155">Si les dépendances au moment de l'exécution diffèrent des dépendances lorsque Ngen.exe est exécuté, la liaison à une image native n'est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="47e39-155">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\App.exe
--- A detailed error log follows.

LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\App.exe.
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.
WRN: No matching native image found.
LOG: Bind to native image assembly did not succeed. Use IL image.
```

<span data-ttu-id="47e39-156">Le journal suivant montre un échec de liaison à une image native qui s'est produit parce que les paramètres de sécurité sur l'ordinateur au moment où l'application a été exécutée étaient différents des paramètres de sécurité en vigueur au moment où l'image native a été créée.</span><span class="sxs-lookup"><span data-stu-id="47e39-156">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***

The operation failed.
Bind result: hr = 0x80004005. Unspecified error

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\Application101622.exe
--- A detailed error log follows.

LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\Application101622.exe.
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Dependency evaluation succeeded.
LOG: Validation of dependencies succeeded.
LOG: Start loading all the dependencies into load context.
LOG: Loading of dependencies succeeded.
LOG: Bind to native image succeeded.
Native image has correct version information.
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.
Discarding native image.
```

## <a name="the-log-settings-dialog"></a><span data-ttu-id="47e39-157">La boîte de dialogue Paramètres du journal</span><span class="sxs-lookup"><span data-stu-id="47e39-157">The Log Settings Dialog</span></span>

<span data-ttu-id="47e39-158">Vous pouvez utiliser la boîte de dialogue **Paramètres du journal** pour effectuer les actions suivantes.</span><span class="sxs-lookup"><span data-stu-id="47e39-158">You can use the **Log Settings** dialog to perform the following actions.</span></span>

#### <a name="to-disable-logging"></a><span data-ttu-id="47e39-159">Pour désactiver l'enregistrement</span><span class="sxs-lookup"><span data-stu-id="47e39-159">To disable logging</span></span>

- <span data-ttu-id="47e39-160">Activez la case d’option **Journal désactivé**.</span><span class="sxs-lookup"><span data-stu-id="47e39-160">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="47e39-161">Notez que cette option est sélectionnée par défaut.</span><span class="sxs-lookup"><span data-stu-id="47e39-161">Note that this option is selected by default.</span></span>

#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="47e39-162">Pour enregistrer des liaisons d'assemblys dans les exceptions</span><span class="sxs-lookup"><span data-stu-id="47e39-162">To log assembly binds in exceptions</span></span>

- <span data-ttu-id="47e39-163">Activez la case d’option **Enregistrer dans le texte de l’exception**.</span><span class="sxs-lookup"><span data-stu-id="47e39-163">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="47e39-164">Seules les informations les moins détaillées du journal de fusion sont stockées dans un texte d'exception.</span><span class="sxs-lookup"><span data-stu-id="47e39-164">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="47e39-165">Pour afficher des informations complètes, utilisez un des autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="47e39-165">To view full information, use one of the other settings.</span></span>

  <span data-ttu-id="47e39-166">Consultez la Remarque importante relative aux assemblys chargés comme étant indépendants du domaine.</span><span class="sxs-lookup"><span data-stu-id="47e39-166">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="47e39-167">Pour enregistrer des échecs de liaison d'assemblys</span><span class="sxs-lookup"><span data-stu-id="47e39-167">To log assembly bind failures</span></span>

- <span data-ttu-id="47e39-168">Activez la case d’option **Enregistrer les échecs de liaison sur le disque**.</span><span class="sxs-lookup"><span data-stu-id="47e39-168">Select the **Log bind failures to disk** option button.</span></span>

  <span data-ttu-id="47e39-169">Consultez la Remarque importante relative aux assemblys chargés comme étant indépendants du domaine.</span><span class="sxs-lookup"><span data-stu-id="47e39-169">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="47e39-170">Pour enregistrer toutes les liaisons d'assemblys</span><span class="sxs-lookup"><span data-stu-id="47e39-170">To log all assembly binds</span></span>

- <span data-ttu-id="47e39-171">Activez la case d’option **Enregistrer toutes les liaisons sur le disque**.</span><span class="sxs-lookup"><span data-stu-id="47e39-171">Select the **Log all binds to disk** option button.</span></span>

  <span data-ttu-id="47e39-172">Consultez la Remarque importante relative aux assemblys chargés comme étant indépendants du domaine.</span><span class="sxs-lookup"><span data-stu-id="47e39-172">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="47e39-173">Lorsqu'un assembly est chargé comme étant indépendant du domaine, par exemple en définissant la propriété <xref:System.AppDomainSetup.LoaderOptimization%2A> à <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> ou <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, l'activation de l'enregistrement peut entraîner une fuite de mémoire dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="47e39-173">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="47e39-174">Cela peut arriver si une entrée de journal est faite lorsqu'un module indépendant du domaine est chargé dans un domaine d'application, et qu'ultérieurement le domaine d'application est déchargé.</span><span class="sxs-lookup"><span data-stu-id="47e39-174">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="47e39-175">L'entrée de journal ne peut pas être diffusée avant la fin du processus.</span><span class="sxs-lookup"><span data-stu-id="47e39-175">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="47e39-176">Certains débogueurs activent automatiquement l'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="47e39-176">Some debuggers automatically turn on logging.</span></span>

#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="47e39-177">Pour activer un chemin de journal personnalisé</span><span class="sxs-lookup"><span data-stu-id="47e39-177">To enable a custom log path</span></span>

1. <span data-ttu-id="47e39-178">Activez la case d’option **Activer le chemin de journal personnalisé**.</span><span class="sxs-lookup"><span data-stu-id="47e39-178">Select the **Enable custom log path** option button.</span></span>

2. <span data-ttu-id="47e39-179">Entrez le chemin dans la zone de texte **Chemin du journal personnalisé**.</span><span class="sxs-lookup"><span data-stu-id="47e39-179">Enter the path into the **Custom log path** text box.</span></span>

> [!NOTE]
> <span data-ttu-id="47e39-180">La [visionneuse du journal de liaison d’assembly (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) utilise le cache Internet Explorer (IE) pour stocker son journal de liaison.</span><span class="sxs-lookup"><span data-stu-id="47e39-180">The [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="47e39-181">En raison de la perte d’intégrité occasionnelle du cache IE, la [visionneuse du journal de liaison d’assembly (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) peut parfois cesser d’afficher les nouveaux journaux de liaison dans la fenêtre d’affichage.</span><span class="sxs-lookup"><span data-stu-id="47e39-181">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="47e39-182">Suite à cette perte d’intégrité, l’infrastructure de liaison .NET (fusion) ne peut pas écrire ou lire dans le journal de liaison.</span><span class="sxs-lookup"><span data-stu-id="47e39-182">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="47e39-183">(Ce problème ne se produit pas si vous utilisez un chemin d’accès de journal personnalisé.)  Pour résoudre le problème et permettre à la fusion d’afficher à nouveau les journaux de liaison, effacez le cache IE en supprimant les fichiers Internet temporaires à partir de la boîte de dialogue Options Internet d’Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="47e39-183">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>
>
> <span data-ttu-id="47e39-184">Si votre application non managée héberge le Common Language Runtime en implémentant les interfaces `IHostAssemblyManager` et `IHostAssemblyStore`, les entrées de journal ne peuvent pas être stockées dans le cache de WinInet.</span><span class="sxs-lookup"><span data-stu-id="47e39-184">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="47e39-185">Pour consulter les entrées de journal correspondant aux hôtes personnalisés qui implémentent ces interfaces, vous devez spécifier un autre chemin d'accès au journal.</span><span class="sxs-lookup"><span data-stu-id="47e39-185">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>

#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="47e39-186">Pour activer la journalisation pour les applications qui s'exécutent dans le conteneur d'application Windows</span><span class="sxs-lookup"><span data-stu-id="47e39-186">To enable logging for apps running in the Windows app container</span></span>

1. <span data-ttu-id="47e39-187">Activez un chemin du journal personnalisé, comme décrit dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="47e39-187">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="47e39-188">Par défaut, les applications qui s'exécutent dans le conteneur d'application Windows ont un accès limité au disque dur.</span><span class="sxs-lookup"><span data-stu-id="47e39-188">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="47e39-189">Le répertoire spécifié dispose d'un accès en lecture/écriture pour toutes les applications du conteneur d'application.</span><span class="sxs-lookup"><span data-stu-id="47e39-189">The directory you specify will have read/write access for all apps in the app container.</span></span>

2. <span data-ttu-id="47e39-190">Cochez la case **Activer la journalisation immersive**.</span><span class="sxs-lookup"><span data-stu-id="47e39-190">Select the **Enable immersive logging** check box.</span></span>

    > [!NOTE]
    > <span data-ttu-id="47e39-191">Cette zone est activée uniquement sur Windows 8 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="47e39-191">This box is enabled only on Windows 8 or later.</span></span>

## <a name="see-also"></a><span data-ttu-id="47e39-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47e39-192">See also</span></span>

- <xref:System.TypeLoadException>
- [<span data-ttu-id="47e39-193">Outils</span><span class="sxs-lookup"><span data-stu-id="47e39-193">Tools</span></span>](index.md)
- [<span data-ttu-id="47e39-194">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="47e39-194">Global Assembly Cache</span></span>](../app-domains/gac.md)
- [<span data-ttu-id="47e39-195">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="47e39-195">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="47e39-196">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="47e39-196">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
