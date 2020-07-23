---
title: 'Procédure : enregistrer des informations relatives aux services'
description: Savoir comment consigner des informations sur les services. Définissez la propriété AutoLog si vous souhaitez que votre projet de service Windows interagisse avec le journal des événements de l’application.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutoLog property
- services, logging information
- Windows Service applications, logging information about
- event logs, service applications
- application event logs, service applications
- logs, service applications
ms.assetid: c0d8140f-c055-4d8e-a2e0-37358a550116
author: ghogen
ms.openlocfilehash: 6ebce5464dc25ba4101b3898ee791714f8efc5d6
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925746"
---
# <a name="how-to-log-information-about-services"></a>Procédure : enregistrer des informations relatives aux services
Par défaut, tous les projets de service Windows ont la possibilité d’interagir avec le journal d’événements des applications et d’y écrire des informations et des exceptions. Vous utilisez la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> pour indiquer si vous souhaitez cette fonctionnalité dans votre application. Par défaut, la journalisation est activée pour tout service que vous créez avec le modèle de projet de service Windows. Vous pouvez utiliser un formulaire statique de la classe <xref:System.Diagnostics.EventLog> pour écrire des informations de service dans un journal sans avoir à créer une instance d’un composant <xref:System.Diagnostics.EventLog> ou inscrire manuellement une source.  
  
 Le programme d’installation de votre service inscrit automatiquement chaque service de votre projet comme source valide d’événements dans le journal des applications sur l’ordinateur où le service est installé, quand la journalisation est activée. Le service enregistre des informations chaque fois que le service est démarré, arrêté, suspendu, repris, installé ou désinstallé. Il enregistre également tous les échecs qui se produisent. Vous n’avez pas besoin d’écrire du code pour écrire des entrées dans le journal quand vous utilisez le comportement par défaut. Le service le gère pour vous automatiquement.  
  
 Si vous souhaitez écrire dans un journal d’événements autre que le journal des applications, vous devez définir la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> sur `false`, créer votre propre journal d’événements personnalisé dans le code de vos services et inscrire votre service en tant que source valide d’entrées de ce journal. Vous devez ensuite écrire le code nécessaire pour enregistrer des entrées dans le journal chaque fois qu’une action qui vous intéresse se produit.  
  
> [!NOTE]
> Si vous utilisez un journal d’événements personnalisé et configurez votre application de service pour qu’elle écrive dans ce journal, vous ne devez pas tenter d’accéder au journal d’événements avant de définir la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> du service dans votre code. Le journal des événements a besoin de la valeur de cette propriété pour inscrire votre service en tant que source d’événements valide.  
  
### <a name="to-enable-default-event-logging-for-your-service"></a>Pour activer la journalisation des événements par défaut pour votre service  
  
- Définissez la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> pour votre composant sur `true`.  
  
    > [!NOTE]
    > Par défaut, cette propriété est définie sur `true`. Vous n’avez pas besoin de la définir explicitement, sauf si vous générez un traitement plus complexe, comme l’évaluation d’une condition, puis que vous définissez la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> en fonction du résultat de cette condition.  
  
### <a name="to-disable-event-logging-for-your-service"></a>Pour désactiver la journalisation des événements pour votre service  
  
- Définissez la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> pour votre composant sur `false`.  
  
     [!code-csharp[VbRadconService#17](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#17)]
     [!code-vb[VbRadconService#17](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#17)]  
  
### <a name="to-set-up-logging-to-a-custom-log"></a>Pour configurer l’enregistrement dans un journal personnalisé  
  
1. Affectez à la propriété <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> la valeur `false`.  
  
    > [!NOTE]
    > Vous devez définir <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> sur false pour utiliser un journal personnalisé.  
  
2. Configurez une instance d’un composant <xref:System.Diagnostics.EventLog> dans votre application de service Windows.  
  
3. Créez un journal personnalisé en appelant la méthode <xref:System.Diagnostics.EventLog.CreateEventSource%2A> et en spécifiant la chaîne source et le nom du fichier journal que vous souhaitez créer.  
  
4. Définissez la propriété <xref:System.Diagnostics.EventLog.Source%2A> dans l’instance du composant <xref:System.Diagnostics.EventLog> sur la chaîne source que vous avez créée à l’étape 3.  
  
5. Écrivez vos entrées en accédant à la méthode <xref:System.Diagnostics.EventLog.WriteEntry%2A> dans l’instance du composant <xref:System.Diagnostics.EventLog> .  
  
     Le code suivant montre comment configurer l’enregistrement dans un journal personnalisé.  
  
    > [!NOTE]
    > Dans cet exemple de code, une instance d’un composant <xref:System.Diagnostics.EventLog> est appelée `eventLog1` (`EventLog1` en Visual Basic). Si vous avez créé une instance avec un autre nom à l’étape 2, modifiez le code en conséquence.  
  
     [!code-csharp[VbRadconService#14](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#14)]
     [!code-vb[VbRadconService#14](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#14)]  
    [!code-csharp[VbRadconService#15](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#15)]
    [!code-vb[VbRadconService#15](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#15)]  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux applications de service Windows](introduction-to-windows-service-applications.md)
