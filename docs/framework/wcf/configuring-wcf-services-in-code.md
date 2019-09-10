---
title: Configuration de services WCF dans le code
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: d2ef7b2095bf7f238a25f2db0e5d3cf47e885550
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855641"
---
# <a name="configuring-wcf-services-in-code"></a>Configuration de services WCF dans le code
Windows Communication Foundation (WCF) permet aux développeurs de configurer des services à l’aide de fichiers de configuration ou de code.  Les fichiers de configuration sont utiles lorsqu'un service doit être configuré après avoir été déployé. Lorsqu'il utilise des fichiers de configuration, un professionnel de l'informatique doit uniquement mettre à jour le fichier de configuration, aucune recompilation n'est nécessaire. Les fichiers de configuration, toutefois, peuvent être complexes et difficiles à gérer. Il n'existe aucune prise en charge du débogage de fichiers de configuration et les éléments de configuration sont référencés par des noms. La création de fichiers de configuration est donc susceptible d'engendrer des erreurs et difficile. WCF vous permet également de configurer des services dans le code. Dans les versions précédentes de WCF (4,0 et versions antérieures) la configuration des services dans le code était facile dans les scénarios <xref:System.ServiceModel.ServiceHost> auto-hébergés, la classe vous permettait de configurer des points de terminaison et des comportements avant d’appeler ServiceHost. Open. Dans les scénarios hébergés sur le Web, toutefois, vous n'avez pas accès direct à la classe <xref:System.ServiceModel.ServiceHost>. Pour configurer un service hébergé sur le Web vous deviez créer un `System.ServiceModel.ServiceHostFactory` qui créait le <xref:System.ServiceModel.Activation.ServiceHostFactory> et effectuait la configuration nécessaire. À compter de .NET 4,5, WCF offre un moyen plus simple de configurer des services auto-hébergés et hébergés sur le Web dans le code.  
  
## <a name="the-configure-method"></a>Méthode Configure  
 Il suffit de définir une méthode statique publique appelée `Configure` avec la signature suivante dans votre classe d'implémentation de service :  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 La méthode Configure prend une instance <xref:System.ServiceModel.ServiceConfiguration> qui permet au développeur d'ajouter des points de terminaison et des comportements. Cette méthode est appelée par WCF avant l’ouverture de l’hôte de service. S'ils sont définis, les paramètres de configuration du service spécifiés dans un fichier app.config ou web.config sont ignorés.  
  
 L'extrait de code suivant montre comment définir la méthode `Configure` et ajouter un point de terminaison de service, un comportement de point de terminaison et des comportements de service :  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 Pour activer un protocole tel que https pour un service, vous pouvez soit ajouter explicitement un point de terminaison qui utilise le protocole ou vous pouvez ajouter automatiquement des points de terminaison en appelant ServiceConfiguration.EnableProtocol (Binding) qui ajoute un point de terminaison pour chaque adresse de base compatible avec le protocole et chaque contrat de service défini. L'exemple de code suivant illustre l'utilisation de la méthode ServiceConfiguration.EnableProtocol :  
  
```csharp  
public class Service1 : IService1   
{   
    public string GetData(int value);   
    public static void Configure(ServiceConfiguration config)   
    {   
        // Enable "Add Service Reference" support   
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });   
       // set up support for http, https, net.tcp, net.pipe   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new BasicHttpBinding());   
       config.EnableProtocol(new NetTcpBinding());   
       config.EnableProtocol(new NetNamedPipeBinding());   
       // add an extra BasicHttpBinding endpoint at http:///basic   
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");   
    }   
}   
```  
  
 Les paramètres de la section`protocolMappings`> < sont utilisés uniquement si aucun point <xref:System.ServiceModel.ServiceConfiguration> de terminaison d’application n’est ajouté par programmation à. Vous pouvez éventuellement charger la configuration du service à partir du fichier de configuration de l' <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> application par défaut en appelant, puis modifier les paramètres. La classe <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> vous permet également de charger la configuration à partir d'une configuration centralisée. Le code suivant illustre comment implémenter cela :  
  
```csharp
public class Service1 : IService1   
{   
    public void DoWork();   
    public static void Configure(ServiceConfiguration config)   
    {   
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));   
    }   
}  
```  
  
> [!IMPORTANT]
> Notez que <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A> ignore <`host`paramètres de > dans la`service`balise de >`system.serviceModel`< de < >. Conceptuellement, <`host`> concerne la configuration de l’hôte, et non la configuration du service, et il est chargé avant l’exécution de la méthode de configuration.  
  
## <a name="see-also"></a>Voir aussi

- [Configuration des services à l’aide de fichiers de configuration](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)
- [Configuration des comportements clients](../../../docs/framework/wcf/configuring-client-behaviors.md)
- [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md)
- [Configuration](../../../docs/framework/wcf/samples/configuration-sample.md)
- [Activation basée sur la configuration dans les services IIS et WAS](../../../docs/framework/wcf/feature-details/configuration-based-activation-in-iis-and-was.md)
- [Prise en charge de la configuration et des métadonnées](../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
- [Configuration](../../../docs/framework/wcf/diagnostics/exceptions-reference/configuration.md)
- [Guide pratique pour Spécifier une liaison de service dans la configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Guide pratique : Créer un point de terminaison de service dans la configuration](../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [Guide pratique pour Publier les métadonnées d’un service à l’aide d’un fichier de configuration](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Guide pratique pour Spécifier une liaison de client dans la configuration](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
