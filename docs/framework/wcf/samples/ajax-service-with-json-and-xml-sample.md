---
title: AJAX Service with JSON and XML, exemple
ms.date: 03/30/2017
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
ms.openlocfilehash: 8f70b6aa2e61d01a075a6edb3fe490ef593e73b0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575951"
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="016ac-102">AJAX Service with JSON and XML, exemple</span><span class="sxs-lookup"><span data-stu-id="016ac-102">AJAX Service with JSON and XML Sample</span></span>

<span data-ttu-id="016ac-103">Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service JavaScript et XML (AJAX) asynchrone qui retourne des données JavaScript Object Notation (JSON) ou XML.</span><span class="sxs-lookup"><span data-stu-id="016ac-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="016ac-104">Vous pouvez accéder à un service AJAX en utilisant le code JavaScript à partir d'un client de navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="016ac-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="016ac-105">Cet exemple s’appuie sur l’exemple de [service Ajax de base](basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="016ac-105">This sample builds on the [Basic AJAX Service](basic-ajax-service.md) sample.</span></span>

<span data-ttu-id="016ac-106">Contrairement aux autres exemples AJAX, celui-ci n'utilise pas ASP.NET AJAX et le contrôle <xref:System.Web.UI.ScriptManager>.</span><span class="sxs-lookup"><span data-stu-id="016ac-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="016ac-107">Avec une configuration supplémentaire, les services WCF AJAX sont accessibles à partir de n’importe quelle page HTML via JavaScript, et ce scénario est illustré ici.</span><span class="sxs-lookup"><span data-stu-id="016ac-107">With some additional configuration, WCF AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="016ac-108">Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez [exemples Ajax](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="016ac-108">For an example of using WCF with ASP.NET AJAX, see [AJAX Samples](ajax.md).</span></span>

<span data-ttu-id="016ac-109">Cet exemple illustre comment commuter le type de réponse d'une opération entre JSON et XML.</span><span class="sxs-lookup"><span data-stu-id="016ac-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="016ac-110">Cette fonctionnalité est disponible que le service soit configuré pour être accessible par ASP.NET AJAX ou par une page cliente HTML/JavaScript.</span><span class="sxs-lookup"><span data-stu-id="016ac-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>

> [!NOTE]
> <span data-ttu-id="016ac-111">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="016ac-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="016ac-112">Pour permettre l'utilisation de clients AJAX non-ASP.NET, utilisez <xref:System.ServiceModel.Activation.WebServiceHostFactory> (pas <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) dans le fichier .svc.</span><span class="sxs-lookup"><span data-stu-id="016ac-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="016ac-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> ajoute un point de terminaison standard <xref:System.ServiceModel.Description.WebHttpEndpoint> au service.</span><span class="sxs-lookup"><span data-stu-id="016ac-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="016ac-114">Le point de terminaison est configuré à une adresse vide relative au fichier. svc ; Cela signifie que l’adresse du service est `http://localhost/ServiceModelSamples/service.svc` , sans suffixe supplémentaire autre que le nom de l’opération.</span><span class="sxs-lookup"><span data-stu-id="016ac-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

<span data-ttu-id="016ac-115">La section suivante dans Web.config peut être utilisée pour apporter des modifications de configuration supplémentaires au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="016ac-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="016ac-116">Elle peut être supprimée si aucune modification supplémentaire n'est requise.</span><span class="sxs-lookup"><span data-stu-id="016ac-116">It can be removed if no extra changes are needed.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name="" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="016ac-117">Le format de données par défaut pour <xref:System.ServiceModel.Description.WebHttpEndpoint> est XML, tandis que le format de données par défaut pour <xref:System.ServiceModel.Description.WebScriptEndpoint> est JSON.</span><span class="sxs-lookup"><span data-stu-id="016ac-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="016ac-118">Pour plus d’informations, consultez [création de services WCF Ajax sans ASP.net](../feature-details/creating-wcf-ajax-services-without-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="016ac-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>

<span data-ttu-id="016ac-119">Dans l’exemple suivant, le service est un service WCF standard avec deux opérations.</span><span class="sxs-lookup"><span data-stu-id="016ac-119">The service in the following sample is a standard WCF service with two operations.</span></span> <span data-ttu-id="016ac-120">Ces deux opérations requièrent le style de corps <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> sur les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute>, ce qui est spécifique au comportement `webHttp` et n'a aucune incidence sur le commutateur de format de données JSON/XML.</span><span class="sxs-lookup"><span data-stu-id="016ac-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

<span data-ttu-id="016ac-121">Le format de réponse pour l’opération est spécifié en tant que XML, qui est le paramètre par défaut pour le [\<webHttp>](../../configure-apps/file-schema/wcf/webhttp.md) comportement.</span><span class="sxs-lookup"><span data-stu-id="016ac-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="016ac-122">Il est toutefois conseillé de spécifier explicitement le format de réponse.</span><span class="sxs-lookup"><span data-stu-id="016ac-122">However, it is good practice explicitly specify the response format.</span></span>

<span data-ttu-id="016ac-123">L'autre opération utilise l'attribut `WebInvokeAttribute` et spécifie explicitement JSON au lieu de XML pour la réponse.</span><span class="sxs-lookup"><span data-stu-id="016ac-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

<span data-ttu-id="016ac-124">Notez que dans les deux cas, les opérations retournent un type complexe, `MathResult` , qui est un type de contrat de données WCF standard.</span><span class="sxs-lookup"><span data-stu-id="016ac-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard WCF data contract type.</span></span>

<span data-ttu-id="016ac-125">La page Web client XmlAjaxClientPage. htm contient du code JavaScript qui appelle l’une des deux opérations précédentes quand l’utilisateur clique sur les boutons **exécuter le calcul (retourner JSON)** ou **exécuter le calcul (retour XML)** sur la page.</span><span class="sxs-lookup"><span data-stu-id="016ac-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="016ac-126">Le code permettant d'appeler le service construit un corps JSON et l'envoie à l'aide de HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="016ac-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="016ac-127">La demande est créée manuellement dans JavaScript, contrairement à l’exemple de [service Ajax de base](basic-ajax-service.md) et aux autres exemples utilisant ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="016ac-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>

```csharp
// Create HTTP request
var xmlHttp;
// Request instantiation code omitted…
// Result handler code omitted…

// Build the operation URL
var url = "service.svc/ajaxEndpoint/";
url = url + operation;

// Build the body of the JSON message
var body = '{"n1":';
body = body + document.getElementById("num1").value + ',"n2":';
body = body + document.getElementById("num2").value + '}';

// Send the HTTP request
xmlHttp.open("POST", url, true);
xmlHttp.setRequestHeader("Content-type", "application/json");
xmlHttp.send(body);
```

<span data-ttu-id="016ac-128">La réponse du service s'affiche sans traitement supplémentaire dans une zone de texte de la page.</span><span class="sxs-lookup"><span data-stu-id="016ac-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="016ac-129">Cet exemple est implémenté à des fins de démonstration pour vous permettre d'observer directement les formats de données XML et JSON utilisés.</span><span class="sxs-lookup"><span data-stu-id="016ac-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> <span data-ttu-id="016ac-130">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="016ac-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="016ac-131">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="016ac-131">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="016ac-132">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="016ac-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="016ac-133">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="016ac-133">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="016ac-134">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="016ac-134">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="016ac-135">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="016ac-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="016ac-136">Générez la solution XmlAjaxService. sln comme décrit dans [génération des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="016ac-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="016ac-137">Accédez à `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (n’ouvrez pas XmlAjaxClientPage. htm dans le navigateur à partir du répertoire du projet).</span><span class="sxs-lookup"><span data-stu-id="016ac-137">Navigate to `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>

## <a name="see-also"></a><span data-ttu-id="016ac-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="016ac-138">See also</span></span>

- [<span data-ttu-id="016ac-139">AJAX Service Using HTTP POST</span><span class="sxs-lookup"><span data-stu-id="016ac-139">AJAX Service Using HTTP POST</span></span>](ajax-service-using-http-post.md)
