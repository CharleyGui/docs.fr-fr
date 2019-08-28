---
title: 'Procédure : publier des métadonnées pour un service à l’aide d’un fichier de configuration'
ms.date: 03/30/2017
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
ms.openlocfilehash: 26894a3951b91879a7b3e6f66731891113394082
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045303"
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="f5975-102">Procédure : publier des métadonnées pour un service à l’aide d’un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="f5975-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="f5975-103">Il s’agit de l’une des deux rubriques de procédures qui illustrent la publication de métadonnées pour un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f5975-103">This is one of two how-to topics that demonstrate publishing metadata for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="f5975-104">Il y a deux façons de spécifier comment un service doit publier des métadonnées : à l'aide d'un fichier de configuration et à l'aide du code.</span><span class="sxs-lookup"><span data-stu-id="f5975-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="f5975-105">Cette rubrique montre comment publier des métadonnées pour un service à l'aide d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f5975-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f5975-106">Cette rubrique indique comment publier des métadonnées de manière non sécurisée.</span><span class="sxs-lookup"><span data-stu-id="f5975-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="f5975-107">Tout client peut récupérer les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="f5975-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="f5975-108">Si vous avez besoin que votre service publie des métadonnées de manière sécurisée, consultez [point de terminaison de métadonnées sécurisées personnalisées](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="f5975-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 <span data-ttu-id="f5975-109">Pour plus d’informations sur la publication de métadonnées [dans le code, consultez Procédure: Publier les métadonnées d’un service](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="f5975-109">For more information about publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="f5975-110">La publication des métadonnées permet aux clients de récupérer les métadonnées via une requête WS-Transfer GET ou une requête HTTP/GET à l'aide de la chaîne de requête `?wsdl`.</span><span class="sxs-lookup"><span data-stu-id="f5975-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="f5975-111">Pour être sûr que le code fonctionne, créez un service WCF de base.</span><span class="sxs-lookup"><span data-stu-id="f5975-111">To be sure that the code is working, create a basic WCF service.</span></span> <span data-ttu-id="f5975-112">Pour plus de simplicité, un service auto-hébergé de base est fourni dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="f5975-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f5975-113">Ce service est un service auto-hébergé, configuré à l'aide d'un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f5975-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="f5975-114">Le fichier de configuration suivant sert de point de départ.</span><span class="sxs-lookup"><span data-stu-id="f5975-114">The following configuration file serves as a starting point.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="f5975-115">Pour publier les métadonnées d'un service WCF à l'aide d'un fichier de configuration d'application</span><span class="sxs-lookup"><span data-stu-id="f5975-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1. <span data-ttu-id="f5975-116">Dans le fichier App.config, après la fermeture de l'élément `</services>`, créez un élément `<behaviors>`.</span><span class="sxs-lookup"><span data-stu-id="f5975-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  

2. <span data-ttu-id="f5975-117">Dans l'élément `<behaviors>`, ajoutez un nouvel élément `<serviceBehaviors>`.</span><span class="sxs-lookup"><span data-stu-id="f5975-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  

3. <span data-ttu-id="f5975-118">Ajoutez un élément `<behavior>` à l'élément `<serviceBehaviors>` et spécifiez une valeur pour l'attribut `name` de l'élément `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="f5975-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  

4. <span data-ttu-id="f5975-119">Ajoutez un élément `<serviceMetadata>` à l'élément `<behavior>`.</span><span class="sxs-lookup"><span data-stu-id="f5975-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="f5975-120">Affectez à l'attribut `httpGetEnabled` la valeur `true` et à l'attribut `policyVersion` la valeur Policy15.</span><span class="sxs-lookup"><span data-stu-id="f5975-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="f5975-121">`httpGetEnabled` permet au service de répondre aux demandes de métadonnées faites par une demande HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="f5975-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="f5975-122">`policyVersion` indique au service de se conformer à WS-Policy 1.5 lors de la génération des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f5975-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  

5. <span data-ttu-id="f5975-123">Ajoutez un attribut `behaviorConfiguration` à l'élément `<service>` et spécifiez l'attribut `name` de l'élément `<behavior>` ajouté à l'étape 1, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f5975-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6. <span data-ttu-id="f5975-124">Ajoutez un ou plusieurs éléments `<endpoint>` et attribuez au contrat la valeur `IMetadataExchange`, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f5975-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7. <span data-ttu-id="f5975-125">Pour les points de terminaison de métadonnées ajoutés à l'étape précédente, affectez à l'attribut `binding` l'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5975-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    - <span data-ttu-id="f5975-126">`mexHttpBinding` pour la publication HTTP.</span><span class="sxs-lookup"><span data-stu-id="f5975-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    - <span data-ttu-id="f5975-127">`mexHttpsBinding` pour la publication HTTPS.</span><span class="sxs-lookup"><span data-stu-id="f5975-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    - <span data-ttu-id="f5975-128">`mexNamedPipeBinding` pour la publication de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="f5975-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    - <span data-ttu-id="f5975-129">`mexTcpBinding` pour la publication TCP.</span><span class="sxs-lookup"><span data-stu-id="f5975-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8. <span data-ttu-id="f5975-130">Pour les points de terminaison de métadonnées ajoutés à l'étape précédente, attribuez à l'adresse la valeur suivante :</span><span class="sxs-lookup"><span data-stu-id="f5975-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    - <span data-ttu-id="f5975-131">Une chaîne vide pour utiliser l’adresse de base de l’application hôte comme point de publication si l’adresse de base est la même que la liaison de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f5975-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    - <span data-ttu-id="f5975-132">Une adresse relative si l'application hôte a une adresse de base.</span><span class="sxs-lookup"><span data-stu-id="f5975-132">A relative address if the host application has a base address.</span></span>  
  
    - <span data-ttu-id="f5975-133">Une adresse absolue.</span><span class="sxs-lookup"><span data-stu-id="f5975-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="f5975-134">Créez et exécutez l'application console.</span><span class="sxs-lookup"><span data-stu-id="f5975-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="f5975-135">Utilisez Internet Explorer pour accéder à l’adresse de base du service (http://localhost:8001/MetadataSample dans cet exemple) et vérifiez que la publication des métadonnées est activée.</span><span class="sxs-lookup"><span data-stu-id="f5975-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="f5975-136">Si ce n’est pas le cas, un message en haut de la page qui s’affiche: «La publication des métadonnées pour ce service est actuellement désactivée».</span><span class="sxs-lookup"><span data-stu-id="f5975-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="f5975-137">Pour utiliser les points de terminaison par défaut</span><span class="sxs-lookup"><span data-stu-id="f5975-137">To use default endpoints</span></span>  
  
1. <span data-ttu-id="f5975-138">Pour configurer des métadonnées sur un service qui utilise les points de terminaison par défaut, spécifiez <xref:System.ServiceModel.Description.ServiceMetadataBehavior> dans le fichier de configuration, comme dans l'exemple précédent, mais ne spécifiez aucun point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f5975-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="f5975-139">Le fichier de configuration se présenterait alors comme suit.</span><span class="sxs-lookup"><span data-stu-id="f5975-139">The configuration file would then look like this.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="f5975-140">Étant donné que le service a un <xref:System.ServiceModel.Description.ServiceMetadataBehavior> avec le `httpGetEnabled` ayant la valeur `true`, la publication des métadonnées est activée pour le service, et comme aucun point de terminaison n'a été ajouté explicitement, le runtime ajoute les points de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="f5975-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> <span data-ttu-id="f5975-141">Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](../../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour les services WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f5975-141">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5975-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="f5975-142">Example</span></span>  
 <span data-ttu-id="f5975-143">L’exemple de code suivant montre l’implémentation d’un service WCF de base et le fichier de configuration qui publie des métadonnées pour le service.</span><span class="sxs-lookup"><span data-stu-id="f5975-143">The following code example shows the implementation of a basic WCF service and the configuration file that publishes metadata for the service.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5975-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5975-144">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="f5975-145">Guide pratique pour Héberger un service WCF dans une application managée</span><span class="sxs-lookup"><span data-stu-id="f5975-145">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="f5975-146">Auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="f5975-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="f5975-147">Vue d’ensemble de l’architecture de métadonnées</span><span class="sxs-lookup"><span data-stu-id="f5975-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
- [<span data-ttu-id="f5975-148">Utilisation des métadonnées</span><span class="sxs-lookup"><span data-stu-id="f5975-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [<span data-ttu-id="f5975-149">Guide pratique : Publier les métadonnées d’un service à l’aide de code</span><span class="sxs-lookup"><span data-stu-id="f5975-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
