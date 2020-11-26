---
title: 'Anticipation de l’adoption de Windows Communication Foundation : Facilitation de la migration future'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: bf3155f19e42787746d59ce7b593273522e2840a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245053"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a>Anticipation de l’adoption de Windows Communication Foundation : Facilitation de la migration future

Pour garantir une migration future plus facile des nouvelles applications ASP.NET vers WCF, suivez les recommandations ci-dessus, ainsi que les recommandations suivantes.  
  
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
  
 Cela est recommandé, car WCF exige des messages conformes à différents protocoles, tels que SOAP 1,1 et SOAP 1,2, pour accéder à des points de terminaison différents. Si un service Web ASP.NET 2,0 est configuré pour prendre en charge à la fois SOAP 1,1 et SOAP 1,2, qui est la configuration par défaut, il ne peut pas être migré vers un point de terminaison WCF unique à l’adresse d’origine, qui serait certainement compatible avec tous les clients existants du service Web ASP.NET. De plus, le choix de SOAP 1.2 au lieu de 1.1 restreint davantage la clientèle du service.  
  
## <a name="service-development"></a>Développement des services  

 WCF vous permet de définir des contrats de service en appliquant <xref:System.ServiceModel.ServiceContractAttribute> à des interfaces ou à des classes. Il est recommandé d'appliquer l'attribut à une interface plutôt qu'à une classe, afin de créer une définition d'un contrat qui peut être implémenté de différentes façons par un nombre illimité de classes. ASP.NET 2.0 prend en charge la possibilité d'appliquer l'attribut <xref:System.Web.Services.WebService> aux interfaces aussi bien qu'aux classes. Toutefois, comme indiqué précédemment, ASP.NET 2.0 présente un défaut qui fait que le paramètre Namespace de l'attribut <xref:System.Web.Services.WebService> n'a aucun effet lorsque cet attribut est appliqué à une interface plutôt qu'à une classe. Étant donné qu’il est généralement recommandé de modifier l’espace de noms d’un service à partir de la valeur par défaut, `http://tempuri.org` , à l’aide du paramètre d’espace de noms de l' <xref:System.Web.Services.WebService> attribut, vous devez continuer à définir des Services Web ASP.net en appliquant l' <xref:System.ServiceModel.ServiceContractAttribute> attribut à des interfaces ou à des classes.  
  
- Les méthodes chargées de définir ces interfaces doivent contenir un minimum de code. Faites-les déléguer leur tâche à d'autres classes. Les nouveaux types de service WCF peuvent également déléguer leur travail substantiel à ces classes.  
  
- Fournissez des noms explicites pour les opérations d'un service à l'aide du paramètre `MessageName` de <xref:System.Web.Services.WebMethodAttribute>.  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     Cela est important, car les noms par défaut pour les opérations dans ASP.NET sont différents des noms par défaut fournis par WCF. En fournissant des noms explicites, vous n'avez pas à vous reposer sur les noms par défaut.  
  
- N’implémentez pas d’opérations de service Web ASP.NET avec des méthodes polymorphes, car WCF ne prend pas en charge l’implémentation d’opérations avec des méthodes polymorphes.  
  
- Utilisez le <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> afin de fournir des valeurs explicites pour les en-têtes HTTP SOAPAction chargés d'acheminer les demandes HTTP aux méthodes.  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     En adoptant cette approche, vous contenterez d’utiliser les valeurs SOAPAction par défaut utilisées par ASP.NET et WCF comme étant identiques.  
  
- Évitez l’utilisation des extensions SOAP. Si des extensions SOAP sont requises, déterminez si l’objectif pour lequel elles sont prises en compte est une fonctionnalité qui est déjà fournie par WCF. Si c’est effectivement le cas, reconsidérez le choix de ne pas adopter WCF immédiatement.  
  
## <a name="state-management"></a>Gestion des états  

 Évitez de devoir maintenir l'état dans les services. Non seulement la gestion de l’État a tendance à compromettre l’évolutivité d’une application, mais les mécanismes de gestion de l’état de ASP.NET et WCF sont très différents, bien que WCF prenne en charge les mécanismes ASP.NET en mode de compatibilité ASP.NET.  
  
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
  
 Ces classes d’exception seront facilement réutilisables avec la <xref:System.ServiceModel.FaultException%601> classe WCF pour lever une nouvelle `FaultException<AnticipatedException>(anticipatedException);`  
  
## <a name="security"></a>Sécurité  

 Les éléments suivants sont des recommandations de sécurité.  
  
- Évitez d’utiliser des profils ASP.NET 2,0, car leur utilisation limiterait l’utilisation du mode d’intégration ASP.NET si le service a été migré vers WCF.  
  
- Évitez d’utiliser des listes de contrôle d’accès pour contrôler l’accès aux services, car les services Web ASP.NET prennent en charge les ACL à l’aide d’Internet Information Services (IIS), mais pas WCF, car les services Web ASP.NET dépendent d’IIS pour l’hébergement, et WCF ne doit pas nécessairement être hébergé dans IIS.  
  
- Vous pouvez faire appel à des fournisseurs de rôles ASP.NET 2.0 pour autoriser l'accès aux ressources d'un service.  
  
## <a name="see-also"></a>Voir aussi

- [Anticipation de l’adoption de Windows Communication Foundation : Facilitation de l’intégration future](anticipating-adopting-the-wcf-easing-future-integration.md)
