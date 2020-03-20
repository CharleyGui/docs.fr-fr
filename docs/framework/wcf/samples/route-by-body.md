---
title: Route by Body
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: c3f4b19e646a6a9716d2264a3969b339208c60a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144186"
---
# <a name="route-by-body"></a>Route by Body
Cet exemple montre comment implémenter un service qui accepte des objets de message avec toute action SOAP. Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui met en œuvre un service de calculatrice. Le service implémente une opération `Calculate` unique qui accepte un paramètre de demande <xref:System.ServiceModel.Channels.Message> et retourne une réponse <xref:System.ServiceModel.Channels.Message>.  
  
 Dans cet exemple, le client est une application console (.exe) et le service est hébergé dans IIS.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'exemple illustre la distribution des messages selon le contenu du corps. Le mécanisme intégré de répartition des messages du modèle de service de la Windows Communication Foundation (WCF) est basé sur les actions de message. Toutefois, il existe de nombreux services Web qui définissent toutes leurs opérations avec l'action="". Il est impossible de générer un service reposant sur WSDL qui continue à distribuer des messages de demande selon les informations d'action. Cet exemple montre un contrat de service basé sur WSDL (WSDL est contenu dans Service.wsdl, lui-même inclus dans l'exemple). Le contrat de service est Calculator, similaire à celui utilisé dans [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md). Toutefois, le `[OperationContract]` spécifie `Action=""` pour toutes les opérations.  
  
```csharp  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 Selon le contrat, le service requiert le comportement de distribution personnalisé `DispatchByBodyBehavior` pour autoriser les messages à être distribués entre des opérations. Ce comportement de répartition `DispatchByBodyElementOperationSelector` initialise le sélecteur d’opération personnalisé avec une table des noms d’opération clés par QName d’éléments d’emballage respectifs. `DispatchByBodyElementOperationSelector` examine la balise de début du premier enfant du corps et sélectionne l'opération à l'aide du tableau mentionné précédemment.  
  
 Le client utilise un proxy auto-généré à partir de la WSDL exportée par le service à l’aide [de ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Le fait que les actions de toutes les opérations soient vides n'a aucun impact sur le code client, à l'exception des paramètres d'action du proxy généré automatiquement.  
  
 Le code client effectue plusieurs calculs. Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
2. Pour construire la solution, suivez les instructions dans [la construction des échantillons de la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
