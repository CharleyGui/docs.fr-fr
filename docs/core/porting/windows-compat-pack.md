---
title: Utiliser le pack de compatibilité Windows pour porter du code vers .NET Core
description: Découvrez le Pack de compatibilité Windows et comment pouvez-vous l’utiliser pour porter le code .NET Framework existant vers .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733612"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="993e2-103">Utiliser le pack de compatibilité Windows pour porter du code vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="993e2-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="993e2-104">Certains des problèmes les plus courants rencontrés lors du Portage de code existant vers .NET Core sont des dépendances sur les API et les technologies qui se trouvent uniquement dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="993e2-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="993e2-105">Le *pack de compatibilité Windows* comporte la plupart de ces technologies, ce qui facilite la création d’applications .NET Core et de bibliothèques .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="993e2-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="993e2-106">Le Pack de compatibilité est une [extension logique de .NET Standard 2,0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) qui augmente considérablement l’ensemble des API.</span><span class="sxs-lookup"><span data-stu-id="993e2-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="993e2-107">Le code existant est compilé avec presque aucune modification.</span><span class="sxs-lookup"><span data-stu-id="993e2-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="993e2-108">Pour conserver sa promesse de « l’ensemble des API fournies par toutes les implémentations .NET », .NET Standard n’inclut pas les technologies qui ne peuvent pas fonctionner sur toutes les plateformes, telles que le registre, les Windows Management Instrumentation (WMI) ou les API de l’émission de réflexion.</span><span class="sxs-lookup"><span data-stu-id="993e2-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="993e2-109">Le Pack de compatibilité Windows se trouve au-dessus de .NET Standard et fournit un accès à ces technologies Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="993e2-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="993e2-110">Elle est particulièrement utile pour les clients qui souhaitent passer à .NET Core, mais elles envisagent de rester sur Windows, au moins en tant que première étape.</span><span class="sxs-lookup"><span data-stu-id="993e2-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="993e2-111">Dans ce scénario, la possibilité d’utiliser des technologies Windows uniquement supprime le obstacle à la migration.</span><span class="sxs-lookup"><span data-stu-id="993e2-111">In that scenario, being able to use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="993e2-112">Contenu du package</span><span class="sxs-lookup"><span data-stu-id="993e2-112">Package contents</span></span>

<span data-ttu-id="993e2-113">Le Pack de compatibilité Windows est fourni via le [package NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et peut être référencé à partir des projets qui ciblent .net Core ou .NET standard.</span><span class="sxs-lookup"><span data-stu-id="993e2-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="993e2-114">Il fournit environ 20 000 API, dont des API Windows uniquement ainsi des API multiplateformes des domaines technologiques suivants :</span><span class="sxs-lookup"><span data-stu-id="993e2-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="993e2-115">Pages de codes</span><span class="sxs-lookup"><span data-stu-id="993e2-115">Code Pages</span></span>
- <span data-ttu-id="993e2-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="993e2-116">CodeDom</span></span>
- <span data-ttu-id="993e2-117">Configuration</span><span class="sxs-lookup"><span data-stu-id="993e2-117">Configuration</span></span>
- <span data-ttu-id="993e2-118">Services d'annuaire</span><span class="sxs-lookup"><span data-stu-id="993e2-118">Directory Services</span></span>
- <span data-ttu-id="993e2-119">Dessin</span><span class="sxs-lookup"><span data-stu-id="993e2-119">Drawing</span></span>
- <span data-ttu-id="993e2-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="993e2-120">ODBC</span></span>
- <span data-ttu-id="993e2-121">Autorisations</span><span class="sxs-lookup"><span data-stu-id="993e2-121">Permissions</span></span>
- <span data-ttu-id="993e2-122">Ports</span><span class="sxs-lookup"><span data-stu-id="993e2-122">Ports</span></span>
- <span data-ttu-id="993e2-123">Listes de contrôle d’accès Windows</span><span class="sxs-lookup"><span data-stu-id="993e2-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="993e2-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="993e2-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="993e2-125">Chiffrement Windows</span><span class="sxs-lookup"><span data-stu-id="993e2-125">Windows Cryptography</span></span>
- <span data-ttu-id="993e2-126">Journal des événements Windows</span><span class="sxs-lookup"><span data-stu-id="993e2-126">Windows EventLog</span></span>
- <span data-ttu-id="993e2-127">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="993e2-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="993e2-128">Compteurs de performances Windows</span><span class="sxs-lookup"><span data-stu-id="993e2-128">Windows Performance Counters</span></span>
- <span data-ttu-id="993e2-129">Registre Windows</span><span class="sxs-lookup"><span data-stu-id="993e2-129">Windows Registry</span></span>
- <span data-ttu-id="993e2-130">Mise en cache Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="993e2-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="993e2-131">Services Windows</span><span class="sxs-lookup"><span data-stu-id="993e2-131">Windows Services</span></span>

<span data-ttu-id="993e2-132">Pour plus d’informations, consultez la [spécification du pack de compatibilité](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="993e2-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="993e2-133">Prise en main</span><span class="sxs-lookup"><span data-stu-id="993e2-133">Get started</span></span>

1. <span data-ttu-id="993e2-134">Avant de procéder au Portage, veillez à examiner le [processus de Portage](index.md).</span><span class="sxs-lookup"><span data-stu-id="993e2-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="993e2-135">Lors du Portage du code existant vers .NET Core ou .NET Standard, installez le [package NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="993e2-135">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="993e2-136">Si vous souhaitez rester sur Windows, vous êtes prêt.</span><span class="sxs-lookup"><span data-stu-id="993e2-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="993e2-137">Si vous souhaitez exécuter l’application .NET Core ou la bibliothèque .NET Standard sur Linux ou macOS, utilisez [l’analyseur d’API](../../standard/analyzers/api-analyzer.md) pour trouver l’usage des API qui ne fonctionnent pas sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="993e2-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="993e2-138">Supprimez les usages de ces API, remplacez-les par des alternatives multiplateformes ou protégez-les à l’aide d’une vérification de la plateforme, par exemple :</span><span class="sxs-lookup"><span data-stu-id="993e2-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

<span data-ttu-id="993e2-139">Pour obtenir une démonstration, regardez la [vidéo de Channel 9 sur le pack de compatibilité Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="993e2-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
