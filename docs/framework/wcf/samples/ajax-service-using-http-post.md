---
title: AJAX Service Using HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c5e5de34573fbfc8a5c6e9607d10881941a9bed5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972020"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="ab611-102">AJAX Service Using HTTP POST</span><span class="sxs-lookup"><span data-stu-id="ab611-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="ab611-103">Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service JavaScript et XML (AJAX) asynchrone ASP.NET qui utilise HTTP.</span><span class="sxs-lookup"><span data-stu-id="ab611-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="ab611-104">Un service AJAX est un service auquel vous pouvez accéder à l'aide du code Javascript de base d'un client de navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="ab611-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="ab611-105">Cet exemple s’appuie sur l’exemple [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) . la seule différence entre les deux exemples est l’utilisation de HTTP POSTCONNEXION au lieu de HTTP.</span><span class="sxs-lookup"><span data-stu-id="ab611-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="ab611-106">La prise en charge d’Ajax dans Windows Communication Foundation (WCF) est optimisée pour une `ScriptManager` utilisation avec ASP.NET AJAX par le biais du contrôle.</span><span class="sxs-lookup"><span data-stu-id="ab611-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="ab611-107">Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez les [exemples Ajax](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="ab611-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ab611-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="ab611-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="ab611-109">Dans l’exemple suivant, le service est un service WCF sans code spécifique à AJAX.</span><span class="sxs-lookup"><span data-stu-id="ab611-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="ab611-110">Si l' <xref:System.ServiceModel.Web.WebInvokeAttribute> attribut est appliqué à une opération, ou si <xref:System.ServiceModel.Web.WebGetAttribute> l’attribut n’est pas appliqué, le verbe http par défaut («poster») est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ab611-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="ab611-111">Les demandes POST sont plus difficiles à générer que les demandes GET, mais elles ne sont pas mises en cache ; utilisez des demandes POST pour toutes les opérations où la mise en cache n'est pas appropriée.</span><span class="sxs-lookup"><span data-stu-id="ab611-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="ab611-112">Créez un point de terminaison AJAX sur le service à l'aide de <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, comme dans l'exemple de servie AJAX de base.</span><span class="sxs-lookup"><span data-stu-id="ab611-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="ab611-113">Contrairement aux demandes GET, vous ne pouvez pas appeler des services POST depuis le navigateur.</span><span class="sxs-lookup"><span data-stu-id="ab611-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="ab611-114">Par exemple, la navigation vers `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` génère une erreur, car le service de publication s’attend à `n1` ce `n2` que les paramètres et soient envoyés dans le corps du message au format JSON, et non dans l’URL.</span><span class="sxs-lookup"><span data-stu-id="ab611-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="ab611-115">La page web PostAjaxClientPage.aspx du client contient le code ASP.NET pour appeler le service toutes les fois que l’utilisateur clique sur l’un des boutons d’opération de la page.</span><span class="sxs-lookup"><span data-stu-id="ab611-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="ab611-116">Le service répond de la même façon que dans l’exemple de [service Ajax de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) , avec la requête d’extraction.</span><span class="sxs-lookup"><span data-stu-id="ab611-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ab611-117">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ab611-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ab611-118">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ab611-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ab611-119">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="ab611-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ab611-120">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ab611-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ab611-121">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="ab611-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="ab611-122">Veillez à suivre les instructions d’installation [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab611-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ab611-123">Générez la solution PostAjaxService. sln comme décrit dans [génération des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ab611-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="ab611-124">Accédez à `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (n’ouvrez pas PostAjaxClientPage. aspx dans le navigateur à partir du répertoire du projet).</span><span class="sxs-lookup"><span data-stu-id="ab611-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
