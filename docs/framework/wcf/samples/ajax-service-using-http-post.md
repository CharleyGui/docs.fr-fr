---
title: AJAX Service Using HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 2fb98e38956719608517caa0e7eeaebd14df8d95
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882151"
---
# <a name="ajax-service-using-http-post"></a>AJAX Service Using HTTP POST
Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service ASP.NET Asynchronous JavaScript and XML (AJAX) qui utilise HTTP POST. Un service AJAX est un service auquel vous pouvez accéder à l'aide du code Javascript de base d'un client de navigateur Web. Cet exemple s’appuie sur le [base AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemple ; la seule différence entre les deux exemples est l’utilisation de HTTP POST au lieu de HTTP GET.  
  
 Prise en charge AJAX dans Windows Communication Foundation (WCF) est optimisé pour une utilisation avec ASP.NET AJAX via le `ScriptManager` contrôle. Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez le [exemples Ajax](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le service dans l’exemple suivant est un service WCF sans code spécifique à AJAX.  
  
 Si le <xref:System.ServiceModel.Web.WebInvokeAttribute> attribut est appliqué à une opération, ou le <xref:System.ServiceModel.Web.WebGetAttribute> attribut n’est pas appliqué, le verbe HTTP de valeur par défaut (« POST ») est utilisé. Les demandes POST sont plus difficiles à générer que les demandes GET, mais elles ne sont pas mises en cache ; utilisez des demandes POST pour toutes les opérations où la mise en cache n'est pas appropriée.  

```csharp
[ServiceContract(Namespace = "PostAjaxService")]  
public interface ICalculator  
{
    [WebInvoke]  
    double Add(double n1, double n2);  
    //Other operations omitted…  
}
```

 Créez un point de terminaison AJAX sur le service à l'aide de <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, comme dans l'exemple de servie AJAX de base.  
  
 Contrairement aux demandes GET, vous ne pouvez pas appeler des services POST depuis le navigateur. Par exemple, accédez à `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` entraîne une erreur, car le service POST s’attend le `n1` et `n2` les paramètres à envoyer dans le corps du message au format JSON et non dans l’URL.  
  
 La page web PostAjaxClientPage.aspx du client contient le code ASP.NET pour appeler le service toutes les fois que l’utilisateur clique sur l’un des boutons d’opération de la page. Le service répond de la même façon que dans le [base AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) exemple, avec la demande GET.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir suivi les instructions d’installation [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Générez la solution PostAjaxService.sln comme décrit dans [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Accédez à `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (n’ouvrez pas PostAjaxClientPage.aspx dans le navigateur depuis le répertoire du projet).
