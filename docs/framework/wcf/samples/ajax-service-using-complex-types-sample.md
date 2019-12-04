---
title: AJAX Service Using Complex Types, exemple
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: be8db36be7ed1639d839113174fdb95505466534
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716234"
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="51da6-102">AJAX Service Using Complex Types, exemple</span><span class="sxs-lookup"><span data-stu-id="51da6-102">AJAX Service Using Complex Types Sample</span></span>

<span data-ttu-id="51da6-103">Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service AJAX (JavaScript et XML) asynchrone ASP.NET qui crée des instances de types complexes et les envoie entre le service et le client en tant que JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="51da6-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="51da6-104">Vous pouvez accéder à un service AJAX en utilisant le code JavaScript à partir d'un client de navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="51da6-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="51da6-105">Cet exemple s’appuie sur l’exemple de [service Ajax de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="51da6-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="51da6-106">La prise en charge d’AJAX dans WCF est optimisée pour une utilisation avec ASP.NET AJAX par le biais du contrôle <xref:System.Web.UI.ScriptManager>.</span><span class="sxs-lookup"><span data-stu-id="51da6-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="51da6-107">Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez les [exemples Ajax](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="51da6-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="51da6-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="51da6-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="51da6-109">Dans l’exemple suivant, le service est un service WCF sans code spécifique à AJAX.</span><span class="sxs-lookup"><span data-stu-id="51da6-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="51da6-110">L'attribut <xref:System.ServiceModel.Web.WebGetAttribute> n'étant pas appliqué, le verbe HTTP par défaut ("POST") est utilisé.</span><span class="sxs-lookup"><span data-stu-id="51da6-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="51da6-111">Le service a une opération appelée `DoMath` qui retourne un type complexe appelé `MathResult`.</span><span class="sxs-lookup"><span data-stu-id="51da6-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="51da6-112">Le type complexe est un type de contrat de données standard qui ne contient pas non plus de code spécifique à AJAX.</span><span class="sxs-lookup"><span data-stu-id="51da6-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>

```csharp
[DataContract]
public class MathResult
{
    [DataMember]
    public double sum;
    [DataMember]
    public double difference;
    [DataMember]
    public double product;
    [DataMember]
    public double quotient;
}
```

<span data-ttu-id="51da6-113">Créez un point de terminaison AJAX sur le service à l'aide de <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, comme dans l'exemple de servie AJAX de base.</span><span class="sxs-lookup"><span data-stu-id="51da6-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="51da6-114">La page Web client ComplexTypeClientPage. aspx contient du code ASP.NET et JavaScript pour appeler le service quand l’utilisateur clique sur le bouton **effectuer un calcul** sur la page.</span><span class="sxs-lookup"><span data-stu-id="51da6-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="51da6-115">Le code permettant d’appeler le service construit un corps JSON et l’envoie à l’aide de HTTP HTTP, de la même façon que le [service Ajax à l’aide](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) de l’exemple http après.</span><span class="sxs-lookup"><span data-stu-id="51da6-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>

<span data-ttu-id="51da6-116">Une fois l'appel de service réussi, vous pouvez accéder aux membres de données individuels (`sum`, `difference`, `product` et `quotient`) sur l'objet JavaScript résultant.</span><span class="sxs-lookup"><span data-stu-id="51da6-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="51da6-117">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="51da6-117">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="51da6-118">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51da6-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="51da6-119">Générez la solution ComplexTypeAjaxService. sln comme décrit dans [génération des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="51da6-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="51da6-120">Accédez à `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (n’ouvrez pas ComplexTypeClientPage. aspx dans le navigateur à partir du répertoire du projet).</span><span class="sxs-lookup"><span data-stu-id="51da6-120">Navigate to `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51da6-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="51da6-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="51da6-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="51da6-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="51da6-123">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51da6-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="51da6-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="51da6-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a><span data-ttu-id="51da6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51da6-125">See also</span></span>

- [<span data-ttu-id="51da6-126">Service AJAX de base</span><span class="sxs-lookup"><span data-stu-id="51da6-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
