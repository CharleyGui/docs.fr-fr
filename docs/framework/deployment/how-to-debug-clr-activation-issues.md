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
# <a name="how-to-debug-clr-activation-issues"></a>Guide pratique pour déboguer les problèmes d’activation du CLR

Si vous avez des difficultés à faire en sorte que votre application s’exécute avec la version correcte du Common Language Runtime (CLR), vous pouvez afficher et déboguer les journaux d’activation du CLR. Ces journaux peuvent être très utiles pour déterminer la cause d’un problème d’activation, quand votre application charge une autre version du CLR que celle prévue ou ne charge pas du tout le CLR. L’article [Erreurs d’initialisation de .NET Framework : gérer l’expérience utilisateur](initialization-errors-managing-the-user-experience.md) décrit l’expérience quand aucun CLR n’est trouvé pour une application.

Vous pouvez activer la journalisation de l’activation du CLR à l’échelle du système à l’aide d’une clé de Registre HKEY_LOCAL_MACHINE ou d’une variable d’environnement système. Le journal sera généré jusqu’à ce que l’entrée de Registre ou la variable d’environnement soit supprimée. Vous pouvez également utiliser une variable d’environnement utilisateur ou locale au processus pour activer la journalisation avec une portée et une durée différentes.

Il ne faut pas confondre les journaux d’activation du CLR avec les [journaux de liaison d’assembly](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), qui sont totalement différents.

## <a name="to-enable-clr-activation-logging"></a>Pour activer la journalisation de l’activation du CLR

### <a name="using-the-registry"></a>À l’aide du Registre

1. Dans l’Éditeur du Registre, accédez au dossier HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (sur un ordinateur 32 bits) ou HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework (sur un ordinateur 64 bits).

2. Ajoutez une valeur de chaîne nommée `CLRLoadLogDir` et affectez-lui le chemin complet d’un répertoire existant où vous souhaitez stocker les journaux d’activation du CLR.

La journalisation de l’activation reste active jusqu’à ce que vous supprimiez la valeur de chaîne.

### <a name="using-an-environment-variable"></a>À l’aide d’une variable d’environnement

- Affectez à la variable d’environnement `COMPLUS_CLRLoadLogDir` une chaîne qui représente le chemin complet d’un répertoire existant où vous souhaitez stocker les journaux d’activation du CLR.

    La façon dont vous définissez la variable d’environnement détermine sa portée :

  - Si vous la définissez au niveau du système, la journalisation de l’activation est activée pour toutes les applications .NET Framework sur cet ordinateur jusqu’à ce que la variable d’environnement soit supprimée.

  - Si vous la définissez au niveau de l’utilisateur, la journalisation de l’activation est activée uniquement pour le compte d’utilisateur actuel. La journalisation continue jusqu’à ce que la variable d’environnement soit supprimée.

  - Si vous la définissez à l’intérieur du processus avant le chargement du CLR, la journalisation de l’activation est activée jusqu’à ce que le processus se termine.

  - Si vous la définissez à une invite de commandes avant d’exécuter une application, la journalisation de l’activation est activée pour toute application exécutée à partir de cette invite de commandes.

    Par exemple, pour stocker les journaux d’activation dans le répertoire c:\clrloadlogs avec une portée au niveau du processus, ouvrez une fenêtre d’invite de commandes et tapez ce qui suit avant d’exécuter l’application :

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a>Exemple

Les journaux d’activation du CLR fournissent une grande quantité de données sur l’activation du CLR et l’utilisation des API d’hébergement du CLR. La plupart de ces données sont utilisées en interne par Microsoft, mais certaines peuvent également être utiles aux développeurs, comme décrit dans cet article.

Le journal reflète l’ordre dans lequel les API d’hébergement du CLR ont été appelées. Il inclut également des données utiles relatives à l’ensemble des runtimes installés détectés sur l’ordinateur. Le format du journal d’activation du CLR n’est pas documenté, mais peut être utilisé pour aider les développeurs qui doivent résoudre des problèmes d’activation du CLR.

> [!NOTE]
> Vous ne pouvez pas ouvrir un journal d’activation tant que le processus qui utilise le CLR ne s’est pas arrêté.

> [!NOTE]
> Les journaux d’activation du CLR ne sont pas localisés ; ils sont toujours générés en langue anglaise.

Dans l’exemple de journal d’activation suivant, les informations les plus utiles sont mises en surbrillance et décrites après le journal.

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

- **CLR Loading log** fournit le chemin du fichier exécutable qui a démarré le processus ayant chargé du code managé. Notez qu’il peut s’agir d’un hôte natif.

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- **Installed Runtime** est l’ensemble des versions du CLR installées sur l’ordinateur qui sont des candidats pour la demande d’activation.

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- **built with version** est la version du CLR qui a été utilisée pour générer le fichier binaire fourni à une méthode comme [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- **feature-on-demand installation** fait référence à l’activation du .NET Framework 3.5 sur Windows 8. Pour plus d’informations sur ce scénario, consultez [Erreurs d’initialisation de .NET Framework : gérer l’expérience utilisateur](initialization-errors-managing-the-user-experience.md).

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a>Voir aussi

- [Déploiement](index.md)
- [Comment : configurer une application pour prendre en charge .NET Framework 4 ou versions ultérieures](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
