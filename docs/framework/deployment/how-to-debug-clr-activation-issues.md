---
title: Guide pratique pour déboguer les problèmes d’activation du CLR
description: Consultez Comment déboguer des problèmes d’activation d’common language runtime (CLR) dans .NET. Afficher et déboguer les journaux d’activation du CLR, ce qui peut être utile pour déterminer les causes racines.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 5215e82aebf93fa8d6d1937563ab348126a01d97
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622612"
---
# <a name="how-to-debug-clr-activation-issues"></a><span data-ttu-id="782b9-104">Guide pratique pour déboguer les problèmes d’activation du CLR</span><span class="sxs-lookup"><span data-stu-id="782b9-104">How to debug CLR activation issues</span></span>

<span data-ttu-id="782b9-105">Si vous avez des difficultés à faire en sorte que votre application s’exécute avec la version correcte du Common Language Runtime (CLR), vous pouvez afficher et déboguer les journaux d’activation du CLR.</span><span class="sxs-lookup"><span data-stu-id="782b9-105">If you encounter problems in getting your application to run with the correct version of the common language runtime (CLR), you can view and debug CLR activation logs.</span></span> <span data-ttu-id="782b9-106">Ces journaux peuvent être très utiles pour déterminer la cause d’un problème d’activation, quand votre application charge une autre version du CLR que celle prévue ou ne charge pas du tout le CLR.</span><span class="sxs-lookup"><span data-stu-id="782b9-106">These logs can be very useful in determining the root cause of an activation issue, when your application either loads a different CLR version than expected or doesn't load the CLR at all.</span></span> <span data-ttu-id="782b9-107">L’article [Erreurs d’initialisation de .NET Framework : gérer l’expérience utilisateur](initialization-errors-managing-the-user-experience.md) décrit l’expérience quand aucun CLR n’est trouvé pour une application.</span><span class="sxs-lookup"><span data-stu-id="782b9-107">The [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) discusses the experience when no CLR is found for an application.</span></span>

<span data-ttu-id="782b9-108">Vous pouvez activer la journalisation de l’activation du CLR à l’échelle du système à l’aide d’une clé de Registre HKEY_LOCAL_MACHINE ou d’une variable d’environnement système.</span><span class="sxs-lookup"><span data-stu-id="782b9-108">CLR activation logging can be enabled system-wide by using an HKEY_LOCAL_MACHINE registry key or a system environment variable.</span></span> <span data-ttu-id="782b9-109">Le journal sera généré jusqu’à ce que l’entrée de Registre ou la variable d’environnement soit supprimée.</span><span class="sxs-lookup"><span data-stu-id="782b9-109">The log will be generated until the registry entry or the environment variable is removed.</span></span> <span data-ttu-id="782b9-110">Vous pouvez également utiliser une variable d’environnement utilisateur ou locale au processus pour activer la journalisation avec une portée et une durée différentes.</span><span class="sxs-lookup"><span data-stu-id="782b9-110">Alternatively, you can use a user or process-local environment variable to enable logging with a different scope and duration.</span></span>

<span data-ttu-id="782b9-111">Il ne faut pas confondre les journaux d’activation du CLR avec les [journaux de liaison d’assembly](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), qui sont totalement différents.</span><span class="sxs-lookup"><span data-stu-id="782b9-111">CLR activation logs shouldn't be confused with [assembly binding logs](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), which are entirely different.</span></span>

## <a name="to-enable-clr-activation-logging"></a><span data-ttu-id="782b9-112">Pour activer la journalisation de l’activation du CLR</span><span class="sxs-lookup"><span data-stu-id="782b9-112">To enable CLR activation logging</span></span>

### <a name="using-the-registry"></a><span data-ttu-id="782b9-113">À l’aide du Registre</span><span class="sxs-lookup"><span data-stu-id="782b9-113">Using the registry</span></span>

1. <span data-ttu-id="782b9-114">Dans l’Éditeur du Registre, accédez au dossier HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (sur un ordinateur 32 bits) ou HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework (sur un ordinateur 64 bits).</span><span class="sxs-lookup"><span data-stu-id="782b9-114">In the Registry Editor, navigate to HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework (on a 32-bit computer) or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework folder (on a 64-bit computer).</span></span>

2. <span data-ttu-id="782b9-115">Ajoutez une valeur de chaîne nommée `CLRLoadLogDir` et affectez-lui le chemin complet d’un répertoire existant où vous souhaitez stocker les journaux d’activation du CLR.</span><span class="sxs-lookup"><span data-stu-id="782b9-115">Add a string value named `CLRLoadLogDir`, and set it to the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

<span data-ttu-id="782b9-116">La journalisation de l’activation reste active jusqu’à ce que vous supprimiez la valeur de chaîne.</span><span class="sxs-lookup"><span data-stu-id="782b9-116">Activation logging remains enabled until you remove the string value.</span></span>

### <a name="using-an-environment-variable"></a><span data-ttu-id="782b9-117">À l’aide d’une variable d’environnement</span><span class="sxs-lookup"><span data-stu-id="782b9-117">Using an environment variable</span></span>

- <span data-ttu-id="782b9-118">Affectez à la variable d’environnement `COMPLUS_CLRLoadLogDir` une chaîne qui représente le chemin complet d’un répertoire existant où vous souhaitez stocker les journaux d’activation du CLR.</span><span class="sxs-lookup"><span data-stu-id="782b9-118">Set the `COMPLUS_CLRLoadLogDir` environment variable to a string that represents the full path of an existing directory where you'd like to store CLR activation logs.</span></span>

    <span data-ttu-id="782b9-119">La façon dont vous définissez la variable d’environnement détermine sa portée :</span><span class="sxs-lookup"><span data-stu-id="782b9-119">How you set the environment variable determines its scope:</span></span>

  - <span data-ttu-id="782b9-120">Si vous la définissez au niveau du système, la journalisation de l’activation est activée pour toutes les applications .NET Framework sur cet ordinateur jusqu’à ce que la variable d’environnement soit supprimée.</span><span class="sxs-lookup"><span data-stu-id="782b9-120">If you set it at the system level, activation logging is enabled for all .NET Framework applications on that computer until the environment variable is removed.</span></span>

  - <span data-ttu-id="782b9-121">Si vous la définissez au niveau de l’utilisateur, la journalisation de l’activation est activée uniquement pour le compte d’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="782b9-121">If you set it at the user level, activation logging is enabled only for the current user account.</span></span> <span data-ttu-id="782b9-122">La journalisation continue jusqu’à ce que la variable d’environnement soit supprimée.</span><span class="sxs-lookup"><span data-stu-id="782b9-122">Logging continues until the environment variable is removed.</span></span>

  - <span data-ttu-id="782b9-123">Si vous la définissez à l’intérieur du processus avant le chargement du CLR, la journalisation de l’activation est activée jusqu’à ce que le processus se termine.</span><span class="sxs-lookup"><span data-stu-id="782b9-123">If you set it from within the process before loading the CLR, activation logging is enabled until the process terminates.</span></span>

  - <span data-ttu-id="782b9-124">Si vous la définissez à une invite de commandes avant d’exécuter une application, la journalisation de l’activation est activée pour toute application exécutée à partir de cette invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="782b9-124">If you set it at a command prompt before you run an application, activation logging is enabled for any application that is run from that command prompt.</span></span>

    <span data-ttu-id="782b9-125">Par exemple, pour stocker les journaux d’activation dans le répertoire c:\clrloadlogs avec une portée au niveau du processus, ouvrez une fenêtre d’invite de commandes et tapez ce qui suit avant d’exécuter l’application :</span><span class="sxs-lookup"><span data-stu-id="782b9-125">For example, to store activation logs in the c:\clrloadlogs directory with process-level scope, open a Command Prompt window and type the following before you run the application:</span></span>

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a><span data-ttu-id="782b9-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="782b9-126">Example</span></span>

<span data-ttu-id="782b9-127">Les journaux d’activation du CLR fournissent une grande quantité de données sur l’activation du CLR et l’utilisation des API d’hébergement du CLR.</span><span class="sxs-lookup"><span data-stu-id="782b9-127">CLR activation logs provide a large amount of data about CLR activation and the use of the CLR hosting APIs.</span></span> <span data-ttu-id="782b9-128">La plupart de ces données sont utilisées en interne par Microsoft, mais certaines peuvent également être utiles aux développeurs, comme décrit dans cet article.</span><span class="sxs-lookup"><span data-stu-id="782b9-128">Most of this data is used internally by Microsoft, but some of the data can also be useful to developers, as described in this article.</span></span>

<span data-ttu-id="782b9-129">Le journal reflète l’ordre dans lequel les API d’hébergement du CLR ont été appelées.</span><span class="sxs-lookup"><span data-stu-id="782b9-129">The log reflects the order in which the CLR hosting APIs were called.</span></span> <span data-ttu-id="782b9-130">Il inclut également des données utiles relatives à l’ensemble des runtimes installés détectés sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="782b9-130">It also includes useful data about the set of installed runtimes detected on the computer.</span></span> <span data-ttu-id="782b9-131">Le format du journal d’activation du CLR n’est pas documenté, mais peut être utilisé pour aider les développeurs qui doivent résoudre des problèmes d’activation du CLR.</span><span class="sxs-lookup"><span data-stu-id="782b9-131">The CLR activation log format is not itself documented, but can be used to aid developers who need to resolve CLR activation issues.</span></span>

> [!NOTE]
> <span data-ttu-id="782b9-132">Vous ne pouvez pas ouvrir un journal d’activation tant que le processus qui utilise le CLR ne s’est pas arrêté.</span><span class="sxs-lookup"><span data-stu-id="782b9-132">You cannot open an activation log until the process that uses the CLR has terminated.</span></span>

> [!NOTE]
> <span data-ttu-id="782b9-133">Les journaux d’activation du CLR ne sont pas localisés ; ils sont toujours générés en langue anglaise.</span><span class="sxs-lookup"><span data-stu-id="782b9-133">CLR activation logs are not localized; they are always generated in the English language.</span></span>

<span data-ttu-id="782b9-134">Dans l’exemple de journal d’activation suivant, les informations les plus utiles sont mises en surbrillance et décrites après le journal.</span><span class="sxs-lookup"><span data-stu-id="782b9-134">In the following example of an activation log, the most useful information is highlighted and described after the log.</span></span>

```output
532,205950.367,CLR Loading log for C:\Tests\myapp.exe
532,205950.367,Log started at 4:26:12 PM on 10/6/2011
532,205950.367,-----------------------------------
532,205950.382,FunctionCall: _CorExeMain
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
532,205950.382,Input values for ComputeVersionString follow this line
532,205950.382,-----------------------------------
532,205950.382,Default Application Name: C:\Tests\myapp.exe
532,205950.382,IsLegacyBind is: 0
532,205950.382,IsCapped is 0
532,205950.382,SkuCheckFlags are 0
532,205950.382,ShouldEmulateExeLaunch is 0
532,205950.382,LegacyBindRequired is 0
532,205950.382,-----------------------------------
532,205950.382,Parsing config file: C:\Tests\myapp.exe
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.
532,205950.398,SEM_FAILCRITICALERRORS is set to 0
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
532,205950.398,FunctionCall: RealDllMain. Reason: 0
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0
```

- <span data-ttu-id="782b9-135">**CLR Loading log** fournit le chemin du fichier exécutable qui a démarré le processus ayant chargé du code managé.</span><span class="sxs-lookup"><span data-stu-id="782b9-135">**CLR Loading log** provides the path to the executable that started the process that loaded managed code.</span></span> <span data-ttu-id="782b9-136">Notez qu’il peut s’agir d’un hôte natif.</span><span class="sxs-lookup"><span data-stu-id="782b9-136">Note that this could be a native host.</span></span>

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- <span data-ttu-id="782b9-137">**Installed Runtime** est l’ensemble des versions du CLR installées sur l’ordinateur qui sont des candidats pour la demande d’activation.</span><span class="sxs-lookup"><span data-stu-id="782b9-137">**Installed Runtime** is the set of CLR versions installed on the computer that are candidates for the activation request.</span></span>

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- <span data-ttu-id="782b9-138">**built with version** est la version du CLR qui a été utilisée pour générer le fichier binaire fourni à une méthode comme [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span><span class="sxs-lookup"><span data-stu-id="782b9-138">**built with version** is the version of the CLR that was used to build the binary that was provided to a method such as [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).</span></span>

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- <span data-ttu-id="782b9-139">**feature-on-demand installation** fait référence à l’activation du .NET Framework 3.5 sur Windows 8.</span><span class="sxs-lookup"><span data-stu-id="782b9-139">**feature-on-demand installation** refers to enabling the .NET Framework 3.5 on Windows 8.</span></span> <span data-ttu-id="782b9-140">Pour plus d’informations sur ce scénario, consultez [Erreurs d’initialisation de .NET Framework : gérer l’expérience utilisateur](initialization-errors-managing-the-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="782b9-140">See [.NET Framework Initialization Errors: Managing the User Experience](initialization-errors-managing-the-user-experience.md) for more information about this scenario.</span></span>

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a><span data-ttu-id="782b9-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="782b9-141">See also</span></span>

- [<span data-ttu-id="782b9-142">Déploiement</span><span class="sxs-lookup"><span data-stu-id="782b9-142">Deployment</span></span>](index.md)
- [<span data-ttu-id="782b9-143">Comment : configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="782b9-143">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
