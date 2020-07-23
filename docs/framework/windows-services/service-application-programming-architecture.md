---
title: Architecture de programmation d'une application de service
description: Comprendre l’architecture de programmation des applications de service. Les applications de service Windows sont basées sur une classe qui hérite de System. ServiceProcess. ServiceBase.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceController components, programming architecture
- ServiceBase class, service states
- Windows Service applications, code model
- services, programming architecture
- ServiceController class
- services, states
- ServiceProcessInstaller class, service application code model
- Windows Service applications, states
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
author: ghogen
ms.openlocfilehash: c59ccc5a8b2f11fda9c4734487092c1aabb74908
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925577"
---
# <a name="service-application-programming-architecture"></a>Architecture de programmation d'une application de service
Les applications de service Windows sont basées sur une classe qui hérite de la classe <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType>. Substituez les méthodes de cette classe et définissez des fonctionnalités pour qu’elles déterminent le comportement de votre service.  
  
 Les principales classes impliquées dans la création du service sont les suivantes :  
  
- <xref:System.ServiceProcess.ServiceBase?displayProperty=nameWithType> : substituez les méthodes de la classe <xref:System.ServiceProcess.ServiceBase> au moment de la création d’un service et définissez le code pour déterminer le fonctionnement de votre service dans cette classe héritée.  
  
- <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=nameWithType> et <xref:System.ServiceProcess.ServiceInstaller?displayProperty=nameWithType> : utilisez ces classes pour installer et désinstaller votre service.  
  
 Par ailleurs, vous pouvez utiliser une classe nommée <xref:System.ServiceProcess.ServiceController> pour manipuler le service. Cette classe n’est pas impliquée dans la création d’un service, mais vous pouvez vous en servir pour démarrer et arrêter le service, lui passer des commandes et retourner une série d’énumérations.  
  
## <a name="defining-your-services-behavior"></a>Définition du comportement de votre service  
 Dans votre classe de service, substituez les fonctions de classe de base qui déterminent ce qui se passe en cas de changement de l’état de votre service dans le Gestionnaire de contrôle des services. La classe <xref:System.ServiceProcess.ServiceBase> expose les méthodes suivantes, que vous pouvez substituer pour ajouter un comportement personnalisé.  
  
|Méthode|Substituer pour|  
|------------|-----------------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|Indiquer les actions à effectuer quand votre service commence à s’exécuter. Vous devez écrire du code dans cette procédure pour que votre service effectue des tâches utiles.|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|Indiquer ce qui doit se passer quand votre service est suspendu.|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|Indiquer ce qui doit se passer quand votre service arrête de s’exécuter.|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|Indiquer ce qui doit se passer quand votre service revient à son fonctionnement normal après avoir été suspendu.|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|Indiquer ce qui doit se passer juste avant l’arrêt de votre système si votre service est en cours d’exécution à ce moment-là.|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|Indiquer ce qui doit se passer quand votre service reçoit une commande personnalisée. Pour plus d’informations sur les commandes personnalisées, consultez MSDN Online.|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|Indiquer comment le service doit répondre à la suite d’un événement de gestion de l’alimentation (batterie faible, opération suspendue, etc.).|  
  
> [!NOTE]
> Ces méthodes représentent les états par lesquels passe le service au cours de sa vie (le service passe d’un état à l’autre). Par exemple, le service ne répond jamais à une commande <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> avant un appel à <xref:System.ServiceProcess.ServiceBase.OnStart%2A>.  
  
 D’autres propriétés et méthodes présentent un intérêt. notamment :  
  
- La méthode <xref:System.ServiceProcess.ServiceBase.Run%2A> sur la classe <xref:System.ServiceProcess.ServiceBase>. Il s’agit du point d’entrée principal du service. Quand vous créez un service à l’aide du modèle de service Windows, le code est inséré dans la méthode `Main` de votre application pour exécuter le service. Ce code ressemble à ceci :  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    > Ces exemples utilisent un tableau de type <xref:System.ServiceProcess.ServiceBase>, dans lequel chaque service contenu dans votre application peut être ajouté. Tous les services peuvent ensuite être exécutés ensemble. Toutefois, si vous ne créez qu’un seul service, vous pouvez choisir de ne pas utiliser le tableau. Dans ce cas, déclarez simplement un nouvel objet héritant de <xref:System.ServiceProcess.ServiceBase> et exécutez-le. Pour obtenir un exemple, consultez [Guide pratique pour écrire des services par programmation](how-to-write-services-programmatically.md).  
  
- Une série de propriétés sur la classe <xref:System.ServiceProcess.ServiceBase>. Celles-ci déterminent les méthodes qui peuvent être appelées sur votre service. Par exemple, quand la propriété <xref:System.ServiceProcess.ServiceBase.CanStop%2A> a la valeur `true`, la méthode <xref:System.ServiceProcess.ServiceBase.OnStop%2A> sur votre service peut être appelée. Quand la propriété <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> a la valeur `true`, les méthodes <xref:System.ServiceProcess.ServiceBase.OnPause%2A> et <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> peuvent être appelées. Si vous définissez l’une de ces propriétés avec la valeur `true`, vous devez ensuite remplacer et définir le traitement des méthodes associées.  
  
    > [!NOTE]
    > Pour être utile, votre service doit substituer au moins <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.  
  
 Vous pouvez également utiliser un composant appelé <xref:System.ServiceProcess.ServiceController> pour communiquer avec un service existant et contrôler son comportement.  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux applications de service Windows](introduction-to-windows-service-applications.md)
- [Procédure : créer des services Windows](how-to-create-windows-services.md)
