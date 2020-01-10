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
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Utiliser le pack de compatibilité Windows pour porter du code vers .NET Core

Certains des problèmes les plus courants rencontrés lors du Portage de code existant vers .NET Core sont des dépendances sur les API et les technologies qui se trouvent uniquement dans .NET Framework. Le *pack de compatibilité Windows* comporte la plupart de ces technologies, ce qui facilite la création d’applications .NET Core et de bibliothèques .NET Standard.

Ce package est une [extension logique de.NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) qui augmente considérablement l’ensemble d’API et le code existant est compilé sans presque aucune modification. Afin de conserver la promesse d' .NET Standard (« il s’agit de l’ensemble d’API fourni par toutes les implémentations .NET »), le Pack n’inclut pas les technologies qui ne peuvent pas fonctionner sur toutes les plateformes, telles que le registre, Windows Management Instrumentation (WMI) ou l’émission de réflexion Interfaces.

Le Pack de compatibilité Windows se trouve au-dessus de .NET Standard et permet d’accéder aux technologies Windows uniquement. Il est particulièrement utile pour les clients qui veulent passer à .NET Core, mais envisagent de rester sur Windows pour commencer. Dans ce scénario, le fait de ne pas pouvoir utiliser les technologies Windows uniquement est un obstacle à la migration sans avantages architecturaux.

## <a name="package-contents"></a>Contenu du package

Le Pack de compatibilité Windows est fourni via le [package NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et peut être référencé à partir des projets qui ciblent .net Core ou .NET standard.

Il fournit environ 20 000 API, dont des API Windows uniquement ainsi des API multiplateformes des domaines technologiques suivants :

- Pages de codes
- CodeDom
- Configuration
- Services d'annuaire
- Dessin
- ODBC
- Autorisations
- Ports
- Listes de contrôle d’accès Windows
- Windows Communication Foundation (WCF)
- Chiffrement Windows
- Journal des événements Windows
- Windows Management Instrumentation (WMI)
- Compteurs de performances Windows
- Registre Windows
- Mise en cache Windows Runtime
- Services Windows

Pour plus d’informations, consultez la [spécification du pack de compatibilité](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Prise en main

1. Avant de procéder au Portage, veillez à examiner le [processus de Portage](index.md).

2. Lors du Portage du code existant vers .NET Core ou .NET Standard, installez le [package NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

   Si vous souhaitez rester sur Windows, vous êtes prêt.

3. Si vous souhaitez exécuter l’application .NET Core ou la bibliothèque .NET Standard sur Linux ou macOS, utilisez [l’analyseur d’API](../../standard/analyzers/api-analyzer.md) pour trouver l’usage des API qui ne fonctionnent pas sur toutes les plateformes.

4. Supprimez les usages de ces API, remplacez-les par des alternatives multiplateformes ou protégez-les à l’aide d’une vérification de la plateforme, par exemple :

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
