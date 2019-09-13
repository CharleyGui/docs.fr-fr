---
title: Flux de transactions vers et depuis des services de workflow
ms.date: 03/30/2017
ms.assetid: 03ced70e-b540-4dd9-86c8-87f7bd61f609
ms.openlocfilehash: db1a1ef6bcf3f048584b39450c90fac3ff35646b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893374"
---
# <a name="flowing-transactions-into-and-out-of-workflow-services"></a>Flux de transactions vers et depuis des services de workflow
Les services et clients de workflow peuvent participer aux transactions.  Pour qu'une opération de service fasse partie d'une transaction ambiante, placez une activité <xref:System.ServiceModel.Activities.Receive> dans une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Tous les appels effectués par une activité <xref:System.ServiceModel.Activities.Send> ou <xref:System.ServiceModel.Activities.SendReply> au sein de l’activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> seront également effectués dans la transaction ambiante. Une application cliente de workflow peut créer une transaction ambiante en utilisant l’activité <xref:System.Activities.Statements.TransactionScope> et appeler des opérations de service à l’aide de la transaction ambiante. Cette rubrique vous guide dans la création d’un service de workflow et d’un client de workflow qui participent à des transactions.  
  
> [!WARNING]
> Si une instance de service de workflow est chargée dans une transaction et que le <xref:System.Activities.Statements.Persist> Workflow contient une activité, l’instance de workflow est bloquée jusqu’à ce que la transaction expire.  
  
> [!IMPORTANT]
> Lorsque vous utilisez une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope>, il est recommandé de placer toutes les réceptions dans le workflow dans les activités <xref:System.ServiceModel.Activities.TransactedReceiveScope>.  
  
> [!IMPORTANT]
> Lorsque vous utilisez <xref:System.ServiceModel.Activities.TransactedReceiveScope> et les messages arrivent dans le mauvais ordre incorrect, le workflow est abandonné lorsque vous tentez de livrer le premier message dans le désordre. Vous devez vous assurer que votre workflow est toujours à un point d'arrêt cohérent lorsqu'il est inactif. Cela vous permet de redémarrer le workflow à partir d'un point de persistance précédent s'il est abandonné.  
  
### <a name="create-a-shared-library"></a>Créer une bibliothèque partagée  
  
1. Créez une solution Visual Studio vide.  
  
2. Ajoutez un nouveau projet de bibliothèque de classes nommé `Common`. Ajoutez des références aux assemblys suivants :  
  
    - System.Activities.dll  
  
    - System.ServiceModel.dll  
  
    - System.ServiceModel.Activities.dll  
  
    - System.Transactions.dll  
  
3. Ajoutez une nouvelle classe nommée `PrintTransactionInfo` au projet `Common`. Cette classe est dérivée de <xref:System.Activities.NativeActivity> et surcharge la méthode <xref:System.Activities.NativeActivity.Execute%2A>.  
  
    ```csharp
    using System;  
    using System;  
    using System.Activities;  
    using System.Transactions;  
  
    namespace Common  
    {  
        public class PrintTransactionInfo : NativeActivity  
        {  
            protected override void Execute(NativeActivityContext context)  
            {  
                RuntimeTransactionHandle rth = context.Properties.Find(typeof(RuntimeTransactionHandle).FullName) as RuntimeTransactionHandle;  
  
                if (rth == null)  
                {  
                    Console.WriteLine("There is no ambient RuntimeTransactionHandle");  
                }  
  
                Transaction t = rth.GetCurrentTransaction(context);  
  
                if (t == null)  
                {  
                    Console.WriteLine("There is no ambient transaction");  
                }  
                else  
                {  
                    Console.WriteLine("Transaction: {0} is {1}", t.TransactionInformation.DistributedIdentifier, t.TransactionInformation.Status);  
                }  
            }  
        }  
  
    }  
    ```  
  
     Il s’agit d’une activité native qui affiche des informations sur la transaction ambiante et est utilisée dans les workflows du service et du client utilisés dans cette rubrique. Générez la solution pour rendre cette activité disponible dans la section **commune** de la **boîte à outils**.  
  
### <a name="implement-the-workflow-service"></a>Implémenter le service de workflow  
  
1. Ajoutez un nouveau service de flux de travail `WorkflowService` WCF, `Common` appelé au projet. Pour ce faire, cliquez avec `Common` le bouton droit sur le projet, sélectionnez **Ajouter**, **nouvel élément...** , sélectionnez **Workflow** sous **modèles installés** , puis sélectionnez **service de flux de travail WCF**.  
  
     ![Ajout d'un service de flux de travail](./media/flowing-transactions-into-and-out-of-workflow-services/add-workflow-service.jpg)  
  
2. Supprimez les activités par défaut `ReceiveRequest` et `SendResponse`.  
  
3. Faites glisser et déposez une activité <xref:System.Activities.Statements.WriteLine> dans l’activité `Sequential Service`. Affectez à la propriété Text la valeur `"Workflow Service starting ..."`, comme le montre l'exemple suivant.  
  
     ! [Ajout d’une activité WriteLine à l’activité de service séquentielle (./Media/Flowing-transactions-into-and-out-of-Workflow-Services/Add-WriteLine-Sequential-service.jpg)  
  
4. Faites glisser et déposez une activité <xref:System.ServiceModel.Activities.TransactedReceiveScope> après l’activité <xref:System.Activities.Statements.WriteLine>. L' <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité se trouve dans la section **messagerie** de la **boîte à outils**. L' <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité est composée de deux sections **Request** et **Body**. La section de la requête <xref:System.ServiceModel.Activities.Receive> contient l’activité. La section **Body** contient les activités à exécuter dans une transaction après réception d’un message.  
  
     ![Ajout d'une activité TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactedreceivescope-activity.jpg)  
  
5. Sélectionnez l' <xref:System.ServiceModel.Activities.TransactedReceiveScope> activité et cliquez sur le bouton **variables** . Ajoutez les variables suivantes.  
  
     ![Ajout de variables à TransactedReceiveScope](./media/flowing-transactions-into-and-out-of-workflow-services/add-transactedreceivescope-variables.jpg)  
  
    > [!NOTE]
    > Vous pouvez supprimer la variable de données proposée à cet endroit par défaut. Vous pouvez également utiliser la variable de handle existante.  
  
6. Faites glisser et déposez une <xref:System.ServiceModel.Activities.Receive> activité dans la section <xref:System.ServiceModel.Activities.TransactedReceiveScope> **requête** de l’activité. Définissez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |CanCreateInstance|True (activez la case à cocher)|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Le workflow doit ressembler à ceci :  
  
     ![Ajout d'une activité Receive](./media/flowing-transactions-into-and-out-of-workflow-services/add-receive-activity.jpg)  
  
7. Cliquez sur le lien **définir...** dans <xref:System.ServiceModel.Activities.Receive> l’activité et définissez les paramètres suivants :  
  
     ![Définition des paramètres de message pour l’activité Receive](./media/flowing-transactions-into-and-out-of-workflow-services/receive-message-settings.jpg)  
  
8. Faites glisser et déposez une activité <xref:System.Activities.Statements.Sequence> dans la section de corps du <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Dans l’activité <xref:System.Activities.Statements.Sequence>, faites glisser et déposez deux activités <xref:System.Activities.Statements.WriteLine> et définissez les propriétés <xref:System.Activities.Statements.WriteLine.Text%2A> conformément aux indications du tableau suivant.  
  
    |Activité|Valeur|  
    |--------------|-----------|  
    |1re WriteLine|Services Réception terminée»|  
    |2e WriteLine|Services Received = "+ requestMessage|  
  
     Le workflow doit maintenant ressembler à ceci :  
  
     ![Séquence après l’ajout d’activités WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-writelines.jpg)  
  
9. Faites glisser et déposez l' `PrintTransactionInfo` activité après la deuxième <xref:System.ServiceModel.Activities.TransactedReceiveScope> <xref:System.Activities.Statements.WriteLine> activité dans le corps de l’activité.  
  
     ![Séquence après l’ajout de PrintTransactionInfo](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-printtransactioninfo.jpg )  
  
10. Faites glisser et déposez une activité <xref:System.Activities.Statements.Assign> après l’activité `PrintTransactionInfo` et définissez ses propriétés conformément aux indications du tableau suivant.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |À|replyMessage|  
    |Valeur|Services Envoi de la réponse».|  
  
11. Faites glisser et déposez une <xref:System.Activities.Statements.WriteLine> activité après l’activité <xref:System.Activities.Statements.WriteLine.Text%2A> et affectez à sa propriété la <xref:System.Activities.Statements.Assign> valeur «service : BEGIN reply».  
  
     Le workflow doit maintenant ressembler à ceci :  
  
     ![Après l'ajout de Assign et de WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/after-adding-sbr-writeline.jpg)  
  
12. Cliquez avec le <xref:System.ServiceModel.Activities.Receive> bouton droit sur l’activité, puis sélectionnez **Create SendReply** et collez-la après la dernière <xref:System.Activities.Statements.WriteLine> activité. Cliquez sur le lien **définir...** dans `SendReplyToReceive` l’activité et définissez les paramètres suivants.  
  
     ![Paramètres des messages Reply](./media/flowing-transactions-into-and-out-of-workflow-services/reply-message-settings.jpg)  
  
13. Faites glisser et déposez <xref:System.Activities.Statements.WriteLine> une `SendReplyToReceive` activité après l' <xref:System.Activities.Statements.WriteLine.Text%2A> activité et affectez à sa propriété la valeur "service : Réponse envoyée».  
  
14. Faites glisser et déposez une <xref:System.Activities.Statements.WriteLine> activité en bas du workflow et affectez à sa <xref:System.Activities.Statements.WriteLine.Text%2A> propriété la valeur «service : Le flux de travail se termine, appuyez sur entrée pour quitter.»  
  
     Le workflow de service terminé doit ressembler à ceci :  
  
     ![Flux de travail du service complet](./media/flowing-transactions-into-and-out-of-workflow-services/service-complete-workflow.jpg)  
  
### <a name="implement-the-workflow-client"></a>Implémenter le client de workflow  
  
1. Ajoutez une nouvelle application de workflow WCF nommée `WorkflowClient` au projet `Common`. Pour ce faire, cliquez avec `Common` le bouton droit sur le projet, sélectionnez **Ajouter**, **nouvel élément...** , sélectionnez **Workflow** sous **modèles installés** , puis sélectionnez **activité**.  
  
     ![Ajouter un projet d'activité](./media/flowing-transactions-into-and-out-of-workflow-services/add-activity-project.jpg)  
  
2. Faites glisser et déposez une activité <xref:System.Activities.Statements.Sequence> sur l’aire de conception.  
  
3. Dans l’activité <xref:System.Activities.Statements.Sequence>, faites glisser et déposez une activité <xref:System.Activities.Statements.WriteLine> et affectez à sa propriété <xref:System.Activities.Statements.WriteLine.Text%2A> la valeur `"Client: Workflow starting"`. Le workflow doit maintenant ressembler à ceci :  
  
     ![Ajouter une activité WriteLine](./media/flowing-transactions-into-and-out-of-workflow-services/add-writeline-activity.jpg)  
  
4. Faites glisser une activité <xref:System.Activities.Statements.TransactionScope> après l'activité <xref:System.Activities.Statements.WriteLine>.  Sélectionnez l'activité <xref:System.Activities.Statements.TransactionScope>, cliquez sur le bouton Variables et ajoutez les variables suivantes.  
  
     ![Ajouter des variables à TransactionScope](./media/flowing-transactions-into-and-out-of-workflow-services/transactionscope-variables.jpg)  
  
5. Faites glisser et déposez une activité <xref:System.Activities.Statements.Sequence> dans le corps de l’activité <xref:System.Activities.Statements.TransactionScope>.  
  
6. Faites glisser une activité `PrintTransactionInfo` dans <xref:System.Activities.Statements.Sequence>.  
  
7. Faites glisser et déposez une <xref:System.Activities.Statements.WriteLine> activité après l’activité <xref:System.Activities.Statements.WriteLine.Text%2A> et affectez à sa propriété la `PrintTransactionInfo` valeur «client : Début de l’envoi». Le workflow doit maintenant ressembler à ceci :  
  
     ![Ajout du client : Début des activités d’envoi](./media/flowing-transactions-into-and-out-of-workflow-services/client-add-cbs-writeline.jpg)  
  
8. Faites glisser une activité <xref:System.ServiceModel.Activities.Send> après l'activité <xref:System.Activities.Statements.Assign> et définissez les propriétés suivantes :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |EndpointConfigurationName|workflowServiceEndpoint|  
    |OperationName|StartSample|  
    |ServiceContractName|ITransactionSample|  
  
     Le workflow doit maintenant ressembler à ceci :  
  
     ![Définition des propriétés de l'activité Send](./media/flowing-transactions-into-and-out-of-workflow-services/client-send-activity-settings.jpg)  
  
9. Cliquez sur le lien **définir...** et définissez les paramètres suivants :  
  
     ![Paramètres des messages de l'activité Send](./media/flowing-transactions-into-and-out-of-workflow-services/send-message-settings.jpg)  
  
10. Cliquez avec le <xref:System.ServiceModel.Activities.Send> bouton droit sur l’activité, puis sélectionnez **créer ReceiveReply**. L'activité <xref:System.ServiceModel.Activities.ReceiveReply> sera automatiquement placée après l'activité <xref:System.ServiceModel.Activities.Send>.  
  
11. Cliquez sur le lien Définir de l'activité ReceiveReplyForSend et effectuez les paramétrages suivants :  
  
     ![Définition des paramètres de message ReceiveForSend](./media/flowing-transactions-into-and-out-of-workflow-services/client-reply-message-settings.jpg)  
  
12. Faites glisser et déposez une <xref:System.Activities.Statements.WriteLine> activité <xref:System.ServiceModel.Activities.ReceiveReply> entre les activités et <xref:System.Activities.Statements.WriteLine.Text%2A> et affectez à sa propriété la <xref:System.ServiceModel.Activities.Send> valeur «client : Envoi terminé».  
  
13. Faites glisser et déposez <xref:System.Activities.Statements.WriteLine> une <xref:System.ServiceModel.Activities.ReceiveReply> activité après l’activité <xref:System.Activities.Statements.WriteLine.Text%2A> et définissez sa propriété sur «côté client : Reply received = "+ replyMessage  
  
14. Faites glisser une activité `PrintTransactionInfo` après l'activité <xref:System.Activities.Statements.WriteLine>.  
  
15. Faites glisser une activité <xref:System.Activities.Statements.WriteLine> à la fin du workflow et affectez à sa propriété <xref:System.Activities.Statements.WriteLine.Text%2A> la valeur "Client workflow ends." Le workflow du client terminé doit ressembler au diagramme suivant.  
  
     ![Workflow client terminé](./media/flowing-transactions-into-and-out-of-workflow-services/client-complete-workflow.jpg)  
  
16. Générez la solution.  
  
### <a name="create-the-service-application"></a>Créer l'application Service  
  
1. Ajoutez à la solution un nouveau projet d'application console nommé `Service`. Ajoutez des références aux assemblys suivants :  
  
    1. System.Activities.dll  
  
    2. System.ServiceModel.dll  
  
    3. System.ServiceModel.Activities.dll  
  
2. Ouvrez le fichier Program.cs généré et le code suivant :  
  
    ```csharp
          static void Main()  
          {  
              Console.WriteLine("Building the server.");  
              using (WorkflowServiceHost host = new WorkflowServiceHost(new DeclarativeServiceWorkflow(), new Uri("net.tcp://localhost:8000/TransactedReceiveService/Declarative")))  
              {                
                  //Start the server  
                  host.Open();  
                  Console.WriteLine("Service started.");  
  
                  Console.WriteLine();  
                  Console.ReadLine();  
                  //Shutdown  
                  host.Close();  
              };         
          }  
    ```  
  
3. Ajoutez le fichier app.config suivant au projet.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <!-- Copyright © Microsoft Corporation.  All rights reserved. -->  
    <configuration>  
        <system.serviceModel>  
            <bindings>  
                <netTcpBinding>  
                    <binding transactionFlow="true" />  
                </netTcpBinding>  
            </bindings>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="create-the-client-application"></a>Créer l'application Client  
  
1. Ajoutez à la solution un nouveau projet d'application console nommé `Client`. Ajoutez une référence à System.Activities.dll.  
  
2. Ouvrez le fichier program.cs et ajoutez le code suivant.  
  
    ```csharp
        class Program  
        {  
  
            private static AutoResetEvent syncEvent = new AutoResetEvent(false);  
  
            static void Main(string[] args)  
            {  
                //Build client  
                Console.WriteLine("Building the client.");  
                WorkflowApplication client = new WorkflowApplication(new DeclarativeClientWorkflow());  
                client.Completed = Program.Completed;  
                client.Aborted = Program.Aborted;  
                client.OnUnhandledException = Program.OnUnhandledException;  
  
                //Wait for service to start  
                Console.WriteLine("Press ENTER once service is started.");  
                Console.ReadLine();  
  
                //Start the client              
                Console.WriteLine("Starting the client.");  
                client.Run();  
                syncEvent.WaitOne();  
  
                //Sample complete  
                Console.WriteLine();  
                Console.WriteLine("Client complete. Press ENTER to exit.");  
                Console.ReadLine();  
            }  
  
            private static void Completed(WorkflowApplicationCompletedEventArgs e)  
            {  
                Program.syncEvent.Set();  
            }  
  
            private static void Aborted(WorkflowApplicationAbortedEventArgs e)  
            {  
                Console.WriteLine("Client Aborted: {0}", e.Reason);  
                Program.syncEvent.Set();  
            }  
  
            private static UnhandledExceptionAction OnUnhandledException(WorkflowApplicationUnhandledExceptionEventArgs e)  
            {  
                Console.WriteLine("Client had an unhandled exception: {0}", e.UnhandledException);  
                return UnhandledExceptionAction.Cancel;  
            }  
        }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Services de workflow](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Vue d’ensemble des transactions Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/transactions-overview.md)
