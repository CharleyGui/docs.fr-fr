---
title: 'Procédure : créer un service de workflow avec les activités de messagerie'
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: b4991fc9f8a6c45cae3943f1506247c42ed2b30b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597122"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>Procédure : créer un service de workflow avec les activités de messagerie
Cette rubrique décrit comment créer un service de workflow simple, à l'aide d'activités de messagerie. Elle est consacrée à la mécanique de création d'un service de workflow, simplement constitué d'activités de messagerie. Dans un service réel, le workflow contient de nombreuses autres activités. Le service implémente une opération nommée Echo, qui prend une chaîne et la retourne à l'appelant. Cette rubrique est la première d'une série de deux. La rubrique suivante [Comment : accéder à un service à partir d’une application de workflow](how-to-access-a-service-from-a-workflow-application.md) explique comment créer une application de workflow capable d’appeler le service créé dans cette rubrique.  
  
### <a name="to-create-a-workflow-service-project"></a>Pour créer un projet de service de workflow  
  
1. Démarrez Visual Studio 2012.  
  
2. Cliquez sur le menu **fichier** , sélectionnez **nouveau**, puis **projet** pour afficher la **boîte de dialogue Nouveau projet**. Sélectionnez **Workflow** dans la liste des modèles installés et **application de service de flux de travail WCF** dans la liste des types de projets. Nommez le projet `MyWFService` et utilisez l’emplacement par défaut, comme indiqué dans l’illustration suivante.  
  
     Cliquez sur le bouton **OK** pour fermer la **boîte de dialogue Nouveau projet**.  
  
3. Lorsque le projet est créé, le fichier Service1.xamlx s'ouvre dans le concepteur, comme indiqué dans l'illustration suivante.  
  
     ![Capture d’écran affiche le fichier Open Service1. xamlx dans le concepteur.](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     Cliquez avec le bouton droit sur l’activité nommée **service séquentiel** , puis sélectionnez **supprimer**.  
  
### <a name="to-implement-the-workflow-service"></a>Pour implémenter le service de workflow  
  
1. Sélectionnez l’onglet **boîte à outils** sur le côté gauche de l’écran pour afficher la boîte à outils et cliquez sur la punaise pour garder la fenêtre ouverte. Développez la section **messagerie** de la boîte à outils pour afficher les activités de messagerie et les modèles d’activité de messagerie, comme indiqué dans l’illustration suivante.  
  
     ![Capture d’écran qui montre la section boîte à outils avec messagerie développée.](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. Glissez-déposez un modèle **ReceiveAndSendReply** dans le concepteur de Workflow. Cela crée une <xref:System.Activities.Statements.Sequence> activité avec une activité **Receive** suivie d’une <xref:System.ServiceModel.Activities.SendReply> activité, comme indiqué dans l’illustration suivante.  
  
     ![Capture d’écran qui montre le modèle ReceiveAndSendReply.](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     Remarque : l'activité <xref:System.ServiceModel.Activities.SendReply> possède une propriété <xref:System.ServiceModel.Activities.SendReply.Request%2A> qui est définie sur `Receive`, le nom de l'activité <xref:System.ServiceModel.Activities.Receive> à laquelle répond l'activité <xref:System.ServiceModel.Activities.SendReply>.  
  
3. Dans le <xref:System.ServiceModel.Activities.Receive> type d’activité, dans `Echo` la zone de texte intitulée **NomOpération**. Cela définit le nom de l'opération que le service implémente.  
  
     ![Capture d’écran montrant où spécifier le nom de l’opération.](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. Une fois l' <xref:System.ServiceModel.Activities.Receive> activité sélectionnée, ouvrez la fenêtre Propriétés si elle n’est pas déjà ouverte en cliquant sur le menu **affichage** et en sélectionnant **fenêtre Propriétés**. Dans la **fenêtre Propriétés** , faites défiler l’affichage jusqu’à **CanCreateInstance** et cliquez sur la case à cocher comme indiqué dans l’illustration suivante. Ce paramètre active l'hôte de service de workflow pour créer une nouvelle instance du service (si requis) lorsqu'un message est reçu.  
  
     ![Capture d’écran qui montre la propriété CanCreateInstance.](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. Sélectionnez l' <xref:System.Activities.Statements.Sequence> activité et cliquez sur le bouton **variables** dans le coin inférieur gauche du concepteur. Cela affiche l'éditeur de variables. Cliquez sur le lien **créer une variable** pour ajouter une variable afin de stocker la chaîne envoyée à l’opération. Nommez la variable `msg` et définissez son type de **variable** sur String, comme indiqué dans l’illustration suivante.  
  
     ![Capture d’écran montrant comment ajouter une variable.](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     Cliquez à nouveau sur le bouton **variables** pour fermer l’éditeur de variables.  
  
6. Cliquez sur **définir.** dans la zone de texte **contenu** de l' <xref:System.ServiceModel.Activities.Receive> activité pour afficher la boîte de dialogue **définition du contenu** . Sélectionnez la case d’option **paramètres** , cliquez sur le lien **Ajouter un nouveau paramètre** , tapez `inMsg` dans la zone de texte **nom** , sélectionnez **chaîne** dans la zone de liste déroulante **type** , puis tapez `msg` dans la zone de texte **affecter à** , comme indiqué dans l’illustration suivante.  
  
     ![Capture d’écran qui montre comment ajouter du contenu de paramètres.](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     Cela spécifie que l'activité Receive reçoit le paramètre de chaîne et que les données sont liées à la variable `msg`. Cliquez sur **OK** pour fermer la boîte de dialogue **définition du contenu** .  
  
7. Cliquez sur le lien **définir...** dans la zone **contenu** de l' <xref:System.ServiceModel.Activities.SendReply> activité pour afficher la boîte de dialogue **définition du contenu** . Sélectionnez la case d’option **paramètres** , cliquez sur le lien **Ajouter un nouveau paramètre** , tapez `outMsg` dans la zone de texte **nom** , sélectionnez **chaîne** dans la zone de liste déroulante **type** et, `msg` dans la zone de texte **valeur** , comme indiqué dans l’illustration suivante.  
  
     ![Capture d’écran montrant comment ajouter le paramètre outMsg.](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     Cela spécifie que l'activité <xref:System.ServiceModel.Activities.SendReply> envoie un message ou un type de contrat de message et que les données sont liées à la variable `msg`. Comme il s'agit d'une activité <xref:System.ServiceModel.Activities.SendReply>, cela signifie que les données dans `msg` sont utilisées pour remplir le message que l'activité renvoie au client. Cliquez sur **OK** pour fermer la boîte de dialogue **définition du contenu** .  
  
8. Enregistrez et générez la solution en cliquant sur le menu **générer** et en sélectionnant **générer la solution**.  
  
## <a name="configure-the-workflow-service-project"></a>Configurer le projet du service de workflow  
 Le service de workflow est terminé. Cette section explique comment configurer la solution de service de workflow pour en faciliter l'hébergement et l'exécution. Cette solution utilise le serveur de développement ASP.NET pour héberger le service.  
  
#### <a name="to-set-project-start-up-options"></a>Pour définir les options de démarrage du projet  
  
1. Dans la **Explorateur de solutions**, cliquez avec le bouton droit sur **MyWFService** et sélectionnez **Propriétés** pour afficher la boîte de dialogue **Propriétés du projet** .  
  
2. Sélectionnez l’onglet **Web** et sélectionnez une **page spécifique** sous **action de démarrage** , puis tapez `Service1.xamlx` dans la zone de texte, comme indiqué dans l’illustration suivante.  
  
     ![Capture d’écran qui affiche la boîte de dialogue Propriétés du projet.](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     Cela héberge le service défini dans Service1.xamlx dans le serveur de développement ASP.NET.  
  
3. Appuyez sur Ctrl + F5 pour lancer le service. L'icône du serveur de développement ASP.NET s'affiche dans la partie inférieure droite du Bureau, comme le montre l'image suivante.  
  
     ![Capture d’écran montrant l’icône du serveur de développement ASP.NET.](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     De plus, Internet Explorer affiche la page d'aide du service WCF pour le service.  
  
     ![Capture d’écran montrant la page d’aide du service WCF.](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. Passez à la rubrique [Comment : accéder à un service à partir d’une application de flux](how-to-access-a-service-from-a-workflow-application.md) de travail pour créer un client de workflow qui appelle ce service.  
  
## <a name="see-also"></a>Voir aussi

- [Services de workflow](workflow-services.md)
- [Vue d'ensemble de l'hébergement de services de workflow](hosting-workflow-services-overview.md)
- [Activités de messagerie](messaging-activities.md)
