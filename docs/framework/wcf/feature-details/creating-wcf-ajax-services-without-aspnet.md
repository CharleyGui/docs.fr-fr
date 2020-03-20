---
title: Création de services AJAX WCF sans ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: f4d1d093132c501844aacbaa9cf28ecc3cede442
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185241"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a><span data-ttu-id="72165-102">Création de services AJAX WCF sans ASP.NET</span><span class="sxs-lookup"><span data-stu-id="72165-102">Creating WCF AJAX Services without ASP.NET</span></span>
<span data-ttu-id="72165-103">Les services AJAX de la Windows Communication Foundation (WCF) peuvent être consultés à partir de n’importe quelle page Web compatible JavaScript, sans nécessiter ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="72165-103">Windows Communication Foundation (WCF) AJAX services can be accessed from any JavaScript-enabled Web page, without requiring ASP.NET AJAX.</span></span> <span data-ttu-id="72165-104">Ce sujet décrit comment créer un tel service WCF.</span><span class="sxs-lookup"><span data-stu-id="72165-104">This topic describes how to create such a WCF service.</span></span>  
  
 <span data-ttu-id="72165-105">Pour des instructions sur l’utilisation de WCF avec ASP.NET AJAX, voir [Créer des services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span><span class="sxs-lookup"><span data-stu-id="72165-105">For instructions on using WCF with ASP.NET AJAX, see [Creating WCF Services for ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).</span></span>  
  
 <span data-ttu-id="72165-106">Il y a trois parties à la création d’un service WCF AJAX :</span><span class="sxs-lookup"><span data-stu-id="72165-106">There are three parts to a creating a WCF AJAX service:</span></span>  
  
- <span data-ttu-id="72165-107">Création d'un point de terminaison AJAX accessible à partir du navigateur</span><span class="sxs-lookup"><span data-stu-id="72165-107">Creating an AJAX endpoint that can be accessed from the browser.</span></span>  
  
- <span data-ttu-id="72165-108">Création d'un contrat de service compatible AJAX</span><span class="sxs-lookup"><span data-stu-id="72165-108">Creating an AJAX-compatible service contract.</span></span>  
  
- <span data-ttu-id="72165-109">Accès aux services AJAX WCF</span><span class="sxs-lookup"><span data-stu-id="72165-109">Accessing WCF AJAX services.</span></span>  
  
## <a name="creating-an-ajax-endpoint"></a><span data-ttu-id="72165-110">Création d'un point de terminaison AJAX</span><span class="sxs-lookup"><span data-stu-id="72165-110">Creating an AJAX Endpoint</span></span>  
 <span data-ttu-id="72165-111">La façon la plus élémentaire d’activer le <xref:System.ServiceModel.Activation.WebServiceHostFactory> support AJAX dans un service WCF est d’utiliser le fichier .svc associé au service, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="72165-111">The most basic way to enable AJAX support in a WCF service is to use the <xref:System.ServiceModel.Activation.WebServiceHostFactory> in the .svc file associated with the service, as in the following example.</span></span>  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 <span data-ttu-id="72165-112">Vous avez également la possibilité d'utiliser une configuration pour ajouter un point de terminaison AJAX.</span><span class="sxs-lookup"><span data-stu-id="72165-112">Alternatively, you can also use configuration to add an AJAX endpoint.</span></span> <span data-ttu-id="72165-113">Utilisez le <xref:System.ServiceModel.WebHttpBinding> sur le point de terminaison de service et configurez ce point de terminaison avec le <xref:System.ServiceModel.Description.WebHttpBehavior>, comme l'illustre l'extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="72165-113">Use the <xref:System.ServiceModel.WebHttpBinding> on the service endpoint and configure that endpoint with the <xref:System.ServiceModel.Description.WebHttpBehavior> as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="72165-114">Pour un exemple de travail, voir le [service AJAX avec JSON et XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="72165-114">For a working example, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>  
  
## <a name="creating-an-ajax-compatible-service-contract"></a><span data-ttu-id="72165-115">Création d'un contrat de service compatible AJAX</span><span class="sxs-lookup"><span data-stu-id="72165-115">Creating an AJAX-Compatible Service Contract</span></span>  
 <span data-ttu-id="72165-116">Par défaut, les contrats de service exposés sur un point de terminaison AJAX retournent les données au format XML.</span><span class="sxs-lookup"><span data-stu-id="72165-116">By default, service contracts exposed over an AJAX endpoint return data in the XML format.</span></span> <span data-ttu-id="72165-117">Qui plus est, les opérations de service sont, par défaut, accessibles par le biais des requêtes HTTP POST adressées aux URL qui incluent l'adresse du point de terminaison suivie du nom de l'opération, comme l'illustre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="72165-117">Also, by default service operations are accessible through HTTP POST requests to URLs that include the endpoint address followed by the operation name, as shown in the following example.</span></span>  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 <span data-ttu-id="72165-118">Cette opération est accessible à `http://serviceaddress/endpointaddress/GetCities` l’aide d’un MESSAGE HTTP pour retourner un message XML.</span><span class="sxs-lookup"><span data-stu-id="72165-118">This operation is accessible using an HTTP POST to `http://serviceaddress/endpointaddress/GetCities` and return an XML message.</span></span>  
  
 <span data-ttu-id="72165-119">Vous pouvez utiliser le modèle de programmation Web complet pour personnaliser ces aspects de base.</span><span class="sxs-lookup"><span data-stu-id="72165-119">You can use the full Web Programming Model to customize these basic aspects.</span></span> <span data-ttu-id="72165-120">Par exemple, vous pouvez utiliser les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> pour contrôler le verbe HTTP auquel l'opération répond, ou vous pouvez utiliser la propriété `UriTemplate` de ces attributs respectifs pour spécifier des URI personnalisés.</span><span class="sxs-lookup"><span data-stu-id="72165-120">For example, you can use the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to control the HTTP verb to which the operation responds or use the `UriTemplate` property of these respective attributes to specify custom URIs.</span></span> <span data-ttu-id="72165-121">Pour plus d’informations, consultez le thème [du modèle de programmation HTTP web de la WCF.](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)</span><span class="sxs-lookup"><span data-stu-id="72165-121">For more information, see the [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md) topic.</span></span>  
  
 <span data-ttu-id="72165-122">Le format de données JSON est souvent utilisé dans les services AJAX.</span><span class="sxs-lookup"><span data-stu-id="72165-122">The JSON data format is often used in AJAX services.</span></span> <span data-ttu-id="72165-123">Pour créer une opération qui retourne des données JSON au lieu de données XML, affectez <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> à la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> (ou la propriété <xref:System.ServiceModel.Web.WebMessageFormat.Json>).</span><span class="sxs-lookup"><span data-stu-id="72165-123">To create an operation that returns JSON instead of XML, set the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> (or the <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A>) property to <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="72165-124">Le sujet [stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) montre comment intégrés .NET types et types de contrats de données carte à JSON.</span><span class="sxs-lookup"><span data-stu-id="72165-124">The [Stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) topic shows how built-in .NET types and data contract types map to JSON.</span></span>  
  
 <span data-ttu-id="72165-125">En principe, les demandes et les réponses JSON sont composées d'un seul élément.</span><span class="sxs-lookup"><span data-stu-id="72165-125">Normally, JSON requests and responses consist of just one item.</span></span> <span data-ttu-id="72165-126">Pour l'opération `GetCities` précédente, la demande ressemble à l'instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="72165-126">For the preceding `GetCities` operation, the request resembles the following statement.</span></span>  
  
```json
"na"  
```  
  
 <span data-ttu-id="72165-127">La réponse à cette demande ressemble à l'instruction suivante.</span><span class="sxs-lookup"><span data-stu-id="72165-127">The response to that request resembles the following statement.</span></span>  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 <span data-ttu-id="72165-128">Si l'opération utilise un paramètre supplémentaire, le style de demande doit être encapsulé pour encapsuler les deux paramètres dans un seul objet JSON.</span><span class="sxs-lookup"><span data-stu-id="72165-128">If the operation takes an extra parameter, the request style must be wrapped to wrap both parameters in a single JSON object.</span></span> <span data-ttu-id="72165-129">L'exemple suivant illustre un message JSON de ce style.</span><span class="sxs-lookup"><span data-stu-id="72165-129">An example of this style JSON message is in the following example.</span></span>  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 <span data-ttu-id="72165-130">Le contrat suivant accepte ce message.</span><span class="sxs-lookup"><span data-stu-id="72165-130">The following contract accepts this message.</span></span>  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a><span data-ttu-id="72165-131">Accès aux services AJAX</span><span class="sxs-lookup"><span data-stu-id="72165-131">Accessing AJAX Services</span></span>  
 <span data-ttu-id="72165-132">Les critères d’évaluation WCF AJAX acceptent toujours les demandes de JSON et de XML.</span><span class="sxs-lookup"><span data-stu-id="72165-132">WCF AJAX endpoints always accept both JSON and XML requests.</span></span>  
  
 <span data-ttu-id="72165-133">Les demandes HTTP POST avec un type de contenu d'"application/json" sont traitées comme JSON, et celles qui ont un type de contenu indiquant XML (par exemple, "texte/xml") sont traitées comme XML.</span><span class="sxs-lookup"><span data-stu-id="72165-133">HTTP POST requests with a content-type of "application/json" are treated as JSON, and those with content-type that indicate XML (for example, "text/xml") are treated as XML.</span></span>  
  
 <span data-ttu-id="72165-134">Les requêtes HTTP GET contiennent tous les paramètres de requête dans l'URL proprement dite.</span><span class="sxs-lookup"><span data-stu-id="72165-134">HTTP GET requests contain all the request parameters in the URL itself.</span></span>  
  
 <span data-ttu-id="72165-135">Il revient à l'utilisateur de choisir comment créer la requête HTTP au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="72165-135">It is up to the user to decide how to create the HTTP request to the endpoint.</span></span> <span data-ttu-id="72165-136">De plus, l'utilisateur dispose d'un contrôle total sur la construction du JSON qui forme le corps de la demande.</span><span class="sxs-lookup"><span data-stu-id="72165-136">Also, the user has full control over constructing the JSON that forms the body of the request.</span></span> <span data-ttu-id="72165-137">Pour un exemple de création d’une demande de JavaScript, voir le [service AJAX avec JSON et XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span><span class="sxs-lookup"><span data-stu-id="72165-137">For an example of creating a request from JavaScript, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>
