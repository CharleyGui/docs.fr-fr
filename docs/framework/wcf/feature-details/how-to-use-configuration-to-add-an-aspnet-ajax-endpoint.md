---
title: 'Procédure : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: b229173381eed3e821a9ad9e1a6639912521731c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268428"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="ef3af-102">Procédure : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ef3af-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>

<span data-ttu-id="ef3af-103">Windows Communication Foundation (WCF) vous permet de créer un service qui rend disponible un point de terminaison compatible AJAX ASP.NET pouvant être appelé à partir de JavaScript sur un site Web client.</span><span class="sxs-lookup"><span data-stu-id="ef3af-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="ef3af-104">Pour créer un tel point de terminaison, vous pouvez utiliser un fichier de configuration, comme avec tous les autres points de terminaison Windows Communication Foundation (WCF), ou utiliser une méthode qui ne requiert aucun élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="ef3af-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="ef3af-105">Cette rubrique décrit l'approche utilisant le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ef3af-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="ef3af-106">La partie de la procédure qui permet au point de terminaison de service de devenir ASP.NET AJAX consiste à configurer le point de terminaison pour utiliser <xref:System.ServiceModel.WebHttpBinding> et pour ajouter le [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="ef3af-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="ef3af-107">Après la configuration du point de terminaison, les étapes pour implémenter et héberger le service sont similaires à celles utilisées par n’importe quel service WCF.</span><span class="sxs-lookup"><span data-stu-id="ef3af-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="ef3af-108">Pour obtenir un exemple fonctionnel, consultez le [service Ajax à l’aide de http postal](../samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="ef3af-108">For a working example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="ef3af-109">Pour plus d’informations sur la configuration d’un point de terminaison AJAX ASP.NET sans utiliser la configuration, consultez [Comment : ajouter un point de terminaison ASP.NET AJAX sans utiliser la configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="ef3af-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="ef3af-110">Pour créer un service WCF de base</span><span class="sxs-lookup"><span data-stu-id="ef3af-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="ef3af-111">Définissez un contrat de service WCF de base avec une interface marquée avec l' <xref:System.ServiceModel.ServiceContractAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="ef3af-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="ef3af-112">Marquez chaque opération avec <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ef3af-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="ef3af-113">Assurez-vous de définir la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef3af-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="ef3af-114">Implémentez le contrat de service `ICalculator` avec un `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="ef3af-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. <span data-ttu-id="ef3af-115">Définissez un espace de noms pour les implémentations `ICalculator` et `CalculatorService` en les encapsulant dans un bloc Namespace.</span><span class="sxs-lookup"><span data-stu-id="ef3af-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="ef3af-116">Pour créer un point de terminaison ASP.NET AJAX pour le service</span><span class="sxs-lookup"><span data-stu-id="ef3af-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="ef3af-117">Créez une configuration de comportement et spécifiez le [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) comportement des points de terminaison compatibles ASP.NET AJAX du service.</span><span class="sxs-lookup"><span data-stu-id="ef3af-117">Create a behavior configuration and specify the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="ef3af-118">Créez un point de terminaison pour le service qui utilise <xref:System.ServiceModel.WebHttpBinding> et le comportement ASP.NET AJAX défini dans l'étape précédente.</span><span class="sxs-lookup"><span data-stu-id="ef3af-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>
    ```  
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="ef3af-119">Pour héberger le service dans IIS</span><span class="sxs-lookup"><span data-stu-id="ef3af-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="ef3af-120">Pour héberger le service dans IIS, créez un nouveau fichier nommé "Service" avec une extension .svc dans l’application.</span><span class="sxs-lookup"><span data-stu-id="ef3af-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="ef3af-121">Modifiez ce fichier en ajoutant les informations de directive [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) appropriées pour le service.</span><span class="sxs-lookup"><span data-stu-id="ef3af-121">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="ef3af-122">Le contenu du fichier Service pour l'exemple `CalculatorService` contient les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ef3af-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```aspx-csharp
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="ef3af-123">Pour plus d’informations sur l’hébergement dans IIS, consultez [Comment : héberger un service WCF dans IIS](how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="ef3af-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="ef3af-124">Pour appeler le service</span><span class="sxs-lookup"><span data-stu-id="ef3af-124">To call the service</span></span>  
  
1. <span data-ttu-id="ef3af-125">Le point de terminaison est configuré à une adresse vide relative au fichier. svc. par conséquent, le service est maintenant disponible et peut être appelé en envoyant des demandes à service. svc/ \<operation> -par exemple, service. svc/Add pour l' `Add` opération.</span><span class="sxs-lookup"><span data-stu-id="ef3af-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="ef3af-126">Vous pouvez l’utiliser en entrant le point l’URL du point de terminaison dans la collection Scripts du contrôle Script Manager ASP.NET AJAX .</span><span class="sxs-lookup"><span data-stu-id="ef3af-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="ef3af-127">Pour obtenir un exemple, consultez le [service Ajax à l’aide de http postal](../samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="ef3af-127">For an example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef3af-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef3af-128">See also</span></span>

- [<span data-ttu-id="ef3af-129">Création de services WCF pour ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="ef3af-129">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="ef3af-130">Procédure : migrer des services web ASP.NET compatibles AJAX vers WCF</span><span class="sxs-lookup"><span data-stu-id="ef3af-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
