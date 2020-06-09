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
# <a name="ajax-service-with-json-and-xml-sample"></a>AJAX Service with JSON and XML, exemple

Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service JavaScript et XML (AJAX) asynchrone qui retourne des données JavaScript Object Notation (JSON) ou XML. Vous pouvez accéder à un service AJAX en utilisant le code JavaScript à partir d'un client de navigateur Web. Cet exemple s’appuie sur l’exemple de [service Ajax de base](basic-ajax-service.md) .

Contrairement aux autres exemples AJAX, celui-ci n'utilise pas ASP.NET AJAX et le contrôle <xref:System.Web.UI.ScriptManager>. Avec une configuration supplémentaire, les services WCF AJAX sont accessibles à partir de n’importe quelle page HTML via JavaScript, et ce scénario est illustré ici. Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez [exemples Ajax](ajax.md).

Cet exemple illustre comment commuter le type de réponse d'une opération entre JSON et XML. Cette fonctionnalité est disponible que le service soit configuré pour être accessible par ASP.NET AJAX ou par une page cliente HTML/JavaScript.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Pour permettre l'utilisation de clients AJAX non-ASP.NET, utilisez <xref:System.ServiceModel.Activation.WebServiceHostFactory> (pas <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) dans le fichier .svc. <xref:System.ServiceModel.Activation.WebServiceHostFactory> ajoute un point de terminaison standard <xref:System.ServiceModel.Description.WebHttpEndpoint> au service. Le point de terminaison est configuré à une adresse vide relative au fichier. svc ; Cela signifie que l’adresse du service est `http://localhost/ServiceModelSamples/service.svc` , sans suffixe supplémentaire autre que le nom de l’opération.

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>`

La section suivante dans Web.config peut être utilisée pour apporter des modifications de configuration supplémentaires au point de terminaison. Elle peut être supprimée si aucune modification supplémentaire n'est requise.

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

Le format de données par défaut pour <xref:System.ServiceModel.Description.WebHttpEndpoint> est XML, tandis que le format de données par défaut pour <xref:System.ServiceModel.Description.WebScriptEndpoint> est JSON. Pour plus d’informations, consultez [création de services WCF Ajax sans ASP.net](../feature-details/creating-wcf-ajax-services-without-aspnet.md).

Dans l’exemple suivant, le service est un service WCF standard avec deux opérations. Ces deux opérations requièrent le style de corps <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> sur les attributs <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute>, ce qui est spécifique au comportement `webHttp` et n'a aucune incidence sur le commutateur de format de données JSON/XML.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathXml(double n1, double n2);
```

Le format de réponse pour l’opération est spécifié en tant que XML, qui est le paramètre par défaut pour le [\<webHttp>](../../configure-apps/file-schema/wcf/webhttp.md) comportement. Il est toutefois conseillé de spécifier explicitement le format de réponse.

L'autre opération utilise l'attribut `WebInvokeAttribute` et spécifie explicitement JSON au lieu de XML pour la réponse.

```csharp
[OperationContract]
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]
MathResult DoMathJson(double n1, double n2);
```

Notez que dans les deux cas, les opérations retournent un type complexe, `MathResult` , qui est un type de contrat de données WCF standard.

La page Web client XmlAjaxClientPage. htm contient du code JavaScript qui appelle l’une des deux opérations précédentes quand l’utilisateur clique sur les boutons **exécuter le calcul (retourner JSON)** ou **exécuter le calcul (retour XML)** sur la page. Le code permettant d'appeler le service construit un corps JSON et l'envoie à l'aide de HTTP POST. La demande est créée manuellement dans JavaScript, contrairement à l’exemple de [service Ajax de base](basic-ajax-service.md) et aux autres exemples utilisant ASP.NET AJAX.

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

La réponse du service s'affiche sans traitement supplémentaire dans une zone de texte de la page. Cet exemple est implémenté à des fins de démonstration pour vous permettre d'observer directement les formats de données XML et JSON utilisés.

```javascript
// Create result handler
xmlHttp.onreadystatechange=function(){
     if(xmlHttp.readyState == 4){
          document.getElementById("result").value = xmlHttp.responseText;
     }
}
```

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Générez la solution XmlAjaxService. sln comme décrit dans [génération des exemples de Windows Communication Foundation](building-the-samples.md).

3. Accédez à `http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm` (n’ouvrez pas XmlAjaxClientPage. htm dans le navigateur à partir du répertoire du projet).

## <a name="see-also"></a>Voir aussi

- [AJAX Service Using HTTP POST](ajax-service-using-http-post.md)
