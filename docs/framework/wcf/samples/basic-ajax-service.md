---
title: Basic AJAX Service
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 4705070c7f7f72db835073b30c5bda115a45f179
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892703"
---
# <a name="basic-ajax-service"></a>Basic AJAX Service

Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service AJAX (Basic JavaScript and XML) asynchrone ASP.NET (un service auquel vous pouvez accéder à l’aide du code JavaScript à partir d’un client de navigateur Web). L'attribut <xref:System.ServiceModel.Web.WebGetAttribute> est utilisé afin de garantir que le service répond aux requêtes HTTP GET et que ce service utilise le format de données JSON (JavaScript Object Notation) pour les réponses.

La prise en charge d’Ajax dans WCF est optimisée pour une `ScriptManager` utilisation avec ASP.NET AJAX par le biais du contrôle. Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez les [exemples Ajax](ajax.md).

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.

Dans le code suivant, l'attribut <xref:System.ServiceModel.Web.WebGetAttribute> est appliqué à l'opération `Add` afin de garantir que le service répond aux requêtes HTTP GET. Le code utilise la méthode GET pour des raisons pratiques (vous pouvez construire une requête HTTP GET à partir de tout navigateur Web). Vous pouvez également utiliser la méthode GET pour activer la mise en cache. HTTP POST est la valeur par défaut en l'absence d'attribut `WebGetAttribute`.

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

Le fichier d'exemple .svc utilise <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, qui ajoute un point de terminaison standard <xref:System.ServiceModel.Description.WebScriptEndpoint> au service. Ce point de terminaison est configuré à une adresse vide relative au fichier .svc. Cela signifie que l’adresse du service est `http://localhost/ServiceModelSamples/service.svc`, sans suffixe supplémentaire autre que le nom de l’opération.

`<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>`

Le <xref:System.ServiceModel.Description.WebScriptEndpoint> est préconfiguré pour rendre le service accessible à partir d'une page cliente ASP.NET AJAX. La section suivante dans Web.config peut être utilisée pour apporter des modifications de configuration supplémentaires au point de terminaison. Elle peut être supprimée si aucune modification supplémentaire n'est requise.

```xml
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name=""  />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

Le <xref:System.ServiceModel.Description.WebScriptEndpoint> affecte au format de données par défaut du service la valeur JSON au lieu de XML. Pour appeler le service, accédez à `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` après avoir terminé les étapes de configuration et de génération indiquées plus loin dans cette rubrique. L'utilisation d'une requête HTTP GET active cette fonctionnalité de test.

La page web PostAjaxClientPage.aspx du client contient le code ASP.NET permettant d’appeler le service à chaque fois que l’utilisateur clique sur l’un des boutons d’opération de cette page. Le contrôle `ScriptManager` est utilisé pour permettre l'accès à un proxy du service via JavaScript.

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">
    <Services>
        <asp:ServiceReference Path="service.svc" />
    </Services>
</asp:ScriptManager>
```

Le proxy local est instancié et les opérations sont appelées à l'aide du code Javascript suivant.

```javascript
// Code for extracting arguments n1 and n2 omitted…
// Instantiate a service proxy
var proxy = new SimpleAjaxService.ICalculator();
// Code for selecting operation omitted…
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);
```

Si l'appel du service réussit, le code appelle le gestionnaire `onSuccess` et le résultat de l'opération s'affiche dans une zone de texte.

```javascript
function onSuccess(mathResult){
     document.getElementById("result").value = mathResult;
}
```

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
