---
title: 'Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185137"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="d51de-102">Comment : ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration</span><span class="sxs-lookup"><span data-stu-id="d51de-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="d51de-103">Windows Communication Foundation (WCF) vous permet de créer un service qui expose un ASP.NET point de terminaison COMPATIBLE AJAX qui peut être appelé à partir de JavaScript sur un site Web client.</span><span class="sxs-lookup"><span data-stu-id="d51de-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="d51de-104">Pour créer ce point de terminaison, vous pouvez utiliser un fichier de configuration, comme pour tous les autres points de terminaison WCF, ou utiliser une méthode qui ne requiert aucun élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="d51de-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="d51de-105">Cette rubrique décrit la deuxième approche.</span><span class="sxs-lookup"><span data-stu-id="d51de-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="d51de-106">Pour créer des services avec les points de terminaison ASP.NET AJAX sans configuration, les services doivent être hébergés par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="d51de-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="d51de-107">Pour activer un ASP.NET point de terminaison <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> AJAX à l’aide de cette approche, spécifiez le paramètre Factory dans la [ \@directive ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dans le fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="d51de-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="d51de-108">Cette fabrication personnalisée est le composant qui configure automatiquement un point de terminaison ASP.NET AJAX afin qu’il puisse être appelé à partir de JavaScript sur un site web client.</span><span class="sxs-lookup"><span data-stu-id="d51de-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="d51de-109">Pour un exemple de travail, voir le [service AJAX Sans configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d51de-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="d51de-110">Pour un aperçu de la façon de configurer un point de terminaison AJAX ASP.NET à l’aide d’éléments de configuration, voir [Comment : Utilisez configuration pour ajouter un point de terminaison AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="d51de-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="d51de-111">Pour créer un service WCF de base</span><span class="sxs-lookup"><span data-stu-id="d51de-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="d51de-112">Définissez un contrat de service WCF <xref:System.ServiceModel.ServiceContractAttribute> de base avec une interface marquée avec l’attribut.</span><span class="sxs-lookup"><span data-stu-id="d51de-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="d51de-113">Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d51de-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="d51de-114">Assurez-vous de définir la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="d51de-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="d51de-115">Implémentez le contrat de service `ICalculator` avec un `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="d51de-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="d51de-116">Définissez un espace de noms pour les implémentations `ICalculator` et `CalculatorService` en les encapsulant dans un bloc Namespace.</span><span class="sxs-lookup"><span data-stu-id="d51de-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="d51de-117">Pour héberger le service dans les services IIS sans configuration</span><span class="sxs-lookup"><span data-stu-id="d51de-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="d51de-118">Créez un nouveau fichier pour le service avec une extension .svc dans l'application.</span><span class="sxs-lookup"><span data-stu-id="d51de-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="d51de-119">Modifier ce fichier en ajoutant les informations de directive [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) appropriées pour le service.</span><span class="sxs-lookup"><span data-stu-id="d51de-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="d51de-120">Spécifiez que la <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> directive [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) doit être utilisée pour configurer automatiquement un ASP.NET point de terminaison AJAX.</span><span class="sxs-lookup"><span data-stu-id="d51de-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="d51de-121">Générez le service et appelez-le à partir du client.</span><span class="sxs-lookup"><span data-stu-id="d51de-121">Build the service and call it from the client.</span></span> <span data-ttu-id="d51de-122">Les services IIS (Internet Information Services) activent le service lorsqu'il est appelé.</span><span class="sxs-lookup"><span data-stu-id="d51de-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="d51de-123">Pour plus d’informations sur l’hébergement dans l’IIS, voir [Comment: Organiser un service WCF dans IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="d51de-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="d51de-124">Pour appeler le service</span><span class="sxs-lookup"><span data-stu-id="d51de-124">To call the service</span></span>  
  
1. <span data-ttu-id="d51de-125">Le point de terminaison est configuré à une adresse vide par rapport au fichier .svc, de\<sorte que le service est maintenant disponible et `Add` peut être invoqué en envoyant des demandes à service.svc/ opération> - par exemple, service.svc/Add pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="d51de-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="d51de-126">Vous pouvez l'utiliser en entrant l'URL du service dans la collection Scripts du contrôle Script Manager ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="d51de-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="d51de-127">Par exemple, voir le [service AJAX Sans configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d51de-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d51de-128"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d51de-128">Example</span></span>  
  
 <span data-ttu-id="d51de-129">Le point de terminaison configuré automatiquement est créé au niveau d'une adresse vide qui est fonction de l'URL de base.</span><span class="sxs-lookup"><span data-stu-id="d51de-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="d51de-130">Un fichier de configuration peut également être ajouté et utilisé avec cette approche.</span><span class="sxs-lookup"><span data-stu-id="d51de-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="d51de-131">Si le fichier de configuration contient des définitions de point de terminaison, ces points de terminaison sont ajoutés au point de terminaison configuré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d51de-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="d51de-132">Par exemple, service.svc utilise <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> et le répertoire du service contient un fichier Web.config qui définit un point de terminaison pour le même service en utilisant <xref:System.ServiceModel.BasicHttpBinding> au niveau de l'adresse relative « soap ».</span><span class="sxs-lookup"><span data-stu-id="d51de-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="d51de-133">Dans ce cas, le service contient deux points de terminaison : un au niveau de service.svc (qui répond aux demandes ASP.NET AJAX) et un autre au niveau de service.svc/soap (qui répond aux demandes SOAP).</span><span class="sxs-lookup"><span data-stu-id="d51de-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="d51de-134">Si le fichier de configuration définit un point de terminaison au niveau d'une adresse relative vide et <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est utilisé, une exception est levée et le service ne peut pas démarrer.</span><span class="sxs-lookup"><span data-stu-id="d51de-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="d51de-135">Vous ne pouvez pas utiliser de configuration pour modifier des paramètres sur le point de terminaison configuré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d51de-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="d51de-136">Si un paramètre (tel qu'un quota de lecteur) doit être modifié, vous ne devez pas utiliser l'approche sans configuration en supprimant <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> dans le fichier .svc et en créant une entrée de configuration pour le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d51de-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="d51de-137">Si votre service requiert le mode de compatibilité ASP.NET, par exemple, s'il utilise la classe <xref:System.Web.HttpContext> ou les mécanismes d'autorisation ASP.NET, un fichier de configuration est néanmoins requis pour activer ce mode.</span><span class="sxs-lookup"><span data-stu-id="d51de-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="d51de-138">L’élément de configuration requis est le [ \<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) élément, qui doit être ajouté comme suit.</span><span class="sxs-lookup"><span data-stu-id="d51de-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="d51de-139">Pour plus d’informations, consultez le sujet des services et ASP.NET de [la WCF.](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)</span><span class="sxs-lookup"><span data-stu-id="d51de-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="d51de-140">La classe <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> est dérivée de la classe <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="d51de-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="d51de-141">Pour une explication détaillée du mécanisme de l’usine d’accueil de service, voir le thème [d’hébergement d’extension utilisant ServiceHostFactory.](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)</span><span class="sxs-lookup"><span data-stu-id="d51de-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d51de-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d51de-142">See also</span></span>

- [<span data-ttu-id="d51de-143">Création de services WCF pour ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="d51de-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="d51de-144">Comment : migrer des services Web ASP.NET compatibles AJAX vers WCF</span><span class="sxs-lookup"><span data-stu-id="d51de-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
