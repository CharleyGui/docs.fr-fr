---
title: Création d'un service de workflow de longue durée
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 4ae01201230bf848c045158424db60097d8dd767
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599345"
---
# <a name="create-a-long-running-workflow-service"></a>Créer un service de workflow de longue durée

Cette rubrique décrit comment créer un service de workflow de longue durée. Les services de workflow de longue durée peuvent s'exécuter sur de longues périodes. À un certain stade, le workflow peut devenir inactif en attendant des informations supplémentaires. Lorsque cela se produit, le workflow est rendu persistant dans une base de données SQL et supprimé de la mémoire. Une fois que les informations supplémentaires sont disponibles, l'instance de workflow est à nouveau chargée dans la mémoire et continue de s'exécuter.  Dans ce scénario, vous implémentez un système de commande très simplifié.  Le client envoie un message initial au service de workflow pour commencer la commande. Un ID de commande est retourné au client. À ce stade, le service de workflow attend un autre message du client, passe à l'état inactif et est rendu persistant dans une base de données SQL Server.  Lorsque le client envoie le message suivant pour commander un article, le service de workflow est à nouveau chargé dans la mémoire et termine le traitement de la commande. Dans l'exemple de code, il retourne une chaîne indiquant que l'article a été ajouté à la commande. L'exemple de code n'est pas censé refléter une application réelle de la technologie mais plutôt un exemple simple illustrant des services de workflow de longue durée. Cette rubrique suppose que vous savez comment créer des projets et des solutions Visual Studio 2012.

## <a name="prerequisites"></a>Prérequis

Les logiciels suivants doivent être installés pour suivre cette procédure pas à pas :

1. Microsoft SQL Server 2008

2. Visual Studio 2012

3. Microsoft [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4. Vous êtes familiarisé avec WCF et Visual Studio 2012 et vous savez comment créer des projets/solutions.

## <a name="set-up-the-sql-database"></a>Configurer le SQL Database

1. Pour que les instances du service de workflow soient persistantes, Microsoft SQL Server doit être installé et vous devez configurer une base de données pour stocker les instances de workflow persistantes. Exécutez Microsoft SQL Management Studio en cliquant sur le bouton **Démarrer** , en sélectionnant **tous les programmes**, **Microsoft SQL Server 2008**et **Microsoft SQL Management Studio**.

2. Cliquez sur le bouton **se connecter** pour vous connecter à l’instance SQL Server

3. Cliquez avec le bouton droit sur **bases de données** dans l’arborescence et sélectionnez **nouvelle base de données.** pour créer une nouvelle base de données appelée `SQLPersistenceStore` .

4. Exécutez le fichier de script SqlWorkflowInstanceStoreSchema.sql situé dans le répertoire C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dans la base de données SQLPersistenceStore pour configurer les schémas de base de données requis.

5. Exécutez le fichier de script SqlWorkflowInstanceStoreLogic.sql situé dans le répertoire C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en dans la base de données SQLPersistenceStore pour configurer la logique de base de données requise.

## <a name="create-the-web-hosted-workflow-service"></a>Créer le service de flux de travail hébergé sur le Web

1. Créez une solution Visual Studio 2012 vide, nommez-la `OrderProcessing` .

2. Ajoutez à la solution un nouveau projet d'application de service de workflow WCF appelée `OrderService`.

3. Dans la boîte de dialogue Propriétés du projet, sélectionnez l’onglet **Web** .

    1. Sous **action de démarrage** , sélectionnez une **page spécifique** et spécifiez `Service1.xamlx` .

        ![Propriétés Web de projet de service de workflow](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Créer l’option de page spécifique au service de flux de travail hébergé sur le Web")

    2. Sous **serveurs** , sélectionnez **utiliser le serveur Web IIS local**.

        ![Paramètres de serveur Web local](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Créer le service de flux de travail hébergé sur le Web-utiliser l’option de serveur Web IIS local")

        > [!WARNING]
        > Vous devez exécuter Visual Studio 2012 en mode administrateur pour définir ce paramètre.

        Ces deux étapes configurent le projet du service de workflow pour qu'il soit hébergé par IIS.

4. Ouvrez `Service1.xamlx` s’il n’est pas déjà ouvert et supprimez les activités **ReceiveRequest** et **SendResponse** existantes.

5. Sélectionnez l’activité de **service séquentielle** , puis cliquez sur le lien **variables** et ajoutez les variables affichées dans l’illustration suivante. Cette action permet d'ajouter des variables qui seront utilisées ultérieurement dans le service de workflow.

    > [!NOTE]
    > Si CorrelationHandle n’est pas dans la liste déroulante type de variable, sélectionnez **Parcourir les types** dans la liste déroulante. Tapez CorrelationHandle dans la zone **nom de type** , sélectionnez CorrelationHandle dans la zone de liste, puis cliquez sur **OK**.

    ![Ajouter des variables](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Ajoutez des variables à l’activité de service séquentielle.")

6. Faites glisser et déposez un modèle d’activité **ReceiveAndSendReply** dans l’activité de **service séquentielle** . Cet ensemble d'activités recevra un message d'un client et enverra une réponse en retour.

    1. Sélectionnez l’activité **Receive** et définissez les propriétés mises en surbrillance dans l’illustration suivante.

        ![Définir les propriétés de l'activité Receive](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Définissez les propriétés de l’activité Receive.")

        La propriété DisplayName définit le nom affiché pour l'activité Receive dans le concepteur. Les propriétés ServiceContractName et OperationName spécifient le nom du contrat de service et de l'opération implémentés par l'activité Receive. Pour plus d’informations sur l’utilisation des contrats dans les services de workflow, consultez [utilisation de contrats dans le workflow](using-contracts-in-workflow.md).

    2. Cliquez sur le lien **définir...** dans l’activité **ReceiveStartOrder** et définissez les propriétés affichées dans l’illustration suivante.  Notez que la case d’option **paramètres** est sélectionnée. un paramètre nommé `p_customerName` est lié à la `customerName` variable. Cela configure l’activité **Receive** pour recevoir des données et les lier à des variables locales.

        ![Définition des données reçues par l'activité Receive](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Définissez les propriétés des données reçues par l’activité Receive.")

    3. Sélectionnez l’activité **SendReplyToReceive** et définissez la propriété mise en surbrillance indiquée dans l’illustration suivante.

        ![Définition des propriétés de l'activité SendReply](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")

    4. Cliquez sur le lien **définir...** dans l’activité **SendReplyToStartOrder** et définissez les propriétés affichées dans l’illustration suivante. Notez que la case d’option **paramètres** est sélectionnée. un paramètre nommé `p_orderId` est lié à la `orderId` variable. Ce paramètre spécifie que l'activité SendReplyToStartOrder retournera une valeur de type String à l'appelant.

        ![Configuration des données de contenu de l'activité SendReply](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Configurez le paramètre de l’activité SetReplyToStartOrder.")

    5. Faites glisser et déposez une activité Assign entre les activités **Receive** et **SendReply** et définissez les propriétés comme indiqué dans l’illustration suivante :

        ![Ajout d'une activité assign](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Ajoutez une activité Assign.")

        Cette action permet de créer un nouvel ID de commande et de placer la valeur dans la variable orderId.

    6. Sélectionnez l’activité **ReplyToStartOrder** . Dans la fenêtre Propriétés, cliquez sur le bouton de sélection pour **CorrelationInitializers**. Sélectionnez le lien **Ajouter un initialiseur** , entrez `orderIdHandle` dans la zone de texte initialiseur, sélectionnez l’initialiseur de corrélation de requête pour le type de corrélation, puis sélectionnez p_orderId sous la zone de liste déroulante requêtes XPath. Ces paramètres sont affichés dans l’illustration suivante. Cliquez sur **OK**.  Cette action permet d'initialiser une corrélation entre le client et cette instance du service de workflow. Lorsqu'un message contenant cet ID de commande est reçu, il est routé vers cette instance du service de workflow.

        ![Ajout d'un initialiseur de corrélation](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Ajoutez un initialiseur de corrélation.")

7. Faites glisser et déposez une autre activité **ReceiveAndSendReply** à la fin du workflow (en dehors de la **séquence** contenant les premières activités **Receive** et **SendReply** ). Le second message envoyé par le client sera alors reçu et une réponse sera renvoyée.

    1. Sélectionnez la **séquence** qui contient les activités **Receive** et **SendReply** nouvellement ajoutées, puis cliquez sur le bouton **variables** . Ajoutez la variable mise en surbrillance dans l'illustration suivante :

        ![Ajout de nouvelles variables](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Ajoutez la variable ItemId.")

        Ajoutez également `orderResult` As **String** dans l' `Sequence` étendue.

    2. Sélectionnez l’activité **Receive** et définissez les propriétés affichées dans l’illustration suivante :

        ![Définir les propriétés de l’activité Receive](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Définissez les propriétés de l’activité Receive.")

        > [!NOTE]
        > N’oubliez pas de modifier le champ **ServiceContractName** avec `../IAddItem` .

    3. Cliquez sur le lien **définir...** dans l’activité **ReceiveAddItem** et ajoutez les paramètres indiqués dans l’illustration suivante : Cela configure l’activité Receive pour accepter deux paramètres, l’ID de commande et l’ID de l’élément en cours de tri.

        ![Spécification de paramètres pour la seconde réception](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Configurez l’activité Receive pour recevoir deux paramètres.")

    4. Cliquez sur le bouton de sélection **CorrelateOn** et entrez `orderIdHandle` . Sous **requêtes XPath**, cliquez sur la flèche déroulante et sélectionnez `p_orderId` . Cela permet de configurer la corrélation sur la deuxième activité Receive. Pour plus d’informations sur la corrélation, consultez [corrélation](correlation.md).

        ![Définition de la propriété CorrelatesOn](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Définissez la propriété CorrelatesOn.")

    5. Faites glisser et déposez une activité **If** immédiatement après l’activité **ReceiveAddItem** . Cette activité agit de la même façon qu'une instruction if.

        1. Affectez à la propriété **condition** la valeur`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2. Faites glisser une activité **Assign** dans la section **Then** et une autre dans la section **else** , puis définissez les propriétés des activités **Assign** comme indiqué dans l’illustration suivante.

            ![Assignation du résultat de l'appel de service](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Assignez le résultat de l’appel de service.")

            Si la condition est `true` , la section **Then** est exécutée. Si la condition est `false` , la section **else** est exécutée.

        3. Sélectionnez l’activité **SendReplyToReceive** et définissez la propriété **DisplayName** indiquée dans l’illustration suivante.

            ![Définition des propriétés de l'activité SendReply](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Définissez la propriété de l’activité SendReply.")

        4. Cliquez sur le lien **définir...** dans l’activité **SetReplyToAddItem** et configurez-le comme indiqué dans l’illustration suivante. Cela configure l’activité **SendReplyToAddItem** pour retourner la valeur dans la `orderResult` variable.

            ![Définition de la liaison de données pour l’activité SendReply](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Définissez la propriété pour l’activité SendReplyToAddItem.")

8. Ouvrez le fichier Web. config et ajoutez les éléments suivants dans la \<behavior> section pour activer la persistance du flux de travail.

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    > Assurez-vous de remplacer le nom de l'hôte et de l'instance SQL Server dans l'extrait de code précédent.

9. Générez la solution.

## <a name="create-a-client-application-to-call-the-workflow-service"></a>Créer une application cliente pour appeler le service de workflow

1. Ajoutez à la solution un nouveau projet d'application console nommé `OrderClient`.

2. Ajoutez les références aux assemblys suivantes au projet `OrderClient` :

    1. System.ServiceModel.dll

    2. System.ServiceModel.Activities.dll

3. Ajoutez une référence de service au service de workflow et spécifiez `OrderService` comme espace de noms.

4. Dans la méthode `Main()` du projet client, ajoutez le code suivant :

    ```csharp
    static void Main(string[] args)
    {
       // Send initial message to start the workflow service
       Console.WriteLine("Sending start message");
       StartOrderClient startProxy = new StartOrderClient();
       string orderId = startProxy.StartOrder("Kim Abercrombie");

       // The workflow service is now waiting for the second message to be sent
       Console.WriteLine("Workflow service is idle...");
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");
       Console.ReadLine();

       // Send the second message
       Console.WriteLine("Sending add item message");
       AddItemClient addProxy = new AddItemClient();
       AddItem item = new AddItem();
       item.p_itemId = "Zune HD";
       item.p_orderId = orderId;

       string orderResult = addProxy.AddItem(item);
       Console.WriteLine("Service returned: " + orderResult);
    }
    ```

5. Générez la solution et exécutez l'application `OrderClient`. Le client affiche le texte suivant :

    ```output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. Pour vérifier que le service de workflow a été conservé, démarrez le SQL Server Management Studio en accédant au menu **Démarrer** , en sélectionnant **tous les programmes**, **Microsoft SQL Server 2008** **SQL Server Management Studio**.

    1. Dans le volet gauche, développez **bases de données**, **SQLPersistenceStore**, **vues** , puis cliquez avec le bouton droit sur **System. Activities. DurableInstancing. instances** et sélectionnez **Sélectionner les 1000 premières lignes**. Dans le volet de **résultats** , vérifiez qu’au moins une instance est indiquée. D'autres instances d'exécutions précédentes peuvent également être présentes si une exception s'est produite pendant l'exécution. Vous pouvez supprimer des lignes existantes en cliquant avec le bouton droit sur **System. Activities. DurableInstancing. instances** et en sélectionnant **modifier les 200 lignes du haut**, en appuyant sur le bouton **exécuter** , en sélectionnant toutes les lignes dans le volet des résultats et en sélectionnant **supprimer**.  Pour vous assurer que l'instance affichée dans la base de données est bien l'instance créée par votre application, vérifiez que la vue Instances est vide avant d'exécuter le client. Une fois que le client est en cours d'exécution, réexécutez la requête (Sélectionner les 1000 lignes du haut) et assurez-vous qu'une nouvelle instance a été ajoutée.

7. Appuyez sur Entrée pour envoyer le message d'ajout d'élément au service de workflow. Le client affiche le texte suivant :

    ```output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>Voir aussi

- [Services de workflow](workflow-services.md)
