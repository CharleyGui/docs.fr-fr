---
title: Interopérabilité avec les services Web ASP.NET
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: f2f1a8fd2bf34ff61784f2dcb88c0669585da573
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67026020"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="edcfe-102">Interopérabilité avec les services Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="edcfe-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="edcfe-103">L’interopérabilité entre les services Web ASP.NET et des services Web de Windows Communication Foundation (WCF) peut être obtenue en s’assurant que les services implémentés à l’aide de ces deux technologies sont conformes à la norme WS-I Basic Profile 1.1 spécification.</span><span class="sxs-lookup"><span data-stu-id="edcfe-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="edcfe-104">Les services Web ASP.NET qui se conforment à WS-I Basic Profile 1.1 sont interopérables avec les clients WCF à l’aide de liaison fournie par le système WCF, <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="edcfe-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="edcfe-105">Utiliser l’option d’ASP.NET 2.0 de l’ajout du <xref:System.Web.Services.WebService> et <xref:System.Web.Services.WebMethodAttribute> attributs à une interface plutôt qu’à une classe et écrivez une classe pour implémenter l’interface, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="edcfe-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="edcfe-106">L'utilisation de cette option est recommandée, car l'interface avec l'attribut <xref:System.Web.Services.WebService> constitue un contrat pour les opérations exécutées par le service qui peut être réutilisé avec différentes classes, qui peuvent implémenter ce même contrat de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="edcfe-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="edcfe-107">Évitez d'utiliser l'attribut <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> pour router des messages vers des méthodes basées sur le nom qualifié complet de l'élément de corps du message SOAP plutôt que l'en-tête HTTP `SOAPAction`.</span><span class="sxs-lookup"><span data-stu-id="edcfe-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="edcfe-108">WCF utilise le `SOAPAction` en-tête HTTP pour le routage des messages.</span><span class="sxs-lookup"><span data-stu-id="edcfe-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="edcfe-109">Le XML dans lequel <xref:System.Xml.Serialization.XmlSerializer> sérialise un type par défaut est sémantiquement identique au XML dans lequel <xref:System.Runtime.Serialization.DataContractSerializer> sérialise un type, à condition que l'espace de noms du XML soit défini explicitement.</span><span class="sxs-lookup"><span data-stu-id="edcfe-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="edcfe-110">Lorsque vous définissez un type de données pour une utilisation avec les services ASP.NETWeb en prévision d’adoption de WCF, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="edcfe-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="edcfe-111">Définissez le type à l'aide des classes .NET Framework plutôt que XML Schema.</span><span class="sxs-lookup"><span data-stu-id="edcfe-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="edcfe-112">Ajoutez uniquement <xref:System.SerializableAttribute> et <xref:System.Xml.Serialization.XmlRootAttribute> à la classe, en utilisant ce dernier pour définir explicitement l'espace de noms du type.</span><span class="sxs-lookup"><span data-stu-id="edcfe-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="edcfe-113">N'ajoutez pas d'attribut supplémentaire à partir de l'espace de noms <xref:System.Xml.Serialization> pour contrôler la manière dont la classe .NET Framework sera traduite dans XML.</span><span class="sxs-lookup"><span data-stu-id="edcfe-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="edcfe-114">En adoptant cette approche, vous devez être en mesure de créer ultérieurement les classes .NET dans des contrats de données avec l'ajout de <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> sans modifier de manière significative le XML dans lequel les classes sont sérialisées pour la transmission.</span><span class="sxs-lookup"><span data-stu-id="edcfe-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="edcfe-115">Les types utilisés dans les messages par les services Web ASP.NET peuvent être traitées comme des contrats de données par les applications WCF, offrant, entre autres avantages, de meilleures performances dans les applications WCF.</span><span class="sxs-lookup"><span data-stu-id="edcfe-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="edcfe-116">Évitez d'utiliser les options d'authentification fournies par des services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="edcfe-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="edcfe-117">Les clients WCF ne prennent pas en charge les.</span><span class="sxs-lookup"><span data-stu-id="edcfe-117">WCF clients do not support them.</span></span> <span data-ttu-id="edcfe-118">Si un service doit être sécurisé, utilisez les options fournies par WCF, car ces options sont fiables et sont basées sur des protocoles standard.</span><span class="sxs-lookup"><span data-stu-id="edcfe-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="edcfe-119">Impact sur les performances causé par le chargement de ServiceModel HttpModule</span><span class="sxs-lookup"><span data-stu-id="edcfe-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="edcfe-120">Dans le .NET Framework 3.0, `HttpModule` WCF a été installé dans le fichier Web.config racine pour que chaque application ASP.NET soit compatible WCF.</span><span class="sxs-lookup"><span data-stu-id="edcfe-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="edcfe-121">Cela peut affecter les performances, vous pouvez donc supprimer  `ServiceModel` pour le fichier Web.config comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="edcfe-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
<httpModules/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="edcfe-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edcfe-122">See also</span></span>

- [<span data-ttu-id="edcfe-123">Guide pratique pour Configurer le Service WCF pour interagir avec les Clients de Service Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="edcfe-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
