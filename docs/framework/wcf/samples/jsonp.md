---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9e27d4e73f43f004ac1de078db6a73cd42b24bbc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237662"
---
# <a name="jsonp"></a><span data-ttu-id="dab94-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="dab94-102">JSONP</span></span>

<span data-ttu-id="dab94-103">Cet exemple montre comment prendre en charge JSON with Padding (JSONP) dans les services WCF REST.</span><span class="sxs-lookup"><span data-stu-id="dab94-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="dab94-104">JSONP est une convention servant à appeler des scripts entre domaines en générant des balises de script dans le document actif.</span><span class="sxs-lookup"><span data-stu-id="dab94-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="dab94-105">Le résultat est retourné dans une fonction de rappel spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dab94-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="dab94-106">JSONP repose sur l’idée que des balises telles que `<script src="http://..." >` peuvent évaluer des scripts de n’importe quel domaine et que le script récupéré par ces balises est évalué dans une étendue dans laquelle d’autres fonctions peuvent déjà être définies.</span><span class="sxs-lookup"><span data-stu-id="dab94-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="dab94-107">Illustre le</span><span class="sxs-lookup"><span data-stu-id="dab94-107">Demonstrates</span></span>

 <span data-ttu-id="dab94-108">Script entre domaines avec JSONP.</span><span class="sxs-lookup"><span data-stu-id="dab94-108">Cross-domain scripting with JSONP.</span></span>

## <a name="discussion"></a><span data-ttu-id="dab94-109">Discussions</span><span class="sxs-lookup"><span data-stu-id="dab94-109">Discussion</span></span>

 <span data-ttu-id="dab94-110">L'exemple inclut une page Web qui ajoute dynamiquement un bloc de script après que la page a été rendue dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="dab94-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="dab94-111">Ce bloc de script appelle un service WCF REST qui a une seule opération, `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="dab94-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="dab94-112">Le service WCF REST retourne le nom et l'adresse d'un client encapsulés dans un nom de fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="dab94-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="dab94-113">Lorsque le service WCF REST répond, la fonction de rappel de la page web est appelée avec les données client et la fonction de rappel affiche les données dans la page web.</span><span class="sxs-lookup"><span data-stu-id="dab94-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="dab94-114">L'injection de la balise de script et l'exécution de la fonction de rappel sont gérées automatiquement par le contrôle ASP.NET AJAX ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="dab94-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="dab94-115">Le modèle d’utilisation est le même qu’avec tous les proxys ASP.NET AJAX, mais comprend une ligne supplémentaire pour activer JSONP, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="dab94-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>

```csharp
var proxy = new JsonpAjaxService.CustomerService();
proxy.set_enableJsonp(true);
proxy.GetCustomer(onSuccess, onFail, null);
```

 <span data-ttu-id="dab94-116">La page web peut appeler le service WCF REST, car le service utilise le <xref:System.ServiceModel.Description.WebScriptEndpoint> avec `crossDomainScriptAccessEnabled` ayant la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="dab94-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="dab94-117">Ces deux configurations sont effectuées dans le fichier Web.config sous l' \<system.serviceModel> élément.</span><span class="sxs-lookup"><span data-stu-id="dab94-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>

```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

 <span data-ttu-id="dab94-118">ScriptManager gère l'interaction avec le service et cache la complexité de l'implémentation manuelle de l'accès JSONP.</span><span class="sxs-lookup"><span data-stu-id="dab94-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="dab94-119">Lorsque `crossDomainScriptAccessEnabled` a la valeur `true` et que le format de la réponse d’une opération est JSON, l’infrastructure WCF inspecte l’URI de la demande pour un paramètre de chaîne de requête de rappel et encapsule la réponse JSON avec la valeur du paramètre de chaîne de requête de rappel.</span><span class="sxs-lookup"><span data-stu-id="dab94-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="dab94-120">Dans l'exemple, la page Web appelle le service WCF REST avec l'URI suivant.</span><span class="sxs-lookup"><span data-stu-id="dab94-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>

```http
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0
```

 <span data-ttu-id="dab94-121">Étant donné que le paramètre de chaîne de requête de rappel a la valeur `JsonPCallback`, le service WCF retourne une réponse JSONP représentée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dab94-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>

```json
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});
```

 <span data-ttu-id="dab94-122">Cette réponse JSONP inclut les données client mises au format JSON et encapsulées avec le nom de la fonction de rappel que la page web a demandée.</span><span class="sxs-lookup"><span data-stu-id="dab94-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="dab94-123">ScriptManager exécute ce rappel à l'aide d'une balise de script pour effectuer la demande entre domaines, puis passe le résultat au gestionnaire onSuccess qui a été passé à l'opération GetCustomer du proxy ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="dab94-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>

 <span data-ttu-id="dab94-124">L’exemple se compose de deux applications Web ASP.NET : l’une contient uniquement un service WCF, tandis que l’autre contient la page Web. aspx, qui appelle le service.</span><span class="sxs-lookup"><span data-stu-id="dab94-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="dab94-125">Lors de l’exécution de la solution, Visual Studio 2012 héberge les deux sites Web sur des ports différents, ce qui crée un environnement dans lequel le service et le client se trouvent sur des domaines différents.</span><span class="sxs-lookup"><span data-stu-id="dab94-125">When running the solution, Visual Studio 2012 will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dab94-126">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dab94-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="dab94-127">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="dab94-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="dab94-128">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="dab94-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dab94-129">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="dab94-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="dab94-130">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="dab94-130">To run the sample</span></span>  
  
1. <span data-ttu-id="dab94-131">Ouvrez la solution de l'exemple JSONP.</span><span class="sxs-lookup"><span data-stu-id="dab94-131">Open the solution for the JSONP Sample.</span></span>  
  
2. <span data-ttu-id="dab94-132">Appuyez sur F5 pour lancer `http://localhost:26648/JSONPClientPage.aspx` dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="dab94-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3. <span data-ttu-id="dab94-133">Notez qu’après le chargement de la page, les entrées de texte pour « name » et « Address » sont renseignées par des valeurs.</span><span class="sxs-lookup"><span data-stu-id="dab94-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="dab94-134">Ces valeurs ont été fournies par un appel au service WCF une fois que le navigateur a terminé le rendu de la page.</span><span class="sxs-lookup"><span data-stu-id="dab94-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
