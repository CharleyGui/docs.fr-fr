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
# <a name="anticipating-adopting-the-windows-communication-foundation-easing-future-migration"></a><span data-ttu-id="e96ba-102">Anticipation de l‘adoption de Windows Communication Foundation : faciliter la future migration</span><span class="sxs-lookup"><span data-stu-id="e96ba-102">Anticipating Adopting the Windows Communication Foundation: Easing Future Migration</span></span>
<span data-ttu-id="e96ba-103">Afin d’assurer une migration future plus facile des nouvelles demandes de ASP.NET vers le WCF, suivez les recommandations précédentes ainsi que les recommandations suivantes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-103">To ensure an easier future migration of new ASP.NET applications to WCF, follow the preceding recommendations as well as the following recommendations.</span></span>  
  
## <a name="protocols"></a><span data-ttu-id="e96ba-104">Protocoles</span><span class="sxs-lookup"><span data-stu-id="e96ba-104">Protocols</span></span>  
 <span data-ttu-id="e96ba-105">Désactivez la prise en charge d'ASP.NET 2.0 pour SOAP 1.2 :</span><span class="sxs-lookup"><span data-stu-id="e96ba-105">Disable ASP.NET 2.0’s support for SOAP 1.2:</span></span>  
  
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
  
 <span data-ttu-id="e96ba-106">Cela est conseillé parce que WCF nécessite des messages conformes à différents protocoles, comme SOAP 1.1 et SOAP 1.2, pour aller en utilisant différents critères d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="e96ba-106">Doing so is advisable because WCF requires messages conforming to different protocols, like SOAP 1.1 and SOAP 1.2, to go by using different endpoints.</span></span> <span data-ttu-id="e96ba-107">Si un service Web ASP.NET 2.0 est configuré pour prendre en charge à la fois SOAP 1.1 et SOAP 1.2, qui est la configuration par défaut, alors il ne peut pas être migré vers l’avant vers un seul point de terminaison WCF à l’adresse originale qui serait certainement compatible avec l’ensemble de la ASP.NET Web clients existants du service.</span><span class="sxs-lookup"><span data-stu-id="e96ba-107">If an ASP.NET 2.0 Web service is configured to support both SOAP 1.1 and SOAP 1.2, which is the default configuration, then it cannot be migrated forward to a single WCF endpoint at the original address that would be certainly be compatible with all of the ASP.NET Web service’s existing clients.</span></span> <span data-ttu-id="e96ba-108">De plus, le choix de SOAP 1.2 au lieu de 1.1 restreint davantage la clientèle du service.</span><span class="sxs-lookup"><span data-stu-id="e96ba-108">Also choosing SOAP 1.2 instead of 1.1 will more severely restrict the clientele of the service.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="e96ba-109">Développement des services</span><span class="sxs-lookup"><span data-stu-id="e96ba-109">Service Development</span></span>  
 <span data-ttu-id="e96ba-110">WCF vous permet de définir <xref:System.ServiceModel.ServiceContractAttribute> les contrats de service en appliquant les interfaces ou aux classes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-110">WCF allows you to define service contracts by applying the <xref:System.ServiceModel.ServiceContractAttribute> either to interfaces or to classes.</span></span> <span data-ttu-id="e96ba-111">Il est recommandé d'appliquer l'attribut à une interface plutôt qu'à une classe, afin de créer une définition d'un contrat qui peut être implémenté de différentes façons par un nombre illimité de classes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-111">It is recommended to apply the attribute to an interface rather than to a class, because doing so creates a definition of a contract that can be variously implemented by any number of classes.</span></span> <span data-ttu-id="e96ba-112">ASP.NET 2.0 prend en charge la possibilité d'appliquer l'attribut <xref:System.Web.Services.WebService> aux interfaces aussi bien qu'aux classes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-112">ASP.NET 2.0 supports the option of applying the <xref:System.Web.Services.WebService> attribute to interfaces as well as classes.</span></span> <span data-ttu-id="e96ba-113">Toutefois, comme indiqué précédemment, ASP.NET 2.0 présente un défaut qui fait que le paramètre Namespace de l'attribut <xref:System.Web.Services.WebService> n'a aucun effet lorsque cet attribut est appliqué à une interface plutôt qu'à une classe.</span><span class="sxs-lookup"><span data-stu-id="e96ba-113">However, as mentioned already, there is a defect in ASP.NET 2.0, by which the Namespace parameter of the <xref:System.Web.Services.WebService> attribute has no effect when that attribute is applied to an interface rather than a class.</span></span> <span data-ttu-id="e96ba-114">Comme il est généralement conseillé de modifier l’espace de `http://tempuri.org`nom d’un service <xref:System.Web.Services.WebService> à partir de la valeur par défaut, <xref:System.ServiceModel.ServiceContractAttribute> en utilisant le paramètre Namespace de l’attribut, il faut continuer à définir ASP.NET services Web en appliquant l’attribut soit aux interfaces ou aux classes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-114">Since it is generally advisable to modify the namespace of a service from the default value, `http://tempuri.org`, using the Namespace parameter of the <xref:System.Web.Services.WebService> attribute, one should continue defining ASP.NET Web Services by applying the <xref:System.ServiceModel.ServiceContractAttribute> attribute either to interfaces or to classes.</span></span>  
  
- <span data-ttu-id="e96ba-115">Les méthodes chargées de définir ces interfaces doivent contenir un minimum de code.</span><span class="sxs-lookup"><span data-stu-id="e96ba-115">Have as little code as possible in the methods by which those interfaces are defined.</span></span> <span data-ttu-id="e96ba-116">Faites-les déléguer leur tâche à d'autres classes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-116">Have them delegate their work to other classes.</span></span> <span data-ttu-id="e96ba-117">De nouveaux types de services WCF pourraient alors également déléguer leur travail de fond à ces classes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-117">New WCF service types could then also delegate their substantive work to those classes.</span></span>  
  
- <span data-ttu-id="e96ba-118">Fournissez des noms explicites pour les opérations d'un service à l'aide du paramètre `MessageName` de <xref:System.Web.Services.WebMethodAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e96ba-118">Provide explicit names for the operations of a service using the `MessageName` parameter of the <xref:System.Web.Services.WebMethodAttribute>.</span></span>  
  
    ```csharp  
    [WebMethod(MessageName="ExplicitName")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="e96ba-119">Cela est important, car les noms par défaut pour les opérations dans ASP.NET sont différents des noms par défaut fournis par WCF.</span><span class="sxs-lookup"><span data-stu-id="e96ba-119">Doing so is important, because the default names for operations in ASP.NET are different from the default names supplied by WCF.</span></span> <span data-ttu-id="e96ba-120">En fournissant des noms explicites, vous n'avez pas à vous reposer sur les noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="e96ba-120">By providing explicit names, you avoid relying on the default ones.</span></span>  
  
- <span data-ttu-id="e96ba-121">Ne mettez pas en œuvre ASP.NET opérations de service Web avec des méthodes polymorphes, parce que WCF ne prend pas en charge les opérations de mise en œuvre avec des méthodes polymorphes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-121">Do not implement ASP.NET Web service operations with polymorphic methods, because WCF does not support implementing operations with polymorphic methods.</span></span>  
  
- <span data-ttu-id="e96ba-122">Utilisez le <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> afin de fournir des valeurs explicites pour les en-têtes HTTP SOAPAction chargés d'acheminer les demandes HTTP aux méthodes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-122">Use the <xref:System.Web.Services.Protocols.SoapDocumentMethodAttribute> to provide explicit values for the SOAPAction HTTP headers by which HTTP requests will be routed to methods.</span></span>  
  
    ```csharp  
    [WebMethod]  
    [SoapDocumentMethod(RequestElementName="ExplicitAction")]  
    string Echo(string input);  
    ```  
  
     <span data-ttu-id="e96ba-123">Adopter cette approche permettra de contourner le fait de pouvoir s’appuyer sur les valeurs SOAPAction par défaut utilisées par ASP.NET et WCF étant les mêmes.</span><span class="sxs-lookup"><span data-stu-id="e96ba-123">Taking this approach will circumvent having to rely on the default SOAPAction values used by ASP.NET and WCF being the same.</span></span>  
  
- <span data-ttu-id="e96ba-124">Évitez l’utilisation des extensions SOAP.</span><span class="sxs-lookup"><span data-stu-id="e96ba-124">Avoid using SOAP extensions.</span></span> <span data-ttu-id="e96ba-125">Si des extensions SOAP sont nécessaires, déterminez si l’objet pour lequel elles sont considérées est une caractéristique qui est déjà fournie par WCF.</span><span class="sxs-lookup"><span data-stu-id="e96ba-125">If SOAP extensions are required, then determine whether the purpose for which they are being considered is a feature that is already provided by WCF.</span></span> <span data-ttu-id="e96ba-126">Si c’est effectivement le cas, alors réexaminez le choix de ne pas adopter WCF tout de suite.</span><span class="sxs-lookup"><span data-stu-id="e96ba-126">If that is indeed the case, then reconsider the choice to not adopt WCF right away.</span></span>  
  
## <a name="state-management"></a><span data-ttu-id="e96ba-127">Gestion des états</span><span class="sxs-lookup"><span data-stu-id="e96ba-127">State Management</span></span>  
 <span data-ttu-id="e96ba-128">Évitez de devoir maintenir l'état dans les services.</span><span class="sxs-lookup"><span data-stu-id="e96ba-128">Avoid having to maintain state in services.</span></span> <span data-ttu-id="e96ba-129">Non seulement le maintien de l’État a tendance à compromettre l’évolutivité d’une application, mais les mécanismes de gestion de l’État de ASP.NET et WCF sont très différents, bien que WCF ne soutenir les mécanismes de ASP.NET en mode ASP.NET compatibilité.</span><span class="sxs-lookup"><span data-stu-id="e96ba-129">Not only does maintaining state tend to compromise the scalability of an application, but the state management mechanisms of ASP.NET and WCF are very different, although WCF does support the ASP.NET mechanisms in ASP.NET compatibility mode.</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="e96ba-130">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="e96ba-130">Exception Handling</span></span>  
 <span data-ttu-id="e96ba-131">Lors de la conception des structures des types de données à envoyer et à recevoir par un service, concevez aussi des structures pour représenter les divers types d'exceptions qui peuvent se produire dans un service et qu'il faut décrire éventuellement à un client.</span><span class="sxs-lookup"><span data-stu-id="e96ba-131">In designing the structures of the data types to be sent and received by a service, also design structures to represent the various types of exceptions that might occur within a service that one might wish to convey to a client.</span></span>  
  
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
  
 <span data-ttu-id="e96ba-132">Donnez à ces classes la possibilité de se sérialiser en code XML :</span><span class="sxs-lookup"><span data-stu-id="e96ba-132">Give such classes the ability to serialize themselves to XML:</span></span>  
  
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
  
 <span data-ttu-id="e96ba-133">Ces classes peuvent ensuite servir à fournir les détails pour les instances <xref:System.Web.Services.Protocols.SoapException> levées explicitement :</span><span class="sxs-lookup"><span data-stu-id="e96ba-133">The classes can then be used to provide the details for explicitly thrown <xref:System.Web.Services.Protocols.SoapException> instances:</span></span>  
  
```csharp  
AnticipatedException exception = new AnticipatedException();  
exception.AnticipatedExceptionInformation = "…";  
throw new SoapException(  
     "Fault occurred",  
     SoapException.ClientFaultCode,  
     Context.Request.Url.AbsoluteUri,  
     exception.ToXML());  
```  
  
 <span data-ttu-id="e96ba-134">Ces classes d’exception seront facilement réutilisables à la classe WCF <xref:System.ServiceModel.FaultException%601> pour`FaultException<AnticipatedException>(anticipatedException);`</span><span class="sxs-lookup"><span data-stu-id="e96ba-134">These exception classes will be readily reusable with the WCF <xref:System.ServiceModel.FaultException%601> class to throw a new `FaultException<AnticipatedException>(anticipatedException);`</span></span>  
  
## <a name="security"></a><span data-ttu-id="e96ba-135">Sécurité</span><span class="sxs-lookup"><span data-stu-id="e96ba-135">Security</span></span>  
 <span data-ttu-id="e96ba-136">Les éléments suivants sont des recommandations de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e96ba-136">The following are some security recommendations.</span></span>  
  
- <span data-ttu-id="e96ba-137">Éviter d’utiliser ASP.NET 2.0 Profils, car leur utilisation limiterait l’utilisation du mode d’intégration ASP.NET si le service était migré vers WCF.</span><span class="sxs-lookup"><span data-stu-id="e96ba-137">Avoid using ASP.NET 2.0 Profiles, as using them would restrict the use of ASP.NET Integration Mode if the service was migrated to WCF.</span></span>  
  
- <span data-ttu-id="e96ba-138">Évitez d’utiliser les ACL pour contrôler l’accès aux services, car ASP.NET services Web prend en charge les ARL utilisant les services d’information Internet (IIS), le WCF ne le fait pas, parce que ASP.NET services Web dépendent de l’IIS pour l’hébergement, et WCF n’a pas nécessairement besoin d’être hébergé dans l’IIS.</span><span class="sxs-lookup"><span data-stu-id="e96ba-138">Avoid using ACLs to control access to services, as ASP.NET Web services supports ACLs using Internet Information Services (IIS), WCF does not—because ASP.NET Web services depend on IIS for hosting, and WCF does not necessarily have to be hosted in IIS.</span></span>  
  
- <span data-ttu-id="e96ba-139">Vous pouvez faire appel à des fournisseurs de rôles ASP.NET 2.0 pour autoriser l'accès aux ressources d'un service.</span><span class="sxs-lookup"><span data-stu-id="e96ba-139">Do consider using ASP.NET 2.0 Role Providers for authorizing access to the resources of a service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e96ba-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e96ba-140">See also</span></span>

- [<span data-ttu-id="e96ba-141">Anticipation de l'adoption de Windows Communication Foundation : faciliter l'intégration future</span><span class="sxs-lookup"><span data-stu-id="e96ba-141">Anticipating Adopting the Windows Communication Foundation: Easing Future Integration</span></span>](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
