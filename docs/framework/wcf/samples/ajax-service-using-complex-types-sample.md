---
title: AJAX Service Using Complex Types, exemple
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 4227446e8844accd06490d8e7cf933da43d875a6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575912"
---
# <a name="ajax-service-using-complex-types-sample"></a>AJAX Service Using Complex Types, exemple

Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service AJAX (JavaScript et XML) asynchrone ASP.NET qui crée des instances de types complexes et les envoie entre le service et le client en tant que JavaScript Object Notation (JSON). Vous pouvez accéder à un service AJAX en utilisant le code JavaScript à partir d'un client de navigateur Web. Cet exemple s’appuie sur l’exemple de [service Ajax de base](basic-ajax-service.md) .

La prise en charge d’AJAX dans WCF est optimisée pour une utilisation avec ASP.NET AJAX par le biais du <xref:System.Web.UI.ScriptManager> contrôle. Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez les [exemples Ajax](ajax.md).

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Dans l’exemple suivant, le service est un service WCF sans code spécifique à AJAX. L'attribut <xref:System.ServiceModel.Web.WebGetAttribute> n'étant pas appliqué, le verbe HTTP par défaut ("POST") est utilisé. Le service a une opération appelée `DoMath` qui retourne un type complexe appelé `MathResult`. Le type complexe est un type de contrat de données standard qui ne contient pas non plus de code spécifique à AJAX.

```csharp
[DataContract]
public class MathResult
{
    [DataMember]
    public double sum;
    [DataMember]
    public double difference;
    [DataMember]
    public double product;
    [DataMember]
    public double quotient;
}
```

Créez un point de terminaison AJAX sur le service à l'aide de <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, comme dans l'exemple de servie AJAX de base.

La page Web client ComplexTypeClientPage. aspx contient du code ASP.NET et JavaScript pour appeler le service quand l’utilisateur clique sur le bouton **effectuer un calcul** sur la page. Le code permettant d’appeler le service construit un corps JSON et l’envoie à l’aide de HTTP HTTP, de la même façon que le [service Ajax à l’aide](ajax-service-using-http-post.md) de l’exemple http après.

Une fois l'appel de service réussi, vous pouvez accéder aux membres de données individuels (`sum`, `difference`, `product` et `quotient`) sur l'objet JavaScript résultant.

```javascript
function onSuccess(mathResult){
     document.getElementById("sum").value = mathResult.sum;
     document.getElementById("difference").value = mathResult.difference;
     document.getElementById("product").value = mathResult.product;
     document.getElementById("quotient").value = mathResult.quotient;
}
```

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Générez la solution ComplexTypeAjaxService. sln comme décrit dans [génération des exemples de Windows Communication Foundation](building-the-samples.md).

3. Accédez à `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (n’ouvrez pas ComplexTypeClientPage. aspx dans le navigateur à partir du répertoire du projet).

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`

## <a name="see-also"></a>Voir aussi

- [Basic AJAX Service](basic-ajax-service.md)
