---
title: Accès aux services WCF avec une application cliente Windows Store
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: 9316a46f809eec21f73e8eeadb49baf1748c6ca0
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988252"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Accès aux services WCF avec une application cliente Windows Store
Windows 8 introduit un nouveau type d'application appelé applications du Windows Store. Ces applications sont conçues autour d'une interface d'écran tactile. .NET Framework 4.5 permet aux applications du Windows Store d'appeler des services WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Prise en charge de WCF dans les applications du Windows Store  
 Un sous-ensemble de fonctionnalités WCF est disponible dans une application du Windows Store. Pour plus d'informations, consultez les sections suivantes.  
  
> [!IMPORTANT]
> Utilisez les API de syndication WinRT au lieu de celles exposées par WCF. Pour plus d’informations, consultez [API de syndication WinRT](https://go.microsoft.com/fwlink/?LinkId=236265)  
  
> [!WARNING]
> L'utilisation de la fonctionnalité Ajouter une référence de service pour ajouter une référence de service Web à un composant d'exécution Windows n'est pas pris en charge.  
  
### <a name="supported-bindings"></a>Liaisons prises en charge  
 Les liaisons WCF suivantes sont prises en charge dans les applications du Windows Store :  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 Les éléments de liaison suivants sont pris en charge dans les applications du Windows Store :  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Les encodages de texte et binaires sont pris en charge. Tous les modes de transfert WCF sont pris en charge. Pour plus d’informations, consultez [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Ajouter une référence de service  
 Pour appeler un service WCF d'une application du Windows Store, utilisez la fonctionnalité Ajouter une référence de service de Visual Studio 2012. Vous remarquerez certaines modifications apportées à la fonctionnalité Ajouter une référence de service exécutée dans une application du Windows Store. Tout d'abord, aucun fichier de configuration n'est généré. Les applications du Windows Store n'utilisent pas les fichiers de configuration, elles doivent être configurées dans le code. Ce code de configuration se trouve dans le fichier References.cs généré par la fonctionnalité Ajouter une référence de service. Pour afficher ce fichier, veillez à sélectionner «Afficher tous les fichiers» dans l’Explorateur de solutions. Le fichier se trouve sous les nœuds Références de service et Reference.svcmap dans le projet. Toutes les opérations générées pour les services WCF dans une application du Windows Store seront des opérations asynchrones à l'aide du modèle asynchrone basé sur des tâches. Pour plus d’informations, consultez [tâches Async-simplifier la programmation asynchrone avec des tâches](https://msdn.microsoft.com/magazine/ff959203.aspx).  
  
 Comme la configuration est maintenant générée dans le code, toutes les modifications effectuées dans le fichier Reference.cs sont remplacées à chaque mise à jour de la référence de service. Pour remédier à cette situation, le code de configuration est généré dans une méthode partielle, que vous pouvez implémenter dans votre classe proxy client. La méthode partielle est déclarée comme suit :  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 Vous pouvez ensuite appliquer cette méthode partielle et modifier la liaison ou le point de terminaison dans votre classe proxy client comme suit :  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {   
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,   
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a>Sérialisation  
 Les sérialiseurs suivants sont pris en charge dans les applications du Windows Store :  
  
1. DataContractSerializer  
  
2. DataContractJsonSerializer  
  
3. XmlSerializer  
  
> [!WARNING]
> XmlDictionaryWriter.Write(DateTime) écrit maintenant l'objet DateTime en tant que chaîne.  
  
### <a name="security"></a>Sécurité  

Les modes de sécurité suivants sont pris en charge dans les applications du Windows Store:
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
Les types d’informations d’identification du client suivants sont pris en charge dans les applications du Windows Store:
  
1. Aucun  
  
2. De base  
  
3. Digest  
  
4. Par négociation  
  
5. NTLM  
  
6. Windows  
  
7. Nom d'utilisateur (sécurité du message)  
  
8. Windows (sécurité du transport)  
  
 Pour que les applications du Windows Store accèdent aux informations d'identification Windows par défaut et les envoient, vous devez activer cette fonctionnalité dans le fichier Package.appmanifest. Ouvrez ce fichier et sélectionnez l’onglet capacités, puis sélectionnez «informations d’identification Windows par défaut». Cela permet à l'application de se connecter aux ressources intranet qui nécessitent des informations d'identification de domaine.  
  
> [!IMPORTANT]
> Pour que les applications du Windows Store effectuent des appels inter-ordinateurs, vous devez activer une autre fonctionnalité appelée «mise en réseau pour le Bureau à distance». Ce paramètre se trouve également dans le fichier Package.appmanifest sous l'onglet Capacités. Activez la case à cocher Réseau domestique/de bureau. Cela donne à votre application un accès entrant et sortant au réseau des lieux approuvés par l'utilisateur, tels que le domicile et le bureau. Les ports entrants critiques sont toujours bloqués. Pour accéder aux services sur Internet, vous devez également activer la fonction Internet (client).  
  
### <a name="misc"></a>Divers  
 L'utilisation des classes suivantes est prise en charge pour les applications du Windows Store :  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>Définition des contrats de service  
 Nous vous recommandons de définir les opérations de service asynchrones uniquement à l'aide du modèle asynchrone basé sur des tâches. Cela garantit que les applications du Windows Store restent réactives lors de l'appel d'une opération de service.  
  
> [!WARNING]
> Même si aucune exception n'est levée si vous définissez une opération synchrone, il est vivement recommandé de définir uniquement des opérations asynchrones.  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Appels de services WCF des applications du Windows Store  
 Comme mentionné précédemment, toute la configuration doit être effectuée dans le code de la méthode GetBindingForEndpoint de la classe proxy générée. L'appel d'une opération de service est identique à l'appel d'une méthode asynchrone basée sur des tâches comme indiqué dans l'extrait de code suivant.  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 Notez l'utilisation du mot clé async dans la méthode qui effectue l'appel asynchrone et du mot clé await lors de l'appel de la méthode asynchrone.  
  
## <a name="see-also"></a>Voir aussi

- [WCF dans le blog des applications du Windows Store](https://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)
- [Clients du Windows Store WCF et sécurité](https://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)
- [Applications du Windows Store et appels entre ordinateurs](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [Appel d’un service WCF déployé dans Azure à partir d’une application du Windows Store](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [Programmation de la sécurité dans WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Liaisons](../../../../docs/framework/wcf/bindings.md)
