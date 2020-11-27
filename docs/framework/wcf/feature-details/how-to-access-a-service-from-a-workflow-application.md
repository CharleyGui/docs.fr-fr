---
title: 'Procédure : accéder à un service à partir d’une application de workflow'
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: 13fae7dec3026e96e3c196467da29fe768a3655f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257930"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>Procédure : accéder à un service à partir d’une application de workflow

Cette rubrique décrit comment appeler un service de workflow à partir d'une application console de workflow. Cela dépend de l’achèvement de la rubrique [Comment : créer un service de flux de travail avec des activités de messagerie](how-to-create-a-workflow-service-with-messaging-activities.md) . Bien que cette rubrique explique comment appeler un service de workflow à partir d’une application de workflow, les mêmes méthodes peuvent être utilisées pour appeler n’importe quel service Windows Communication Foundation (WCF) à partir d’une application de Workflow.

### <a name="create-a-workflow-console-application-project"></a>Créer un projet d'application console de workflow.

1. Démarrez Visual Studio 2012.

2. Chargez le projet MyWFService que vous avez créé dans la rubrique [procédure : créer un service de flux de travail avec des activités de messagerie](how-to-create-a-workflow-service-with-messaging-activities.md) .

3. Cliquez avec le bouton droit sur la solution **MyWFService** dans le **Explorateur de solutions** , puis sélectionnez **Ajouter**, **nouveau projet**. Dans la liste des types de projets, sélectionnez **Workflow** dans les **modèles installés** et **application console de workflow** . Nommez le projet MyWFClient et utilisez l'emplacement par défaut, comme indiqué dans l'illustration suivante.

     ![Ajouter une nouvelle boîte de dialogue Nouveau projet](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     Cliquez sur le bouton **OK** pour fermer la **boîte de dialogue Ajouter un nouveau projet**.

4. Après avoir créé le projet, le fichier Workflow1.xaml s'ouvre dans le concepteur. Cliquez sur l’onglet **boîte à outils** pour ouvrir la boîte à outils si elle n’est pas déjà ouverte et cliquez sur la punaise pour maintenir la fenêtre boîte à outils ouverte.

5. Appuyez sur **CTRL** + **F5** pour générer et lancer le service. Comme auparavant, le Serveur de développement ASP.NET se lance et Internet Explorer affiche la page d'aide WCF. Notez l'URI de cette page, car vous devez l'utiliser dans l'étape suivante.

     ![IE affichant la page d’aide WCF et l’URI](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. Cliquez avec le bouton droit sur le projet **MyWFClient** dans le **Explorateur de solutions** , puis sélectionnez **Ajouter** une  >  **référence de service**. Cliquez sur le bouton **découvrir** pour rechercher des services dans la solution actuelle. Cliquez sur le triangle à côté de Service1.xamlx dans la liste des services. Cliquez sur le triangle à côté de Service1 pour répertorier les contrats implémentés par le service Service1. Développez le nœud **Service1** dans la liste des **services** . L’opération ECHO est affichée dans la liste des **opérations** , comme indiqué dans l’illustration suivante.

     ![Boîte de dialogue Ajouter une référence de service](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     Conservez l’espace de noms par défaut et cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter une référence de service** . La boîte de dialogue suivante s'affiche.

     ![Boîte de dialogue de notification de Ajouter une référence de service](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     Cliquez sur **OK** pour fermer la boîte de dialogue. Appuyez ensuite sur Ctrl+Maj+B pour générer la solution. Notez que dans la boîte à outils, une nouvelle section a été ajoutée appelée **MyWFClient. ServiceReference1. Activities**. Développez cette section ; l’activité Echo a été ajoutée comme indiqué dans l’illustration suivante.

     ![Activité ECHO dans la boîte à outils](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. Faites glisser une activité <xref:System.Activities.Statements.Sequence> sur l'aire du concepteur. Il se trouve sous la section **Flow Control** de la boîte à outils.

8. Une fois l' <xref:System.Activities.Statements.Sequence> activité activée, cliquez sur le lien **variables** et ajoutez une variable de chaîne nommée `inString` . Attribuez à la variable la valeur par défaut `"Hello, world"` , ainsi qu’une variable de chaîne nommée `outString` comme indiqué dans le diagramme suivant.

     ![Ajout d’une variable inString](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. Faites glisser et déposez une activité **echo** dans le <xref:System.Activities.Statements.Sequence> . Dans la fenêtre Propriétés, liez l' `inMsg` argument à la `inString` variable et l' `outMsg` argument à la `outString` variable, comme indiqué dans l’illustration suivante. Cela transmet la valeur de la variable `inString` à l'opération, puis prend la valeur de retour et la place dans la variable `outString`.

     ![Lier les arguments à des variables](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. Faites glisser et déposez une activité **WriteLine** sous l’activité **echo** pour afficher la chaîne retournée par l’appel de service. L’activité **WriteLine** se trouve dans le nœud **primitives** de la boîte à outils. Liez l’argument **Text** de l’activité **WriteLine** à la `outString` variable en tapant `outString` dans la zone de texte sur l’activité **WriteLine** . Le workflow doit maintenant ressembler à l'illustration suivante.

     ![Flux de travail client complet](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. Cliquez avec le bouton droit sur la solution MyWFService et sélectionnez **définir les projets de démarrage...**. Sélectionnez la case d’option **plusieurs projets de démarrage** et sélectionnez **Démarrer** pour chaque projet dans la colonne **action** comme indiqué dans l’illustration suivante.

     ![Options des projets de démarrage](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. Appuyez sur Ctrl + F5 pour lancer à la fois le service et le client. Le Serveur de développement ASP.NET héberge le service, Internet Explorer affiche la page d’aide WCF et l’application de workflow client est lancée dans une fenêtre de console et affiche la chaîne retournée par le service (« Hello, World »).

## <a name="see-also"></a>Voir aussi

- [Services de workflow](workflow-services.md)
- [Procédure : créer un service de workflow avec des activités de messagerie](how-to-create-a-workflow-service-with-messaging-activities.md)
- [Consommer un service WCF à partir d'un workflow dans un projet Web](/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
