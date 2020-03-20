---
title: Dépannage 'Cette application n’a pas pu être lancée'
description: Apprenez ce qu’il faut faire si vous voyez une boîte de dialogue « Cette application ne pourrait pas être lancée ».
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76965904"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Dépannage d’un message d’erreur « Cette application ne pouvait pas être lancé »

Les applications qui sont développées pour le cadre .NET exigent généralement qu’une version spécifique du cadre .NET soit installée sur votre système. Dans certains cas, vous pouvez essayer d’exécuter une application sans une version installée ou la version attendue du cadre .NET présent. Cela produit souvent une boîte de dialogue d’erreur comme ce qui suit:

![Impossible de démarrer cette application](media/application-not-started/app-could-not-be-started.png)

Cela indique généralement l’une des conditions suivantes :

- Une installation cadre .NET sur votre système est devenue corrompue.

- La version du cadre .NET nécessaire à votre application ne peut pas être détectée.

Pour résoudre ce problème afin que vous puissiez exécuter votre demande, faites ce qui suit :

1. Télécharger le [.NET Framework Repair Tool (NetFxRepairTool.exe)](https://www.microsoft.com/download/details.aspx?id=30135). L’outil s’exécute automatiquement lorsque le téléchargement se termine.

1. Si l’outil de réparation cadre .NET recommande toute action supplémentaire, comme celles indiquées dans le chiffre suivant, **sélectionnez Next**.

   ![Changements recommandés](media/application-not-started/repair-tool-recommended-changes.png)

1. Les outils de réparation cadre .NET affichent une boîte de dialogue indiquée dans le chiffre suivant pour indiquer que les changements sont complets. Laissez la boîte de dialogue ouverte pendant que vous essayez de réexécuter votre demande. Cela devrait réussir si l’outil de réparation cadre .NET a identifié et corrigé une installation cadre .NET corrompue.

   ![Changements recommandés](media/application-not-started/repair-tool-changes-complete.png)

1. Si votre application s’exécute avec succès, sélectionnez le bouton **Finition.** Sinon, sélectionnez le bouton **Suivant.**

1. Si vous avez sélectionné le bouton **Suivant,** l’outil de réparation cadre .NET affiche une boîte de dialogue comme ce qui suit. Sélectionnez le bouton **Finition** pour envoyer des informations diagnostiques à Microsoft.

   ![Incapable de résoudre le problème](media/application-not-started/repair-tool-no-resolution.png)

1. Si vous ne pouvez toujours pas exécuter l’application, installez la dernière version du cadre .NET pris en charge par votre version de Windows, comme indiqué dans le tableau suivant.

   |Version de Windows|.NET Installation-cadre|
   |---|---|
   |Mise à jour anniversaire de Windows 10 et versions ultérieures|[.NET Cadre 4.8 Runtime](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, Windows 10 Novembre Mise à jour|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[.NET Cadre 4.8 Runtime](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 SP1|[.NET Cadre 4.8 Runtime](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4.6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > .NET Framework 4.8 est préinstallé sur Windows 10 mai 2019 Mise à jour.

1. Tentative de lancement de l’application.

1. Dans certains cas, vous pouvez voir une boîte de dialogue comme ce qui suit, qui vous demande d’installer le cadre .NET 3.5. Sélectionnez **Télécharger et installer cette fonctionnalité** pour installer le cadre .NET 3.5, puis lancez l’application à nouveau.

   ![Incapable de résoudre le problème](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Voir aussi

- [Configuration requise du .NET Framework](../get-started/system-requirements.md)
- [Guide d’installation du .NET Framework](index.md)
- [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
