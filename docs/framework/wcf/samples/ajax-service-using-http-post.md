---
title: AJAX Service Using HTTP POST
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: 143585b40a493983b7265971a17224165de6f36d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575886"
---
# <a name="ajax-service-using-http-post"></a>AJAX Service Using HTTP POST

Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service JavaScript et XML (AJAX) asynchrone ASP.NET qui utilise HTTP. Un service AJAX est un service auquel vous pouvez accéder à l'aide du code Javascript de base d'un client de navigateur Web. Cet exemple s’appuie sur l’exemple [Basic AJAX Service](basic-ajax-service.md) . la seule différence entre les deux exemples est l’utilisation de HTTP POSTCONNEXION au lieu de HTTP.

La prise en charge d’AJAX dans Windows Communication Foundation (WCF) est optimisée pour une utilisation avec ASP.NET AJAX par le biais du `ScriptManager` contrôle. Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez les [exemples Ajax](ajax-service-using-http-post.md).

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Dans l’exemple suivant, le service est un service WCF sans code spécifique à AJAX.

Si l' <xref:System.ServiceModel.Web.WebInvokeAttribute> attribut est appliqué à une opération, ou si l' <xref:System.ServiceModel.Web.WebGetAttribute> attribut n’est pas appliqué, le verbe http par défaut (« poster ») est utilisé. Les demandes POST sont plus difficiles à générer que les demandes GET, mais elles ne sont pas mises en cache ; utilisez des demandes POST pour toutes les opérations où la mise en cache n'est pas appropriée.

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

Contrairement aux demandes GET, vous ne pouvez pas appeler des services POST depuis le navigateur. Par exemple, la navigation vers `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` génère une erreur, car le service de publication s’attend à ce que les `n1` `n2` paramètres et soient envoyés dans le corps du message au format JSON, et non dans l’URL.

La page web PostAjaxClientPage.aspx du client contient le code ASP.NET pour appeler le service toutes les fois que l’utilisateur clique sur l’un des boutons d’opération de la page. Le service répond de la même façon que dans l’exemple de [service Ajax de base](basic-ajax-service.md) , avec la requête d’extraction.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Veillez à suivre les instructions d’installation [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Générez la solution PostAjaxService. sln comme décrit dans [génération des exemples de Windows Communication Foundation](building-the-samples.md).

3. Accédez à `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (n’ouvrez pas PostAjaxClientPage. aspx dans le navigateur à partir du répertoire du projet).
