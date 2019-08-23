---
title: AJAX Service Using Complex Types, exemple
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 98d33c250be31ac43eef6d76ade997a30af87090
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923691"
---
# <a name="ajax-service-using-complex-types-sample"></a>AJAX Service Using Complex Types, exemple
Cet exemple montre comment utiliser Windows Communication Foundation (WCF) pour créer un service AJAX (JavaScript et XML) asynchrone ASP.NET qui crée des instances de types complexes et les envoie entre le service et le client en tant que JavaScript Object Notation (JSON). Vous pouvez accéder à un service AJAX en utilisant le code JavaScript à partir d'un client de navigateur Web. Cet exemple s’appuie sur l’exemple de [service Ajax de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .  
  
 La prise en charge d’Ajax dans WCF est optimisée pour une <xref:System.Web.UI.ScriptManager> utilisation avec ASP.NET AJAX par le biais du contrôle. Pour obtenir un exemple d’utilisation de WCF avec ASP.NET AJAX, consultez les [exemples Ajax](ajax.md).  
  
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
  
 La page Web client ComplexTypeClientPage. aspx contient du code ASP.NET et JavaScript pour appeler le service quand l’utilisateur clique sur le bouton **effectuer un calcul** sur la page. Le code permettant d’appeler le service construit un corps JSON et l’envoie à l’aide de HTTP HTTP, de la même façon que le [service Ajax à l’aide](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) de l’exemple http après.  
  
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
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Générez la solution ComplexTypeAjaxService. sln comme décrit dans [génération des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Accédez à `http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (n’ouvrez pas ComplexTypeClientPage. aspx dans le navigateur à partir du répertoire du projet).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>Voir aussi

- [Service AJAX de base](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
