---
title: Demande-réponse non typée
ms.date: 03/30/2017
ms.assetid: 0bf0f9d9-7caf-4d3d-8c9e-2d468cca16a5
ms.openlocfilehash: 46047d1671fadb18052991451910b9056015edd2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591098"
---
# <a name="untyped-requestreply"></a>Untyped Request/Reply
Cet exemple montre comment définir des contrats d'opération qui utilisent la classe Message.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple est basé sur le [prise en main](getting-started-sample.md). Le contrat de service définit une opération qui prend un type de message comme argument et retourne un message. L'opération recueille toutes les données requises pour calculer la somme du corps du message puis envoie la somme dans le corps du message de retour.  
  
```csharp
[OperationContract(Action = CalculatorService.RequestAction, ReplyAction = CalculatorService.ReplyAction)]  
Message ComputeSum(Message request);  
```  
  
 Sur le service, l'opération récupère le tableau d'entiers passé dans le message d'entrée puis calcule la somme. Pour envoyer un message de réponse, l'exemple crée un nouveau message avec la version de message et l'action appropriées et inclut la somme calculée dans son corps. C'est ce que montre l'exemple de code suivant.  
  
```csharp
public Message ComputeSum(Message request)  
{  
    //The body of the message contains a list of numbers which will be
    //read as a int[] using GetBody<T>  
    int result = 0;  
  
    int[] inputs = request.GetBody<int[]>();  
    foreach (int i in inputs)  
    {  
        result += i;  
    }  
  
    Message response = Message.CreateMessage(request.Version,
                                      ReplyAction, result);  
    return response;  
}  
```  
  
 Le client utilise le code généré par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un proxy pour le service distant. Pour envoyer un message de demande, le client doit connaître la version du message, qui dépend du canal sous-jacent. Donc, il crée une <xref:System.ServiceModel.OperationContextScope> étendue au canal proxy qu'il a créé, ce qui crée un <xref:System.ServiceModel.OperationContext> avec la version de message correcte indiquée à la propriété `OutgoingMessageHeaders.MessageVersion`. Le client passe un tableau d'entrées dans le corps du message de demande puis appelle `ComputeSum` sur le proxy. Le client récupère ensuite la somme des entrées qu'il a passées en accédant à la méthode `GetBody<T>` depuis le message de réponse. C'est ce que montre l'exemple de code suivant.  
  
```csharp
using (new OperationContextScope(client.InnerChannel))  
{  
    // Call the Sum service operation.  
    int[] values = { 1, 2, 3, 4, 5 };  
    Message request = Message.CreateMessage(  
        OperationContext.Current.OutgoingMessageHeaders.MessageVersion,
        RequestAction, values);  
    Message reply = client.ComputeSum(request);  
    int response = reply.GetBody<int>();  
  
    Console.WriteLine("Sum of numbers passed (1,2,3,4,5) = {0}",
                                                       response);  
}  
```  
  
 Cet exemple est un exemple hébergé sur le Web donc seul le fichier exécutable client doit être exécuté. L'exemple suivant illustre la sortie sur le client.  
  
```console  
Prompt>Client.exe  
Sum of numbers passed (1,2,3,4,5) = 15  
  
Press <ENTER> to terminate client.  
```  
  
 Cet exemple est un exemple hébergé sur le Web : suivez le lien fourni à l'étape 3 pour voir comment générer et exécuter l'exemple.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Untyped`  
