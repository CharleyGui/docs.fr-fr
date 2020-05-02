---
title: Security Validation
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 90d335f32c43ecf575c69cf800ab69bee05f39ee
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728381"
---
# <a name="security-validation"></a>Validation de la sécurité
Cet exemple montre comment utiliser un comportement personnalisé pour valider des services sur un ordinateur afin de garantir qu'ils répondent à des critères spécifiques. Dans cet exemple, les services sont validés par le comportement personnalisé en analysant chaque point de terminaison sur le service et en vérifiant s'ils contiennent des éléments de liaison sécurisés. Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
## <a name="endpoint-validation-custom-behavior"></a>Comportement personnalisé de validation de point de terminaison  
 En ajoutant le code utilisateur à la méthode `Validate` contenue dans l'interface <xref:System.ServiceModel.Description.IServiceBehavior>, le comportement personnalisé peut être attribué à un service ou un point de terminaison pour effectuer des actions définies par l'utilisateur. Le code suivant est utilisé pour parcourir chaque point de terminaison contenu dans un service et rechercher des liaisons sécurisées dans leurs collections de liaisons.  
  
```csharp
public void Validate(ServiceDescription serviceDescription,
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their
    // binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any
        // secure binding elements. Transport, Asymmetric, and Symmetric
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 L’ajout du code suivant au fichier Web.config ajoute l’extension de comportement `serviceValidate` au service à reconnaître.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>
    ...
</system.serviceModel>
```  
  
 Une fois l’extension de comportement ajoutée au service, il est possible d’ajouter le comportement `endpointValidate` à la liste de comportements dans le fichier Web.config et donc, au service.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 Les comportements et leurs extensions ajoutés au fichier Web.config appliquent le comportement aux services individuels, tandis qu’en cas d’ajout au fichier Machine.config, ils appliquent le comportement à chaque service actif sur l’ordinateur.  
  
> [!NOTE]
> Lors de l'ajout du comportement à tous les services, il est recommandé de sauvegarder le fichier Machine.config avant d'apporter toute modification.  
  
 Exécutez maintenant le client fourni dans le répertoire client\bin de cet exemple. Une exception est levée avec le message suivant : « impossible d’activer le servicehttp://localhost/servicemodelsamples/service.svcdemandé « ». Cette exception est attendue parce qu'un point de terminaison est considéré comme non sécurisé par le comportement de validation de point de terminaison et empêche le démarrage du service. Le comportement lève également une exception interne qui décrit quel point de terminaison n'est pas sécurisé et écrit un message à l'observateur d'événements du système sous la source « System.ServiceModel 4.0.0.0 » et la catégorie « WebHost ». Il est également possible d'activer le suivi sur le service dans cet exemple. Cela permet à l'utilisateur de consulter les exceptions levées par le comportement de validation de point de terminaison en ouvrant les suivis du service à l'aide de l'outil Service Trace Viewer.  
  
### <a name="view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Affichez les messages d’exception de validation de point de terminaison ayant échoué dans le observateur d’événements  
  
1. Cliquez sur le menu **Démarrer** et sélectionnez **exécuter...**.  
  
2. Tapez `eventvwr` puis cliquez sur **OK**.  
  
3. Dans la fenêtre observateur d’événements, cliquez sur **application**.  
  
4. Double-cliquez sur l’événement « System. ServiceModel 4.0.0.0 » ajouté récemment sous la catégorie « WebHost » dans la fenêtre d' **application** pour afficher les messages de point de terminaison non sécurisés.  
  
## <a name="set-up-build-and-run-the-sample"></a>Configurer, générer et exécuter l’exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Voir aussi

- [Exemples d'analyse AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
