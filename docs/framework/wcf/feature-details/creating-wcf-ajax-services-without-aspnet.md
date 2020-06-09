---
title: Création de services AJAX WCF sans ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: b5f0f730f90227dcccc7e5ebf533d80a28f6e6eb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599293"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="152c7-102">Création de services AJAX WCF sans ASP.NET</span><span class="sxs-lookup"><span data-stu-id="152c7-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="152c7-103">Les services AJAX Windows Communication Foundation (WCF) sont accessibles à partir de n’importe quelle page Web compatible avec JavaScript, sans nécessiter ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="152c7-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="152c7-104">Cette rubrique explique comment créer un service WCF de ce type.</span><span class="sxs-lookup"><span data-stu-id="152c7-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="152c7-105">Pour obtenir des instructions sur l’utilisation de WCF avec ASP.NET AJAX, consultez [création de services WCF pour ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="152c7-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="152c7-106">La création d’un service WCF AJAX se décomposant de trois parties :</span><span class="sxs-lookup"><span data-stu-id="152c7-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="152c7-107">Création d'un point de terminaison AJAX accessible à partir du navigateur</span><span class="sxs-lookup"><span data-stu-id="152c7-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="152c7-108">Création d'un contrat de service compatible AJAX</span><span class="sxs-lookup"><span data-stu-id="152c7-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="152c7-109">Accès aux services AJAX WCF</span><span class="sxs-lookup"><span data-stu-id="152c7-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="152c7-110">Création d'un point de terminaison AJAX</span><span class="sxs-lookup"><span data-stu-id="152c7-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="152c7-111">La méthode la plus simple pour activer la prise en charge d’AJAX dans un service WCF consiste à utiliser <xref:System.ServiceModel.Activation.WebServiceHostFactory> dans le fichier. svc associé au service, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="152c7-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="152c7-112">Vous avez également la possibilité d'utiliser une configuration pour ajouter un point de terminaison AJAX.</span><span class="sxs-lookup"><span data-stu-id="152c7-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="152c7-113">Utilisez le <xref:System.ServiceModel.WebHttpBinding> sur le point de terminaison de service et configurez ce point de terminaison avec le <xref:System.ServiceModel.Description.WebHttpBehavior>, comme l'illustre l'extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="152c7-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="AjaxBehavior">  
          <webHttp/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Ajax.Samples.CityService">  
        <endpoint
          address="ajaxEndpoint"  
          behaviorConfiguration="AjaxBehavior"  
          binding="webHttpBinding"  
          contract="Microsoft.Ajax.Samples.ICityService" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="152c7-114">Pour obtenir un exemple fonctionnel, consultez le [service Ajax avec JSON et XML](../samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="152c7-114">For a working example, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="152c7-115">Création d'un contrat de service compatible AJAX</span><span class="sxs-lookup"><span data-stu-id="152c7-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="152c7-116">Par défaut, les contrats de service exposés sur un point de terminaison AJAX retournent les données au format XML.</span><span class="sxs-lookup"><span data-stu-id="152c7-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="152c7-117">Qui plus est, les opérations de service sont, par défaut, accessibles par le biais des requêtes HTTP POST adressées aux URL qui incluent l'adresse du point de terminaison suivie du nom de l'opération, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="152c7-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="152c7-118">Cette opération est accessible à l’aide d’une requête HTTP `http://serviceaddress/endpointaddress/GetCities` et renvoie un message XML.</span><span class="sxs-lookup"><span data-stu-id="152c7-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="152c7-119">Vous pouvez utiliser le modèle de programmation Web complet pour personnaliser ces aspects de base.</span><span class="sxs-lookup"><span data-stu-id="152c7-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="152c7-120">Par exemple, vous pouvez utiliser les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> pour contrôler le verbe HTTP auquel l'opération répond, ou vous pouvez utiliser la propriété `UriTemplate` de ces attributs respectifs pour spécifier des URI personnalisés.</span><span class="sxs-lookup"><span data-stu-id="152c7-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="152c7-121">Pour plus d’informations, consultez la rubrique [modèle de programmation http Web WCF](wcf-web-http-programming-model.md) .</span><span class="sxs-lookup"><span data-stu-id="152c7-121">For more information, see the [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="152c7-122">Le format de données JSON est souvent utilisé dans les services AJAX.</span><span class="sxs-lookup"><span data-stu-id="152c7-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="152c7-123">Pour créer une opération qui retourne des données JSON au lieu de données XML, affectez <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> à la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> (ou la propriété <xref:System.ServiceModel.Web.WebMessageFormat.Json>).</span><span class="sxs-lookup"><span data-stu-id="152c7-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="152c7-124">La rubrique de [SÉRIALISATION JSON autonome](stand-alone-json-serialization.md) montre comment les types .net intégrés et les types de contrat de données sont mappés au format JSON.</span><span class="sxs-lookup"><span data-stu-id="152c7-124">The [Stand-Alone JSON Serialization](stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="152c7-125">En principe, les demandes et les réponses JSON sont composées d'un seul élément.</span><span class="sxs-lookup"><span data-stu-id="152c7-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="152c7-126">Pour l'opération `GetCities` précédente, la demande ressemble à l'instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="152c7-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="152c7-127">La réponse à cette demande ressemble à l'instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="152c7-127">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="152c7-128">Si l'opération utilise un paramètre supplémentaire, le style de demande doit être encapsulé pour encapsuler les deux paramètres dans un seul objet JSON.</span><span class="sxs-lookup"><span data-stu-id="152c7-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="152c7-129">L'exemple suivant illustre un message JSON de ce style.</span><span class="sxs-lookup"><span data-stu-id="152c7-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="152c7-130">Le contrat suivant accepte ce message.</span><span class="sxs-lookup"><span data-stu-id="152c7-130">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="152c7-131">Accès aux services AJAX</span><span class="sxs-lookup"><span data-stu-id="152c7-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="152c7-132">Les points de terminaison WCF AJAX acceptent toujours les requêtes JSON et XML.</span><span class="sxs-lookup"><span data-stu-id="152c7-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="152c7-133">Les requêtes HTTP HTTP avec le type de contenu « application/JSON » sont traitées en tant que JSON, et celles avec le type de contenu qui indiquent XML (par exemple, « texte/XML ») sont traitées comme XML.</span><span class="sxs-lookup"><span data-stu-id="152c7-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="152c7-134">Les requêtes HTTP GET contiennent tous les paramètres de requête dans l'URL proprement dite.</span><span class="sxs-lookup"><span data-stu-id="152c7-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="152c7-135">Il revient à l'utilisateur de choisir comment créer la requête HTTP au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="152c7-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="152c7-136">De plus, l'utilisateur dispose d'un contrôle total sur la construction du JSON qui forme le corps de la demande.</span><span class="sxs-lookup"><span data-stu-id="152c7-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="152c7-137">Pour obtenir un exemple de création d’une demande à partir de JavaScript, consultez le [service Ajax avec JSON et XML](../samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="152c7-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../samples/ajax-service-with-json-and-xml-sample.md).</span></span>
