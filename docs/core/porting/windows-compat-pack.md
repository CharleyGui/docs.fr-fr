---
title: Utiliser le pack de compatibilité Windows pour porter du code vers .NET Core
description: Découvrez le Pack de compatibilité Windows et comment pouvez-vous l’utiliser pour porter le code .NET Framework existant vers .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 65530987a3cded941b6a292118ed9bfdb6f5b86c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715467"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="07ddf-103">Utiliser le pack de compatibilité Windows pour porter du code vers .NET Core</span><span class="sxs-lookup"><span data-stu-id="07ddf-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="07ddf-104">Certains des problèmes les plus courants rencontrés lors du Portage de code existant vers .NET Core sont des dépendances sur les API et les technologies qui se trouvent uniquement dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07ddf-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="07ddf-105">Le *pack de compatibilité Windows* comporte la plupart de ces technologies, ce qui facilite la création d’applications .NET Core et de bibliothèques .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="07ddf-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="07ddf-106">Ce package est une [extension logique de.NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) qui augmente considérablement l’ensemble d’API et le code existant est compilé sans presque aucune modification.</span><span class="sxs-lookup"><span data-stu-id="07ddf-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="07ddf-107">Afin de conserver la promesse d' .NET Standard (« il s’agit de l’ensemble d’API fourni par toutes les implémentations .NET »), le Pack n’inclut pas les technologies qui ne peuvent pas fonctionner sur toutes les plateformes, telles que le registre, Windows Management Instrumentation (WMI) ou l’émission de réflexion Interfaces.</span><span class="sxs-lookup"><span data-stu-id="07ddf-107">In order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), the pack doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="07ddf-108">Le Pack de compatibilité Windows se trouve au-dessus de .NET Standard et permet d’accéder aux technologies Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="07ddf-108">The Windows Compatibility Pack sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="07ddf-109">Il est particulièrement utile pour les clients qui veulent passer à .NET Core, mais envisagent de rester sur Windows pour commencer.</span><span class="sxs-lookup"><span data-stu-id="07ddf-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="07ddf-110">Dans ce scénario, le fait de ne pas pouvoir utiliser les technologies Windows uniquement est un obstacle à la migration sans avantages architecturaux.</span><span class="sxs-lookup"><span data-stu-id="07ddf-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with no architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="07ddf-111">Contenu du package</span><span class="sxs-lookup"><span data-stu-id="07ddf-111">Package contents</span></span>

<span data-ttu-id="07ddf-112">Le Pack de compatibilité Windows est fourni via le [package NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et peut être référencé à partir des projets qui ciblent .net Core ou .NET standard.</span><span class="sxs-lookup"><span data-stu-id="07ddf-112">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="07ddf-113">Il fournit environ 20 000 API, dont des API Windows uniquement ainsi des API multiplateformes des domaines technologiques suivants :</span><span class="sxs-lookup"><span data-stu-id="07ddf-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="07ddf-114">Pages de codes</span><span class="sxs-lookup"><span data-stu-id="07ddf-114">Code Pages</span></span>
- <span data-ttu-id="07ddf-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="07ddf-115">CodeDom</span></span>
- <span data-ttu-id="07ddf-116">Configuration</span><span class="sxs-lookup"><span data-stu-id="07ddf-116">Configuration</span></span>
- <span data-ttu-id="07ddf-117">Services d'annuaire</span><span class="sxs-lookup"><span data-stu-id="07ddf-117">Directory Services</span></span>
- <span data-ttu-id="07ddf-118">Dessin</span><span class="sxs-lookup"><span data-stu-id="07ddf-118">Drawing</span></span>
- <span data-ttu-id="07ddf-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="07ddf-119">ODBC</span></span>
- <span data-ttu-id="07ddf-120">Autorisations</span><span class="sxs-lookup"><span data-stu-id="07ddf-120">Permissions</span></span>
- <span data-ttu-id="07ddf-121">Ports</span><span class="sxs-lookup"><span data-stu-id="07ddf-121">Ports</span></span>
- <span data-ttu-id="07ddf-122">Listes de contrôle d’accès Windows</span><span class="sxs-lookup"><span data-stu-id="07ddf-122">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="07ddf-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="07ddf-123">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="07ddf-124">Chiffrement Windows</span><span class="sxs-lookup"><span data-stu-id="07ddf-124">Windows Cryptography</span></span>
- <span data-ttu-id="07ddf-125">Journal des événements Windows</span><span class="sxs-lookup"><span data-stu-id="07ddf-125">Windows EventLog</span></span>
- <span data-ttu-id="07ddf-126">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="07ddf-126">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="07ddf-127">Compteurs de performances Windows</span><span class="sxs-lookup"><span data-stu-id="07ddf-127">Windows Performance Counters</span></span>
- <span data-ttu-id="07ddf-128">Registre Windows</span><span class="sxs-lookup"><span data-stu-id="07ddf-128">Windows Registry</span></span>
- <span data-ttu-id="07ddf-129">Mise en cache Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="07ddf-129">Windows Runtime Caching</span></span>
- <span data-ttu-id="07ddf-130">Services Windows</span><span class="sxs-lookup"><span data-stu-id="07ddf-130">Windows Services</span></span>

<span data-ttu-id="07ddf-131">Pour plus d’informations, consultez la [spécification du pack de compatibilité](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="07ddf-131">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="07ddf-132">Prise en main</span><span class="sxs-lookup"><span data-stu-id="07ddf-132">Get started</span></span>

1. <span data-ttu-id="07ddf-133">Avant de procéder au Portage, veillez à examiner le [processus de Portage](index.md).</span><span class="sxs-lookup"><span data-stu-id="07ddf-133">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="07ddf-134">Lors du Portage du code existant vers .NET Core ou .NET Standard, installez le [package NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="07ddf-134">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="07ddf-135">Si vous souhaitez rester sur Windows, vous êtes prêt.</span><span class="sxs-lookup"><span data-stu-id="07ddf-135">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="07ddf-136">Si vous souhaitez exécuter l’application .NET Core ou la bibliothèque .NET Standard sur Linux ou macOS, utilisez [l’analyseur d’API](../../standard/analyzers/api-analyzer.md) pour trouver l’usage des API qui ne fonctionnent pas sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="07ddf-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="07ddf-137">Supprimez les usages de ces API, remplacez-les par des alternatives multiplateformes ou protégez-les à l’aide d’une vérification de la plateforme, par exemple :</span><span class="sxs-lookup"><span data-stu-id="07ddf-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="07ddf-138">Pour obtenir une démonstration, regardez la [vidéo de Channel 9 sur le pack de compatibilité Windows](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="07ddf-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
