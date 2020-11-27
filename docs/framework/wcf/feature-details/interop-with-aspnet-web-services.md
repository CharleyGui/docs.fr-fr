---
title: Interopérabilité avec les services Web ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: cca4e1b3da26d8026d41d0a7107432cdd2960545
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276631"
---
# <a name="interoperability-with-aspnet-web-services"></a>Interopérabilité avec les services Web ASP.NET

L’interopérabilité entre les services Web ASP.NET et les services Web de l’Windows Communication Foundation (WCF) peut être obtenue en veillant à ce que les services implémentés à l’aide des deux technologies soient conformes à la spécification WS-I Basic Profile 1,1. Les services Web ASP.NET qui se conforment à WS-I Basic Profile 1,1 sont interopérables avec les clients WCF à l’aide de la liaison fournie par le système WCF <xref:System.ServiceModel.BasicHttpBinding> .  
  
 Utilisez l’option ASP.NET 2,0 pour ajouter <xref:System.Web.Services.WebService> les <xref:System.Web.Services.WebMethodAttribute> attributs et à une interface plutôt qu’à une classe, et écrire une classe pour implémenter l’interface, comme indiqué dans l’exemple de code suivant.  
  
```csharp
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 L'utilisation de cette option est recommandée, car l'interface avec l'attribut <xref:System.Web.Services.WebService> constitue un contrat pour les opérations exécutées par le service qui peut être réutilisé avec différentes classes, qui peuvent implémenter ce même contrat de différentes façons.  
  
 Évitez d'utiliser l'attribut <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> pour router des messages vers des méthodes basées sur le nom qualifié complet de l'élément de corps du message SOAP plutôt que l'en-tête HTTP `SOAPAction`. WCF utilise l' `SOAPAction` en-tête HTTP pour le routage des messages.  
  
 Le XML dans lequel <xref:System.Xml.Serialization.XmlSerializer> sérialise un type par défaut est sémantiquement identique au XML dans lequel <xref:System.Runtime.Serialization.DataContractSerializer> sérialise un type, à condition que l'espace de noms du XML soit défini explicitement. Lors de la définition d’un type de données à utiliser avec les services ASP. NETWeb en prévision de l’adoption de WCF, procédez comme suit :  
  
- Définissez le type à l'aide des classes .NET Framework plutôt que XML Schema.  
  
- Ajoutez uniquement <xref:System.SerializableAttribute> et <xref:System.Xml.Serialization.XmlRootAttribute> à la classe, en utilisant ce dernier pour définir explicitement l'espace de noms du type. N'ajoutez pas d'attribut supplémentaire à partir de l'espace de noms <xref:System.Xml.Serialization> pour contrôler la manière dont la classe .NET Framework sera traduite dans XML.  
  
- En adoptant cette approche, vous devez être en mesure de créer ultérieurement les classes .NET dans des contrats de données avec l'ajout de <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> sans modifier de manière significative le XML dans lequel les classes sont sérialisées pour la transmission. Les types utilisés dans les messages par les services Web ASP.NET peuvent être traités comme des contrats de données par les applications WCF, ce qui donne, entre autres avantages, de meilleures performances dans les applications WCF.  
  
 Évitez d'utiliser les options d'authentification fournies par des services IIS (Internet Information Services). Les clients WCF ne les prennent pas en charge. Si un service doit être sécurisé, utilisez les options fournies par WCF, car ces options sont robustes et sont basées sur des protocoles standard.  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a>Impact sur les performances causé par le chargement de ServiceModel HttpModule  

 Dans le .NET Framework 3.0, `HttpModule` WCF a été installé dans le fichier Web.config racine pour que chaque application ASP.NET soit compatible WCF. Cela peut affecter les performances, vous pouvez donc supprimer  `ServiceModel` pour le fichier Web.config comme illustré dans l'exemple suivant.  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : configurer le service WCF pour interagir avec des clients de services web ASP.NET](config-wcf-service-with-aspnet-web-service.md)
