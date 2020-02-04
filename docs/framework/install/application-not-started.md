---
title: Résolution des problèmes « cette application n’a pas pu être démarrée »
description: Découvrez comment faire si la boîte de dialogue « cette application n’a pas pu être démarrée » s’affiche.
ms.date: 09/05/2019
ms.openlocfilehash: 864c6ea23e9a048f060eee39d904bd4377be5084
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965904"
---
# <a name="troubleshooting-a-this-application-could-not-be-started-error-message"></a>Résolution des problèmes liés à un message d’erreur « cette application n’a pas pu être démarrée »

Les applications développées pour le .NET Framework requièrent généralement qu’une version spécifique du .NET Framework soit installée sur votre système. Dans certains cas, vous pouvez essayer d’exécuter une application sans version installée ou avec la version attendue du .NET Framework présent. Cela génère souvent une boîte de dialogue d’erreur semblable à la suivante :

![Impossible de démarrer cette application](media/application-not-started/app-could-not-be-started.png)

Cela indique généralement l’une des conditions suivantes :

- Une installation .NET Framework sur votre système a été endommagée.

- La version du .NET Framework nécessaire à votre application ne peut pas être détectée.

Pour résoudre ce problème afin de pouvoir exécuter votre application, procédez comme suit :

1. Téléchargez l' [outil de réparation .NET Framework (NetFxRepairTool. exe)](https://www.microsoft.com/download/details.aspx?id=30135). L’outil s’exécute automatiquement une fois le téléchargement terminé.

1. Si l’outil de réparation .NET Framework recommande des actions supplémentaires, comme celles figurant dans l’illustration suivante, sélectionnez **suivant**.

   ![Changements recommandés](media/application-not-started/repair-tool-recommended-changes.png)

1. Le .NET Framework outils de réparation affiche une boîte de dialogue illustrée dans la figure suivante pour indiquer que les modifications sont terminées. Laissez la boîte de dialogue ouverte pendant que vous essayez de réexécuter votre application. Cette opération doit être effectuée si l’outil de réparation .NET Framework a identifié et corrigé une installation endommagée de .NET Framework.

   ![Changements recommandés](media/application-not-started/repair-tool-changes-complete.png)

1. Si votre application s’exécute correctement, sélectionnez le bouton **Terminer** . Dans le cas contraire, sélectionnez le bouton **suivant** .

1. Si vous avez sélectionné le bouton **suivant** , l’outil de réparation .NET Framework affiche une boîte de dialogue semblable à la suivante. Sélectionnez le bouton **Terminer** pour envoyer des informations de diagnostic à Microsoft.

   ![Impossible de résoudre le problème](media/application-not-started/repair-tool-no-resolution.png)

1. Si vous ne pouvez toujours pas exécuter l’application, installez la version la plus récente du .NET Framework pris en charge par votre version de Windows, comme indiqué dans le tableau suivant.

   |Version Windows|Installation de .NET Framework|
   |---|---|
   |Mise à jour anniversaire Windows 10 et versions ultérieures|[.NET Framework 4,8 Runtime](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 10, mise à jour de novembre de Windows 10|[.NET Framework 4.6.2](https://dotnet.microsoft.com/download/dotnet-framework/net462)|
   |Windows 8.1|[.NET Framework 4,8 Runtime](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows 8|[.NET Framework 4.6.1](https://dotnet.microsoft.com/download/dotnet-framework/net461)|
   |Windows 7 SP1|[.NET Framework 4,8 Runtime](https://dotnet.microsoft.com/download/dotnet-framework/net48)|
   |Windows Vista SP2|[.NET Framework 4,6](https://dotnet.microsoft.com/download/dotnet-framework/net46)|

   > [!NOTE]
   > .NET Framework 4,8 est préinstallé sur la mise à jour de Windows 10 mai 2019.

1. Essayez de lancer l’application.

1. Dans certains cas, une boîte de dialogue semblable à la suivante s’affiche, vous demandant d’installer le .NET Framework 3,5. Sélectionnez **Télécharger et installer cette fonctionnalité** pour installer le .NET Framework 3,5, puis relancez l’application.

   ![Impossible de résoudre le problème](media/application-not-started/install-3-5.png)

## <a name="see-also"></a>Voir aussi

- [Configuration système requise pour .NET Framework](../get-started/system-requirements.md)
- [Guide d’installation de .NET Framework](index.md)
- [Résolution des problèmes liés aux installations et désinstallations bloquées du .NET Framework](troubleshoot-blocked-installations-and-uninstallations.md)
