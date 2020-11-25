---
title: Réduction des redémarrages système lors des installations de .NET Framework 4.5
description: Découvrez comment réduire les redémarrages du système pendant les installations .NET Framework 4,5. Un redémarrage peut être nécessaire si une application .NET 4 est en cours d’utilisation pendant l’installation de .NET Framework 4,5.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, reducing system restarts
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: 7aa8cb72-dee9-4716-ac54-b17b9ae8218f
ms.openlocfilehash: bdbf856bd4e431e389109524b70fce0674f552b8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726975"
---
# <a name="reducing-system-restarts-during-net-framework-45-installations"></a>Réduction des redémarrages système lors des installations de .NET Framework 4.5
Le programme d’installation de .NET Framework 4.5 utilise le [Gestionnaire de redémarrage](/windows/win32/rstmgr/about-restart-manager) pour empêcher le redémarrage du système autant que possible pendant l’installation. Si votre programme d’installation de l’application installe .NET Framework, il peut interagir avec le Gestionnaire de redémarrage pour tirer parti de cette fonctionnalité. Pour plus d’informations, consultez [Guide pratique pour obtenir la progression à partir du programme d’installation du .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md).

## <a name="reasons-for-a-restart"></a>Raisons pour un redémarrage
 Lors de l’installation de .NET Framework 4.5, vous devez redémarrer le système si une application .NET Framework 4 est en cours d’utilisation. En effet, .NET Framework 4.5 remplace les fichiers .NET Framework 4 et nécessite que ces fichiers soient disponibles pendant l’installation. Dans de nombreux cas, le redémarrage peut être évité par la détection préemptive et la fermeture des applications .NET Framework 4 en cours d'utilisation. Toutefois, certaines applications de système ne doivent pas être fermées. Dans ces cas là, un redémarrage ne peut pas être évité.

## <a name="end-user-experience"></a>Expérience de l’utilisateur final
 Un utilisateur final qui effectue une installation complète de .NET Framework 4.5 a la possibilité d’éviter un redémarrage du système si le programme d’installation détecte des applications .NET Framework 4 en cours d’utilisation. Un message répertorie toutes les applications utilisant .NET Framework 4 et fournit la possibilité de fermer les applications avant l'installation. Si l'utilisateur confirme, ces applications sont fermées par le programme d'installation, et un redémarrage du système est évité. Si l'utilisateur ne répond pas au message après un certain temps, l'installation reprend sans fermer aucune application.

 Si le Gestionnaire de redémarrage détecte une situation qui requiert un redémarrage du système même si les applications sont fermées, le message n'est pas affiché.

 ![La boîte de dialogue Fermer l’application listant les programmes en cours d’exécution.](./media/reducing-system-restarts/close-application-dialog.png)

## <a name="using-a-chained-installer"></a>Utilisation d'un programme d'installation chaîné
 Si vous voulez redistribuer .NET Framework avec votre application, mais si vous souhaitez utiliser votre propre programme d'installation et votre propre interface utilisateur, vous pouvez inclure (chaîner) le processus d'installation .NET Framework dans votre processus d'installation. Pour plus d’informations sur les installations chaînées, consultez [Guide de déploiement pour les développeurs](deployment-guide-for-developers.md). Pour réduire le nombre de redémarrages du système dans les installations chaînées, le programme d'installation .NET Framework fournit à votre programme d'installation la liste des applications à fermer. Votre programme d'installation doit fournir ces informations à l'utilisateur via une interface utilisateur telle qu'une boîte de message, obtenir la réponse de l'utilisateur, puis transmettre la réponse au programme d'installation .NET Framework. Pour obtenir un exemple d’un programme d’installation chaîné, consultez l’article [Guide pratique pour obtenir la progression à partir du programme d’installation du .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md).

 Si vous utilisez un programme d'installation chaîné, mais que vous ne souhaitez pas fournir votre propre boîte de message pour la fermeture des applications, vous pouvez utiliser les options `/showrmui` et `/passive` sur la ligne de commande lorsque vous chaînez le processus d'installation .NET Framework. Lorsque vous utilisez ces options ensemble, le programme d'installation affiche la boîte de message pour fermer les applications qui peuvent l'être pour éviter le redémarrage du système. Cette boîte de message se comporte de la même manière en mode passif que dans l'interface utilisateur. Consultez [Guide de déploiement pour les développeurs](deployment-guide-for-developers.md) pour les options complètes de la ligne de commande du package redistribuable du .NET Framework.

## <a name="see-also"></a>Voir aussi

- [Déploiement](index.md)
- [Guide de déploiement pour les développeurs](deployment-guide-for-developers.md)
- [Procédure : suivre la progression du programme d’installation de .NET Framework 4.5](how-to-get-progress-from-the-dotnet-installer.md)
