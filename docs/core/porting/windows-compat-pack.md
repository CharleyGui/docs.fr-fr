---
title: Utiliser le pack de compatibilité Windows pour porter du code vers .NET Core
description: Découvrez le pack de compatibilité Windows et comment l’utiliser pour déplacer du code .NET Framework existant vers .NET Core
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 71e390881d4e9c7836622abeed49c0ea2e5f7526
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202562"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Utiliser le pack de compatibilité Windows pour porter du code vers .NET Core

Certains des problèmes courants que l’on peut rencontrer en portant du code vers .NET Core sont des dépendances à des API et à des technologies propres à .NET Framework. Le *pack de compatibilité Windows* comporte la plupart de ces technologies, ce qui facilite la création d’applications .NET Core et de bibliothèques .NET Standard.

Ce package est une [extension logique de.NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) qui augmente considérablement l’ensemble d’API et le code existant est compilé sans presque aucune modification. Toutefois, pour respecter l’engagement de .NET Standard (« il s’agit de l’ensemble d’API fourni par toutes les implémentations .NET »), cela ne comprend pas les technologies qui ne peuvent pas fonctionner sur toutes les plateformes, telles que le Registre, WMI (Windows Management Instrumentation), ou les API d’émission de réflexion.

Le *pack de compatibilité Windows* repose sur .NET Standard et permet d’accéder aux technologies Windows uniquement. Il est particulièrement utile pour les clients qui veulent passer à .NET Core, mais envisagent de rester sur Windows pour commencer. Dans ce scénario, le fait de ne pas pouvoir utiliser les technologies Windows uniquement est juste un obstacle à la migration sans aucun avantage en matière d’architecture.

## <a name="package-contents"></a>Contenu du package

Le *pack de compatibilité Windows* est fourni via le package NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et peut être référencé à partir de projets ciblant .NET Core ou .NET Standard.

Il fournit environ 20 000 API, dont des API Windows uniquement ainsi des API multiplateformes des domaines technologiques suivants :

* Pages de codes
* CodeDom
* Configuration
* Services d'annuaire
* Dessin
* ODBC
* Autorisations
* Ports
* Listes de contrôle d’accès Windows
* Windows Communication Foundation (WCF)
* Chiffrement Windows
* Journal des événements Windows
* WMI (Windows Management Instrumentation)
* Compteurs de performances Windows
* Registre Windows
* Mise en cache Windows Runtime
* services Windows

Pour plus d’informations, consultez la [spécification du pack de compatibilité](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Prise en main

1. Avant le portage, veillez à examiner le [processus de portage](index.md).

2. Lors du portage du code existant vers .NET Core ou .NET Standard, installez le package NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Si vous souhaitez rester sur Windows, vous êtes prêt.

4. Si vous souhaitez exécuter l’application .NET Core ou la bibliothèque .NET Standard sur Linux ou macOS, utilisez [l’analyseur d’API](../../standard/analyzers/api-analyzer.md) pour trouver l’usage des API qui ne fonctionnent pas sur toutes les plateformes.

5. Supprimez les usages de ces API, remplacez-les par des alternatives multiplateformes ou protégez-les à l’aide d’une vérification de la plateforme, par exemple :

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

Pour obtenir une démonstration, regardez la [vidéo de Channel 9 sur le pack de compatibilité Windows](https://channel9.msdn.com/Events/Connect/2017/T123).
