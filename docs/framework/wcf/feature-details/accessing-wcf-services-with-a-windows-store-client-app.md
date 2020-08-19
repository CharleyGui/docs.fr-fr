---
title: Accès aux services WCF avec une application cliente Windows Store
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: ed13a88e3a534cd586d9386396802d7457de56e7
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558970"
---
# <a name="access-wcf-services-with-a-windows-store-client-app"></a>Accéder aux services WCF avec une application cliente Windows Store

Windows 8 introduit un nouveau type d'application appelé applications du Windows Store. Ces applications sont conçues autour d'une interface d'écran tactile. .NET Framework 4.5 permet aux applications du Windows Store d'appeler des services WCF.  
  
## <a name="wcf-support-in-windows-store-applications"></a>Prise en charge de WCF dans les applications du Windows Store  
 Un sous-ensemble de fonctionnalités WCF est disponible dans une application du Windows Store. Pour plus d'informations, consultez les sections suivantes.  
  
> [!IMPORTANT]
> Utilisez les API de syndication WinRT au lieu de celles exposées par WCF. Pour plus d’informations, consultez [API de syndication WinRT](xref:Windows.Web.Syndication)  
  
> [!WARNING]
> L’utilisation de Ajouter une référence de service pour ajouter une référence de service Web à un composant de Windows Runtime n’est pas prise en charge.  
  
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
  
 Les encodages de texte et binaires sont pris en charge. Tous les modes de transfert WCF sont pris en charge. Pour plus d’informations, consultez [Streaming Message Transfer](streaming-message-transfer.md).  
  
### <a name="add-service-reference"></a>Ajouter une référence de service  
 Pour appeler un service WCF d'une application du Windows Store, utilisez la fonctionnalité Ajouter une référence de service de Visual Studio 2012. Vous remarquerez certaines modifications apportées à la fonctionnalité Ajouter une référence de service exécutée dans une application du Windows Store. Tout d'abord, aucun fichier de configuration n'est généré. Les applications du Windows Store n'utilisent pas les fichiers de configuration, elles doivent être configurées dans le code. Ce code de configuration se trouve dans le fichier References.cs généré par la fonctionnalité Ajouter une référence de service. Pour afficher ce fichier, veillez à sélectionner « Afficher tous les fichiers » dans l’Explorateur de solutions. Le fichier se trouve sous les nœuds Références de service et Reference.svcmap dans le projet. Toutes les opérations générées pour les services WCF dans une application du Windows Store seront des opérations asynchrones à l'aide du modèle asynchrone basé sur des tâches. Pour plus d’informations, consultez [tâches Async-simplifier la programmation asynchrone avec des tâches](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).  
  
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

Les modes de sécurité suivants sont pris en charge dans les applications du Windows Store :
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
Les types d’informations d’identification du client suivants sont pris en charge dans les applications du Windows Store :
  
1. None  
  
2. De base  
  
3. Digest  
  
4. Negotiate  
  
5. NTLM  
  
6. Windows  
  
7. Nom d'utilisateur (sécurité du message)  
  
8. Windows (sécurité du transport)  
  
 Pour que les applications du Windows Store accèdent aux informations d'identification Windows par défaut et les envoient, vous devez activer cette fonctionnalité dans le fichier Package.appmanifest. Ouvrez ce fichier et sélectionnez l’onglet capacités, puis sélectionnez « informations d’identification Windows par défaut ». Cela permet à l'application de se connecter aux ressources intranet qui nécessitent des informations d'identification de domaine.  
  
> [!IMPORTANT]
> Pour que les applications du Windows Store effectuent des appels inter-ordinateurs, vous devez activer une autre fonctionnalité appelée « mise en réseau pour le Bureau à distance ». Ce paramètre se trouve également dans le fichier Package. AppManifest sous l’onglet capacités. activez la case à cocher Bureau à distance/travail. Cela donne à votre application un accès entrant et sortant aux réseaux des lieux de confiance de l’utilisateur, tels que les points de départ et de travail. Les ports entrants critiques sont toujours bloqués. Pour accéder aux services sur Internet, vous devez également activer la fonction Internet (client).  
  
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

- [Programmation de la sécurité dans WCF](programming-wcf-security.md)
- [Liaisons](../bindings.md)
