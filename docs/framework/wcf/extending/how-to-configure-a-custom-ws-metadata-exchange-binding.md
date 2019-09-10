---
title: 'Procédure : configurer une liaison WS-Metadata Exchange personnalisée'
ms.date: 03/30/2017
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
ms.openlocfilehash: b4a4005a23c8c74edecb00475669e019b50a17af
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851223"
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a>Procédure : configurer une liaison WS-Metadata Exchange personnalisée
Cette rubrique explique comment configurer une liaison d'échange WS-Metadata personnalisée. Windows Communication Foundation (WCF) comprend quatre liaisons de métadonnées définies par le système, mais vous pouvez publier des métadonnées à l’aide de n’importe quelle liaison de votre choix. Cette rubrique indique comment publier des métadonnées à l'aide du `wsHttpBinding`. Cette liaison vous donne la possibilité d’exposer des métadonnées de manière sécurisée. Le code de cet article est basé sur le [prise en main](../samples/getting-started-sample.md).  
  
### <a name="using-a-configuration-file"></a>Utilisation d'un fichier de configuration  
  
1. Dans le fichier de configuration du service, ajoutez un comportement de service qui contient la balise `serviceMetadata` :  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2. Ajoutez un attribut `behaviorConfiguration` à la balise de service qui référence ce nouveau comportement :  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3. Ajoutez un point de terminaison de métadonnées qui spécifie mex comme adresse, `wsHttpBinding` comme liaison et <xref:System.ServiceModel.Description.IMetadataExchange> comme contrat :  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4. Pour vérifier que le point de terminaison d’échange de métadonnées fonctionne correctement, ajoutez une étiquette de point de terminaison dans le fichier de configuration de client :  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5. Dans la méthode Main() du client, créez une instance <xref:System.ServiceModel.Description.MetadataExchangeClient>, affectez à sa propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> la valeur `true`, appelez <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, puis effectuez une itération au sein de la collection de métadonnées retournée :  
  
    ```csharp
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a>Configuration par code  
  
1. Créez une instance de liaison <xref:System.ServiceModel.WSHttpBinding> :  
  
    ```csharp  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2. Créez une instance <xref:System.ServiceModel.ServiceHost> :  
  
    ```csharp  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3. Ajoutez un point de terminaison de service et ajoutez une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior> :  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4. Ajoutez un point de terminaison d'échange de métadonnées, en spécifiant le <xref:System.ServiceModel.WSHttpBinding> créé précédemment :  
  
    ```csharp  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5. Pour vérifier que le point de terminaison d’échange de métadonnées fonctionne correctement, ajoutez une étiquette de point de terminaison dans le fichier de configuration de client :  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6. Dans la méthode Main() du client, créez une instance <xref:System.ServiceModel.Description.MetadataExchangeClient>, affectez à la propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> la valeur `true`, appelez <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, puis effectuez une itération au sein de la collection de métadonnées retournée :  
  
    ```csharp  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Comportement de publication des métadonnées](../samples/metadata-publishing-behavior.md)
- [Récupérer des métadonnées](../samples/retrieve-metadata.md)
- [Métadonnées](../feature-details/metadata.md)
- [Publication de métadonnées](../feature-details/publishing-metadata.md)
- [Publication de points de terminaison de métadonnées](../publishing-metadata-endpoints.md)
