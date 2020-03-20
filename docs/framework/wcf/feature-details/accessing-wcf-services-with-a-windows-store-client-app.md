---
title: Accès aux services WCF avec une application cliente Windows Store
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: b4b91c103aa91e3b2c9e811c642a8347c7db1a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185483"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="1071d-102">Accès aux services WCF avec une application cliente Windows Store</span><span class="sxs-lookup"><span data-stu-id="1071d-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="1071d-103">Windows 8 introduit un nouveau type d'application appelé applications du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="1071d-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="1071d-104">Ces applications sont conçues autour d'une interface d'écran tactile.</span><span class="sxs-lookup"><span data-stu-id="1071d-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="1071d-105">.NET Framework 4.5 permet aux applications du Windows Store d'appeler des services WCF.</span><span class="sxs-lookup"><span data-stu-id="1071d-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="1071d-106">Prise en charge de WCF dans les applications du Windows Store</span><span class="sxs-lookup"><span data-stu-id="1071d-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="1071d-107">Un sous-ensemble de fonctionnalités WCF est disponible dans une application du Windows Store. Pour plus d'informations, consultez les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="1071d-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1071d-108">Utilisez les API de syndication WinRT au lieu de celles exposées par WCF.</span><span class="sxs-lookup"><span data-stu-id="1071d-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="1071d-109">Pour plus d’informations, consultez [API de syndication WinRT](xref:Windows.Web.Syndication)</span><span class="sxs-lookup"><span data-stu-id="1071d-109">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1071d-110">L'utilisation de la fonctionnalité Ajouter une référence de service pour ajouter une référence de service Web à un composant d'exécution Windows n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1071d-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="1071d-111">Liaisons prises en charge</span><span class="sxs-lookup"><span data-stu-id="1071d-111">Supported Bindings</span></span>  
 <span data-ttu-id="1071d-112">Les liaisons WCF suivantes sont prises en charge dans les applications du Windows Store :</span><span class="sxs-lookup"><span data-stu-id="1071d-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="1071d-113">Les éléments de liaison suivants sont pris en charge dans les applications du Windows Store :</span><span class="sxs-lookup"><span data-stu-id="1071d-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="1071d-114">Les encodages de texte et binaires sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1071d-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="1071d-115">Tous les modes de transfert WCF sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="1071d-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="1071d-116">Pour plus d’informations, consultez [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="1071d-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="1071d-117">Ajouter une référence de service</span><span class="sxs-lookup"><span data-stu-id="1071d-117">Add Service Reference</span></span>  
 <span data-ttu-id="1071d-118">Pour appeler un service WCF d'une application du Windows Store, utilisez la fonctionnalité Ajouter une référence de service de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="1071d-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="1071d-119">Vous remarquerez certaines modifications apportées à la fonctionnalité Ajouter une référence de service exécutée dans une application du Windows Store.</span><span class="sxs-lookup"><span data-stu-id="1071d-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="1071d-120">Tout d'abord, aucun fichier de configuration n'est généré.</span><span class="sxs-lookup"><span data-stu-id="1071d-120">First no configuration file is generated.</span></span> <span data-ttu-id="1071d-121">Les applications du Windows Store n'utilisent pas les fichiers de configuration, elles doivent être configurées dans le code.</span><span class="sxs-lookup"><span data-stu-id="1071d-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="1071d-122">Ce code de configuration se trouve dans le fichier References.cs généré par la fonctionnalité Ajouter une référence de service.</span><span class="sxs-lookup"><span data-stu-id="1071d-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="1071d-123">Pour voir ce fichier, assurez-vous de sélectionner "Afficher tous les fichiers" dans l’explorateur de la solution.</span><span class="sxs-lookup"><span data-stu-id="1071d-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="1071d-124">Le fichier se trouve sous les nœuds Références de service et Reference.svcmap dans le projet.</span><span class="sxs-lookup"><span data-stu-id="1071d-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="1071d-125">Toutes les opérations générées pour les services WCF dans une application du Windows Store seront des opérations asynchrones à l'aide du modèle asynchrone basé sur des tâches.</span><span class="sxs-lookup"><span data-stu-id="1071d-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="1071d-126">Pour plus d’informations, voir [Async Tasks - Simplify Asynchrone Programming with Tasks](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span><span class="sxs-lookup"><span data-stu-id="1071d-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="1071d-127">Comme la configuration est maintenant générée dans le code, toutes les modifications effectuées dans le fichier Reference.cs sont remplacées à chaque mise à jour de la référence de service.</span><span class="sxs-lookup"><span data-stu-id="1071d-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="1071d-128">Pour remédier à cette situation, le code de configuration est généré dans une méthode partielle, que vous pouvez implémenter dans votre classe proxy client.</span><span class="sxs-lookup"><span data-stu-id="1071d-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="1071d-129">La méthode partielle est déclarée comme suit :</span><span class="sxs-lookup"><span data-stu-id="1071d-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="1071d-130">Vous pouvez ensuite appliquer cette méthode partielle et modifier la liaison ou le point de terminaison dans votre classe proxy client comme suit :</span><span class="sxs-lookup"><span data-stu-id="1071d-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
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
  
### <a name="serialization"></a><span data-ttu-id="1071d-131">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="1071d-131">Serialization</span></span>  
 <span data-ttu-id="1071d-132">Les sérialiseurs suivants sont pris en charge dans les applications du Windows Store :</span><span class="sxs-lookup"><span data-stu-id="1071d-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="1071d-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="1071d-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="1071d-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="1071d-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="1071d-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="1071d-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1071d-136">XmlDictionaryWriter.Write(DateTime) écrit maintenant l'objet DateTime en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="1071d-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="1071d-137">Sécurité</span><span class="sxs-lookup"><span data-stu-id="1071d-137">Security</span></span>  

<span data-ttu-id="1071d-138">Les modes de sécurité suivants sont pris en charge dans les applications Windows Store :</span><span class="sxs-lookup"><span data-stu-id="1071d-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="1071d-139">Les types d’identification des clients suivants sont pris en charge dans les applications Windows Store :</span><span class="sxs-lookup"><span data-stu-id="1071d-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="1071d-140">None</span><span class="sxs-lookup"><span data-stu-id="1071d-140">None</span></span>  
  
2. <span data-ttu-id="1071d-141">De base</span><span class="sxs-lookup"><span data-stu-id="1071d-141">Basic</span></span>  
  
3. <span data-ttu-id="1071d-142">Digest</span><span class="sxs-lookup"><span data-stu-id="1071d-142">Digest</span></span>  
  
4. <span data-ttu-id="1071d-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="1071d-143">Negotiate</span></span>  
  
5. <span data-ttu-id="1071d-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="1071d-144">NTLM</span></span>  
  
6. <span data-ttu-id="1071d-145"> Windows</span><span class="sxs-lookup"><span data-stu-id="1071d-145">Windows</span></span>  
  
7. <span data-ttu-id="1071d-146">Nom d'utilisateur (sécurité du message)</span><span class="sxs-lookup"><span data-stu-id="1071d-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="1071d-147">Windows (sécurité du transport)</span><span class="sxs-lookup"><span data-stu-id="1071d-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="1071d-148">Pour que les applications du Windows Store accèdent aux informations d'identification Windows par défaut et les envoient, vous devez activer cette fonctionnalité dans le fichier Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="1071d-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="1071d-149">Ouvrez ce fichier et sélectionnez l’onglet Capacités et sélectionnez les « Informations d’identification Windows par défaut ».</span><span class="sxs-lookup"><span data-stu-id="1071d-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="1071d-150">Cela permet à l'application de se connecter aux ressources intranet qui nécessitent des informations d'identification de domaine.</span><span class="sxs-lookup"><span data-stu-id="1071d-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1071d-151">Pour que les applications Windows Store effectuent des appels inter machines, vous devez activer une autre capacité appelée « Réseautage à domicile/travail ».</span><span class="sxs-lookup"><span data-stu-id="1071d-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="1071d-152">Ce paramètre est également dans le fichier Package.appmanifest sous l’onglet Capacités. Sélectionnez la case à cocher Home/Work Networking.</span><span class="sxs-lookup"><span data-stu-id="1071d-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="1071d-153">Cela donne à votre application un accès entrant et sortant au réseau des lieux approuvés par l'utilisateur, tels que le domicile et le bureau.</span><span class="sxs-lookup"><span data-stu-id="1071d-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="1071d-154">Les ports entrants critiques sont toujours bloqués.</span><span class="sxs-lookup"><span data-stu-id="1071d-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="1071d-155">Pour accéder aux services sur Internet, vous devez également activer la fonction Internet (client).</span><span class="sxs-lookup"><span data-stu-id="1071d-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="1071d-156">Divers</span><span class="sxs-lookup"><span data-stu-id="1071d-156">Misc</span></span>  
 <span data-ttu-id="1071d-157">L'utilisation des classes suivantes est prise en charge pour les applications du Windows Store :</span><span class="sxs-lookup"><span data-stu-id="1071d-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="1071d-158">Définition des contrats de service</span><span class="sxs-lookup"><span data-stu-id="1071d-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="1071d-159">Nous vous recommandons de définir les opérations de service asynchrones uniquement à l'aide du modèle asynchrone basé sur des tâches.</span><span class="sxs-lookup"><span data-stu-id="1071d-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="1071d-160">Cela garantit que les applications du Windows Store restent réactives lors de l'appel d'une opération de service.</span><span class="sxs-lookup"><span data-stu-id="1071d-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1071d-161">Même si aucune exception n'est levée si vous définissez une opération synchrone, il est vivement recommandé de définir uniquement des opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="1071d-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="1071d-162">Appels de services WCF des applications du Windows Store</span><span class="sxs-lookup"><span data-stu-id="1071d-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="1071d-163">Comme mentionné précédemment, toute la configuration doit être effectuée dans le code de la méthode GetBindingForEndpoint de la classe proxy générée.</span><span class="sxs-lookup"><span data-stu-id="1071d-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="1071d-164">L'appel d'une opération de service est identique à l'appel d'une méthode asynchrone basée sur des tâches comme indiqué dans l'extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="1071d-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="1071d-165">Notez l'utilisation du mot clé async dans la méthode qui effectue l'appel asynchrone et du mot clé await lors de l'appel de la méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="1071d-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1071d-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1071d-166">See also</span></span>

- [<span data-ttu-id="1071d-167">WCF dans les applications du Windows Store (blog)</span><span class="sxs-lookup"><span data-stu-id="1071d-167">WCF in Windows Store Apps Blog</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [<span data-ttu-id="1071d-168">WCF, clients du Windows Store et sécurité</span><span class="sxs-lookup"><span data-stu-id="1071d-168">WCF Windows Store Clients and Security</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [<span data-ttu-id="1071d-169">Applications du Windows Store et appels entre ordinateurs</span><span class="sxs-lookup"><span data-stu-id="1071d-169">Windows Store Apps and Cross Machine Calls</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="1071d-170">Appel d’un service WCF déployé dans Azure à partir d’une application du Windows Store</span><span class="sxs-lookup"><span data-stu-id="1071d-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="1071d-171">Programmation de la sécurité dans WCF</span><span class="sxs-lookup"><span data-stu-id="1071d-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="1071d-172">Liaisons</span><span class="sxs-lookup"><span data-stu-id="1071d-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
