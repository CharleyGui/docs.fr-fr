---
title: Utiliser le pack de compatibilité Windows pour porter du code vers .NET Core
description: Découvrez le pack de compatibilité Windows et comment pouvez-vous l’utiliser pour porter le code cadre .NET existant à .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 166259ca37a2005d67f6c545e4843a940f05fb71
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228638"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Utiliser le pack de compatibilité Windows pour porter du code vers .NET Core

Certains des problèmes les plus courants trouvés lors du portage du code existant à .NET Core sont des dépendances sur les API et les technologies qui ne se trouvent que dans .NET Framework. Le *pack de compatibilité Windows* comporte la plupart de ces technologies, ce qui facilite la création d’applications .NET Core et de bibliothèques .NET Standard.

Le pack de compatibilité est une extension logique [de .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) qui augmente considérablement l’ensemble API. Le code existant compile avec presque aucune modification. Pour tenir sa promesse de « l’ensemble des API que toutes les implémentations .NET fournissent », .NET Standard n’inclut pas les technologies qui ne peuvent pas fonctionner sur toutes les plates-formes, telles que le registre, l’instrumentation de gestion de Windows (WMI), ou les API émettant des réflexions. Le Pack de Compatibilité Windows se trouve au-dessus de la norme .NET et donne accès à ces technologies Windows uniquement. Il est particulièrement utile pour les clients qui veulent passer à .NET Core, mais l’intention de rester sur Windows, au moins comme une première étape. Dans ce scénario, être capable d’utiliser uniquement les technologies Windows élimine l’obstacle de migration.

## <a name="package-contents"></a>Contenu d'un package

Le pack de compatibilité Windows est fourni via le [paquet NuGet Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) et peut être référencé à partir de projets qui ciblent .NET Core ou .NET Standard.

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

Pour plus d’informations, consultez la [spécification du pack de compatibilité](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md).

## <a name="get-started"></a>Prise en main

1. Avant le portage, assurez-vous de jeter un oeil au [processus de portage](index.md).

2. Lorsque vous transférez le code existant à .NET Core ou .NET Standard, installez le [paquet NuGet Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

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
