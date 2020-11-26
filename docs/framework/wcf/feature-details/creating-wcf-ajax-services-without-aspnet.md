---
title: Création de services AJAX WCF sans ASP.NET
ms.date: 03/30/2017
ms.assetid: ba4a7d1b-e277-4978-9f62-37684e6dc934
ms.openlocfilehash: 37a442f85ddf5c0a1687c05e26f140d052eaa94f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239092"
---
# <a name="creating-wcf-ajax-services-without-aspnet"></a>Création de services AJAX WCF sans ASP.NET

Les services AJAX Windows Communication Foundation (WCF) sont accessibles à partir de n’importe quelle page Web compatible avec JavaScript, sans nécessiter ASP.NET AJAX. Cette rubrique explique comment créer un service WCF de ce type.  
  
 Pour obtenir des instructions sur l’utilisation de WCF avec ASP.NET AJAX, consultez [création de services WCF pour ASP.NET AJAX](creating-wcf-services-for-aspnet-ajax.md).  
  
 La création d’un service WCF AJAX se décomposant de trois parties :  
  
- Création d'un point de terminaison AJAX accessible à partir du navigateur  
  
- Création d'un contrat de service compatible AJAX  
  
- Accès aux services AJAX WCF  
  
## <a name="creating-an-ajax-endpoint"></a>Création d'un point de terminaison AJAX  

 La méthode la plus simple pour activer la prise en charge d’AJAX dans un service WCF consiste à utiliser <xref:System.ServiceModel.Activation.WebServiceHostFactory> dans le fichier. svc associé au service, comme dans l’exemple suivant.  
  
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
  
 Pour obtenir un exemple fonctionnel, consultez le [service Ajax avec JSON et XML](../samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="creating-an-ajax-compatible-service-contract"></a>Création d'un contrat de service compatible AJAX  

 Par défaut, les contrats de service exposés sur un point de terminaison AJAX retournent les données au format XML. Qui plus est, les opérations de service sont, par défaut, accessibles par le biais des requêtes HTTP POST adressées aux URL qui incluent l'adresse du point de terminaison suivie du nom de l'opération, comme l'illustre l'exemple suivant.  
  
```csharp
[OperationContract]  
string[] GetCities(string firstLetters);  
```  
  
 Cette opération est accessible à l’aide d’une requête HTTP `http://serviceaddress/endpointaddress/GetCities` et renvoie un message XML.  
  
 Vous pouvez utiliser le modèle de programmation Web complet pour personnaliser ces aspects de base. Par exemple, vous pouvez utiliser les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> pour contrôler le verbe HTTP auquel l'opération répond, ou vous pouvez utiliser la propriété `UriTemplate` de ces attributs respectifs pour spécifier des URI personnalisés. Pour plus d’informations, consultez la rubrique [modèle de programmation http Web WCF](wcf-web-http-programming-model.md) .  
  
 Le format de données JSON est souvent utilisé dans les services AJAX. Pour créer une opération qui retourne des données JSON au lieu de données XML, affectez <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> à la propriété <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> (ou la propriété <xref:System.ServiceModel.Web.WebMessageFormat.Json>). La rubrique de [SÉRIALISATION JSON autonome](stand-alone-json-serialization.md) montre comment les types .net intégrés et les types de contrat de données sont mappés au format JSON.  
  
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

 Les points de terminaison WCF AJAX acceptent toujours les requêtes JSON et XML.  
  
 Les requêtes HTTP HTTP avec le type de contenu « application/JSON » sont traitées en tant que JSON, et celles avec le type de contenu qui indiquent XML (par exemple, « texte/XML ») sont traitées comme XML.  
  
 Les requêtes HTTP GET contiennent tous les paramètres de requête dans l'URL proprement dite.  
  
 Il revient à l'utilisateur de choisir comment créer la requête HTTP au point de terminaison. De plus, l'utilisateur dispose d'un contrôle total sur la construction du JSON qui forme le corps de la demande. Pour obtenir un exemple de création d’une demande à partir de JavaScript, consultez le [service Ajax avec JSON et XML](../samples/ajax-service-with-json-and-xml-sample.md).
