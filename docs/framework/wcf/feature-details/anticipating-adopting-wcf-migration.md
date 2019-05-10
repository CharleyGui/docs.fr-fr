---
title: 'Anticipation de l’adoption de Windows Communication Foundation : Facilitation de la migration future'
ms.date: 03/30/2017
ms.assetid: f49664d9-e9e0-425c-a259-93f0a569d01b
ms.openlocfilehash: 5e1146806ce631eb5e6795f5d12267138d54785c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592836"
---
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="88c24-102">Anticipation de l’adoption de Windows Communication Foundation : Facilitation de la migration future</span><span class="sxs-lookup"><span data-stu-id="88c24-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="88c24-103">Afin de faciliter une future migration de nouvelles applications ASP.NET vers WCF, suivez les recommandations précédentes ainsi que les recommandations suivantes.</span><span class="sxs-lookup"><span data-stu-id="88c24-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="88c24-104">Protocoles</span><span class="sxs-lookup"><span data-stu-id="88c24-104">Protocols</span></span>  
 <span data-ttu-id="88c24-105">Désactivez la prise en charge d'ASP.NET 2.0 pour SOAP 1.2 :</span><span class="sxs-lookup"><span data-stu-id="88c24-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="88c24-106">Cela est recommandé, car WCF exige que les messages répondant à différents protocoles, tels que SOAP 1.1 et SOAP 1.2, accédez à l’aide de différents points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="88c24-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="88c24-107">Si Web ASP.NET 2.0 service est configuré pour prendre en charge SOAP 1.1 et SOAP 1.2, ce qui est la configuration par défaut, il ne peut pas être migré avant vers un point de terminaison WCF unique à l’adresse originale qui serait certainement être compatible avec l’ensemble du site Web ASP.NET clients existants du service.</span><span class="sxs-lookup"><span data-stu-id="88c24-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="88c24-108">De plus, le choix de SOAP 1.2 au lieu de 1.1 restreint davantage la clientèle du service.</span><span class="sxs-lookup"><span data-stu-id="88c24-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="88c24-109">Développement des services</span><span class="sxs-lookup"><span data-stu-id="88c24-109">Service Development</span></span>  
 <span data-ttu-id="88c24-110">WCF vous permet de définir des contrats de service en appliquant la <xref:System.ServiceModel.ServiceContractAttribute> aux interfaces ou aux classes.</span><span class="sxs-lookup"><span data-stu-id="88c24-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="88c24-111">Il est recommandé d'appliquer l'attribut à une interface plutôt qu'à une classe, afin de créer une définition d'un contrat qui peut être implémenté de différentes façons par un nombre illimité de classes.</span><span class="sxs-lookup"><span data-stu-id="88c24-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="88c24-112">ASP.NET 2.0 prend en charge la possibilité d'appliquer l'attribut <xref:System.Web.Services.WebService> aux interfaces aussi bien qu'aux classes.</span><span class="sxs-lookup"><span data-stu-id="88c24-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="88c24-113">Toutefois, comme indiqué précédemment, ASP.NET 2.0 présente un défaut qui fait que le paramètre Namespace de l'attribut <xref:System.Web.Services.WebService> n'a aucun effet lorsque cet attribut est appliqué à une interface plutôt qu'à une classe.</span><span class="sxs-lookup"><span data-stu-id="88c24-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="88c24-114">Dans la mesure où il est généralement recommandé de modifier l’espace de noms d’un service à partir de la valeur par défaut, `http://tempuri.org`, utilisant le paramètre Namespace de le <xref:System.Web.Services.WebService> attribut, il faut continuer la définition des Services Web ASP.NET en appliquant la <xref:System.ServiceModel.ServiceContractAttribute> attribut aux interfaces ou aux classes.</span><span class="sxs-lookup"><span data-stu-id="88c24-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="88c24-115">Les méthodes chargées de définir ces interfaces doivent contenir un minimum de code.</span><span class="sxs-lookup"><span data-stu-id="88c24-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="88c24-116">Faites-les déléguer leur tâche à d'autres classes.</span><span class="sxs-lookup"><span data-stu-id="88c24-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="88c24-117">Nouveaux types de service WCF peuvent aussi déléguer les tâches importantes à ces classes.</span><span class="sxs-lookup"><span data-stu-id="88c24-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="88c24-118">Fournissez des noms explicites pour les opérations d'un service à l'aide du paramètre `MessageName` de <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="88c24-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="88c24-119">Cela est important, étant donné que les noms par défaut pour les opérations dans ASP.NET sont différents des noms par défaut fournis par WCF.</span><span class="sxs-lookup"><span data-stu-id="88c24-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="88c24-120">En fournissant des noms explicites, vous n'avez pas à vous reposer sur les noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="88c24-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="88c24-121">N’implémentez pas les opérations de service Web ASP.NET avec des méthodes polymorphes, étant donné que WCF ne prend pas en charge l’implémentation des opérations avec des méthodes polymorphes.</span><span class="sxs-lookup"><span data-stu-id="88c24-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="88c24-122">Utilisez le <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> afin de fournir des valeurs explicites pour les en-têtes HTTP SOAPAction chargés d'acheminer les demandes HTTP aux méthodes.</span><span class="sxs-lookup"><span data-stu-id="88c24-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="88c24-123">Cette approche résoudra de devoir compter sur la valeur par défaut des valeurs SOAPAction utilisés par ASP.NET et WCF qui est la même.</span><span class="sxs-lookup"><span data-stu-id="88c24-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="88c24-124">Évitez l’utilisation des extensions SOAP.</span><span class="sxs-lookup"><span data-stu-id="88c24-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="88c24-125">Si les extensions SOAP sont requises, puis déterminez si l’objectif pour lequel ils sont considérés comme est une fonctionnalité qui est déjà fournie par WCF.</span><span class="sxs-lookup"><span data-stu-id="88c24-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="88c24-126">Si tel est effectivement le cas, reconsidérez le choix de ne pas adopter WCF tout de suite.</span><span class="sxs-lookup"><span data-stu-id="88c24-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="88c24-127">Gestion des états</span><span class="sxs-lookup"><span data-stu-id="88c24-127">State Management</span></span>  
 <span data-ttu-id="88c24-128">Évitez de devoir maintenir l'état dans les services.</span><span class="sxs-lookup"><span data-stu-id="88c24-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="88c24-129">Non seulement maintenir l’état ont tendance à compromettre l’évolutivité d’une application, mais les mécanismes de gestion d’état d’ASP.NET et WCF sont très différents, bien que WCF ne prend pas en charge les mécanismes ASP.NET en mode de compatibilité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="88c24-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="88c24-130">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="88c24-130">Exception Handling</span></span>  
 <span data-ttu-id="88c24-131">Lors de la conception des structures des types de données à envoyer et à recevoir par un service, concevez aussi des structures pour représenter les divers types d'exceptions qui peuvent se produire dans un service et qu'il faut décrire éventuellement à un client.</span><span class="sxs-lookup"><span data-stu-id="88c24-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
```csharp  
[Serializable]  
[XmlRoot(  
     Namespace="ExplicitNamespace", IsNullable=true)]  
    public partial class AnticipatedException {  
  
     private string anticipatedExceptionInformationField;  
  
     public string AnticipatedExceptionInformation {  
      get {  
          return this.anticipatedExceptionInformationField;  
          }  
      set {  
          this.anticipatedExceptionInformationField = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="88c24-132">Donnez à ces classes la possibilité de se sérialiser en code XML :</span><span class="sxs-lookup"><span data-stu-id="88c24-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="88c24-133">Ces classes peuvent ensuite servir à fournir les détails pour les instances <xref:System.Web.Services.Protocols.SoapException> levées explicitement :</span><span class="sxs-lookup"><span data-stu-id="88c24-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnctipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="88c24-134">Ces classes d’exceptions sera réutilisables avec WCF <xref:System.ServiceModel.FaultException%601> classe pour lever une nouvelle `FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="88c24-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="88c24-135">Sécurité</span><span class="sxs-lookup"><span data-stu-id="88c24-135">Security</span></span>  
 <span data-ttu-id="88c24-136">Les éléments suivants sont des recommandations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="88c24-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="88c24-137">Éviter à l’aide de profils ASP.NET 2.0, car leur utilisation peut restreindre l’utilisation du Mode intégration ASP.NET si le service a été migré vers WCF.</span><span class="sxs-lookup"><span data-stu-id="88c24-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="88c24-138">Évitez d’utiliser des ACL pour contrôler l’accès aux services, en tant que services Web ASP.NET prend en charge les ACL à l’aide d’Internet Information Services (IIS), n’est pas le cas de WCF, étant donné que les services Web ASP.NET dépendent d’IIS pour l’hébergement et WCF ne doit pas nécessairement être hébergés dans IIS.</span><span class="sxs-lookup"><span data-stu-id="88c24-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="88c24-139">Vous pouvez faire appel à des fournisseurs de rôles ASP.NET 2.0 pour autoriser l'accès aux ressources d'un service.</span><span class="sxs-lookup"><span data-stu-id="88c24-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c24-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88c24-140">See also</span></span>

- [<span data-ttu-id="88c24-141">Anticipation de l’adoption de Windows Communication Foundation : Faciliter l’intégration Future</span><span class="sxs-lookup"><span data-stu-id="88c24-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
