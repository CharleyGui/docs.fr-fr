---
title: 'Anticipation de l‘adoption de Windows Communication Foundation : faciliter la future migration'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 995bdaaaba96bf8697ea75c1f1a17fa8e51ec2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185470"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Anticipation de l‘adoption de Windows Communication Foundation : faciliter la future migration
Afin d’assurer une migration future plus facile des nouvelles demandes de ASP.NET vers le WCF, suivez les recommandations précédentes ainsi que les recommandations suivantes.  
  
## <a name="protocols"></a>Protocoles  
 Désactivez la prise en charge d'ASP.NET 2.0 pour SOAP 1.2 :  
  
```xml  
<configuration>  
     <system.web>  
      <webServices >  
          <protocols>  
           <remove name="HttpSoap12"/>  
          </protocols>
      </webServices>  
     </system.web>
</configuration>  
```  
  
 Cela est conseillé parce que WCF nécessite des messages conformes à différents protocoles, comme SOAP 1.1 et SOAP 1.2, pour aller en utilisant différents critères d’évaluation. Si un service Web ASP.NET 2.0 est configuré pour prendre en charge à la fois SOAP 1.1 et SOAP 1.2, qui est la configuration par défaut, alors il ne peut pas être migré vers l’avant vers un seul point de terminaison WCF à l’adresse originale qui serait certainement compatible avec l’ensemble de la ASP.NET Web clients existants du service. De plus, le choix de SOAP 1.2 au lieu de 1.1 restreint davantage la clientèle du service.  
  
## <a name="service-development"></a>Développement des services  
 WCF vous permet de définir <xref:System.ServiceModel.ServiceContractAttribute> les contrats de service en appliquant les interfaces ou aux classes. Il est recommandé d'appliquer l'attribut à une interface plutôt qu'à une classe, afin de créer une définition d'un contrat qui peut être implémenté de différentes façons par un nombre illimité de classes. ASP.NET 2.0 prend en charge la possibilité d'appliquer l'attribut <xref:System.Web.Services.WebService> aux interfaces aussi bien qu'aux classes. Toutefois, comme indiqué précédemment, ASP.NET 2.0 présente un défaut qui fait que le paramètre Namespace de l'attribut <xref:System.Web.Services.WebService> n'a aucun effet lorsque cet attribut est appliqué à une interface plutôt qu'à une classe. Comme il est généralement conseillé de modifier l’espace de `http://tempuri.org`nom d’un service <xref:System.Web.Services.WebService> à partir de la valeur par défaut, <xref:System.ServiceModel.ServiceContractAttribute> en utilisant le paramètre Namespace de l’attribut, il faut continuer à définir ASP.NET services Web en appliquant l’attribut soit aux interfaces ou aux classes.  
  
- Les méthodes chargées de définir ces interfaces doivent contenir un minimum de code. Faites-les déléguer leur tâche à d'autres classes. De nouveaux types de services WCF pourraient alors également déléguer leur travail de fond à ces classes.  
  
- Fournissez des noms explicites pour les opérations d'un service à l'aide du paramètre `MessageName` de <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Cela est important, car les noms par défaut pour les opérations dans ASP.NET sont différents des noms par défaut fournis par WCF. En fournissant des noms explicites, vous n'avez pas à vous reposer sur les noms par défaut.  
  
- Ne mettez pas en œuvre ASP.NET opérations de service Web avec des méthodes polymorphes, parce que WCF ne prend pas en charge les opérations de mise en œuvre avec des méthodes polymorphes.  
  
- Utilisez le <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> afin de fournir des valeurs explicites pour les en-têtes HTTP SOAPAction chargés d'acheminer les demandes HTTP aux méthodes.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     Adopter cette approche permettra de contourner le fait de pouvoir s’appuyer sur les valeurs SOAPAction par défaut utilisées par ASP.NET et WCF étant les mêmes.  
  
- Évitez l’utilisation des extensions SOAP. Si des extensions SOAP sont nécessaires, déterminez si l’objet pour lequel elles sont considérées est une caractéristique qui est déjà fournie par WCF. Si c’est effectivement le cas, alors réexaminez le choix de ne pas adopter WCF tout de suite.  
  
## <a name="state-management"></a>Gestion des états  
 Évitez de devoir maintenir l'état dans les services. Non seulement le maintien de l’État a tendance à compromettre l’évolutivité d’une application, mais les mécanismes de gestion de l’État de ASP.NET et WCF sont très différents, bien que WCF ne soutenir les mécanismes de ASP.NET en mode ASP.NET compatibilité.  
  
## <a name="exception-handling"></a>Gestion des exceptions  
 Lors de la conception des structures des types de données à envoyer et à recevoir par un service, concevez aussi des structures pour représenter les divers types d'exceptions qui peuvent se produire dans un service et qu'il faut décrire éventuellement à un client.  
  
```csharp  
[Serializable]  
[XmlRoot(Namespace="ExplicitNamespace", IsNullable=true)]  
public partial class AnticipatedException
{
    private string anticipatedExceptionInformationField;  

    public string AnticipatedExceptionInformation
    {  
        get {
            return this.anticipatedExceptionInformationField;  
        }  
        set {  
            this.anticipatedExceptionInformationField = value;  
        }  
    }  
}  
```  
  
 Donnez à ces classes la possibilité de se sérialiser en code XML :  
  
```csharp  
public XmlNode ToXML()  
{  
     XmlSerializer serializer = new XmlSerializer(  
      typeof(AnticipatedException));  
     MemoryStream memoryStream = new MemoryStream();  
     XmlTextWriter writer = new XmlTextWriter(  
     memoryStream, UnicodeEncoding.UTF8);  
     serializer.Serialize(writer, this);  
     XmlDocument document = new XmlDocument();  
     document.LoadXml(new string(  
     UnicodeEncoding.UTF8.GetChars(  
     memoryStream.GetBuffer())).Trim());  
    return document.DocumentElement;  
}  
```  
  
 Ces classes peuvent ensuite servir à fournir les détails pour les instances <xref:System.Web.Services.Protocols.SoapException> levées explicitement :  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 Ces classes d’exception seront facilement réutilisables à la classe WCF <xref:System.ServiceModel.FaultException%601> pour`FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Sécurité  
 Les éléments suivants sont des recommandations de sécurité.  
  
- Éviter d’utiliser ASP.NET 2.0 Profils, car leur utilisation limiterait l’utilisation du mode d’intégration ASP.NET si le service était migré vers WCF.  
  
- Évitez d’utiliser les ACL pour contrôler l’accès aux services, car ASP.NET services Web prend en charge les ARL utilisant les services d’information Internet (IIS), le WCF ne le fait pas, parce que ASP.NET services Web dépendent de l’IIS pour l’hébergement, et WCF n’a pas nécessairement besoin d’être hébergé dans l’IIS.  
  
- Vous pouvez faire appel à des fournisseurs de rôles ASP.NET 2.0 pour autoriser l'accès aux ressources d'un service.  
  
## <a name="see-also"></a>Voir aussi

- [Anticipation de l'adoption de Windows Communication Foundation : faciliter l'intégration future](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
