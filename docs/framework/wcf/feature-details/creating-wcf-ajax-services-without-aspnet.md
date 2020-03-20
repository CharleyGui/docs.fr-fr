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
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Création de services AJAX WCF sans ASP.NET
Les services AJAX de la Windows Communication Foundation (WCF) peuvent être consultés à partir de n’importe quelle page Web compatible JavaScript, sans nécessiter ASP.NET AJAX. Ce sujet décrit comment créer un tel service WCF.  
  
 Pour des instructions sur l’utilisation de WCF avec ASP.NET AJAX, voir [Créer des services WCF pour ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md).  
  
 Il y a trois parties à la création d’un service WCF AJAX :  
  
- Création d'un point de terminaison AJAX accessible à partir du navigateur  
  
- Création d'un contrat de service compatible AJAX  
  
- Accès aux services AJAX WCF  
  
## <a name="creating-an-ajax-endpoint"></a>Création d'un point de terminaison AJAX  
 La façon la plus élémentaire d’activer le <xref:System.ServiceModel.Activation.WebServiceHostFactory> support AJAX dans un service WCF est d’utiliser le fichier .svc associé au service, comme dans l’exemple suivant.  
  
```text
<%ServiceHost
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CityService"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory  
%>  
```  
  
 Vous avez également la possibilité d'utiliser une configuration pour ajouter un point de terminaison AJAX. Utilisez le <xref:System.ServiceModel.WebHttpBinding> sur le point de terminaison de service et configurez ce point de terminaison avec le <xref:System.ServiceModel.Description.WebHttpBehavior>, comme l'illustre l'extrait de code suivant.  
  
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
  
 Pour un exemple de travail, voir le [service AJAX avec JSON et XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Création d'un contrat de service compatible AJAX  
 Par défaut, les contrats de service exposés sur un point de terminaison AJAX retournent les données au format XML. Qui plus est, les opérations de service sont, par défaut, accessibles par le biais des requêtes HTTP POST adressées aux URL qui incluent l'adresse du point de terminaison suivie du nom de l'opération, comme l'illustre l'exemple suivant.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Cette opération est accessible à `http://serviceaddress/endpointaddress/GetCities` l’aide d’un MESSAGE HTTP pour retourner un message XML.  
  
 Vous pouvez utiliser le modèle de programmation Web complet pour personnaliser ces aspects de base. Par exemple, vous pouvez utiliser les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> pour contrôler le verbe HTTP auquel l'opération répond, ou vous pouvez utiliser la propriété `UriTemplate` de ces attributs respectifs pour spécifier des URI personnalisés. Pour plus d’informations, consultez le thème [du modèle de programmation HTTP web de la WCF.](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
  
 Le format de données JSON est souvent utilisé dans les services AJAX. Pour créer une opération qui retourne des données JSON au lieu de données XML, affectez <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> à la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> (ou la propriété <xref:System.ServiceModel.Web.WebMessageFormat.Json>). Le sujet [stand-Alone JSON Serialization](../../../../docs/framework/wcf/feature-details/stand-alone-json-serialization.md) montre comment intégrés .NET types et types de contrats de données carte à JSON.  
  
 En principe, les demandes et les réponses JSON sont composées d'un seul élément. Pour l'opération `GetCities` précédente, la demande ressemble à l'instruction suivante.  
  
```json
"na"  
```  
  
 La réponse à cette demande ressemble à l'instruction suivante.  
  
```json
["Nairobi", "Naples", "Nashville"]  
```  
  
 Si l'opération utilise un paramètre supplémentaire, le style de demande doit être encapsulé pour encapsuler les deux paramètres dans un seul objet JSON. L'exemple suivant illustre un message JSON de ce style.  
  
```json  
{"firstLetters": "na", "maxNumber": 2}  
```  
  
 Le contrat suivant accepte ce message.  
  
```csharp
[WebInvoke(BodyStyle=WebMessageBodyStyle.WrappedRequest, ResponseFormat=WebMessageFormat.Json)]  
[OperationContract]  
string[] GetCities(string firstLetters, int maxNumber);  
```  
  
## <a name="accessing-ajax-services"></a>Accès aux services AJAX  
 Les critères d’évaluation WCF AJAX acceptent toujours les demandes de JSON et de XML.  
  
 Les demandes HTTP POST avec un type de contenu d'"application/json" sont traitées comme JSON, et celles qui ont un type de contenu indiquant XML (par exemple, "texte/xml") sont traitées comme XML.  
  
 Les requêtes HTTP GET contiennent tous les paramètres de requête dans l'URL proprement dite.  
  
 Il revient à l'utilisateur de choisir comment créer la requête HTTP au point de terminaison. De plus, l'utilisateur dispose d'un contrôle total sur la construction du JSON qui forme le corps de la demande. Pour un exemple de création d’une demande de JavaScript, voir le [service AJAX avec JSON et XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).
