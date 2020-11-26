---
title: Gestion des erreurs HTTP Web WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: cfbf98c69370764a9526c32459d43521177476e3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239027"
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="01b88-102">Gestion des erreurs HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="01b88-102">WCF Web HTTP Error Handling</span></span>

<span data-ttu-id="01b88-103">La gestion des erreurs HTTP Web Windows Communication Foundation (WCF) vous permet de retourner des erreurs à partir des services HTTP Web WCF qui spécifient un code d’état HTTP et retournent des détails d’erreur en utilisant le même format que l’opération (par exemple, XML ou JSON).</span><span class="sxs-lookup"><span data-stu-id="01b88-103">Windows Communication Foundation (WCF) Web HTTP error handling enables you to return errors from WCF Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="01b88-104">Gestion des erreurs HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="01b88-104">WCF Web HTTP Error Handling</span></span>  

 <span data-ttu-id="01b88-105">La classe <xref:System.ServiceModel.Web.WebFaultException> définit un constructeur qui vous permet de spécifier un code d'état HTTP.</span><span class="sxs-lookup"><span data-stu-id="01b88-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="01b88-106">Ce code d'état est alors retourné au client.</span><span class="sxs-lookup"><span data-stu-id="01b88-106">This status code is then returned to the client.</span></span> <span data-ttu-id="01b88-107">Une version générique de la classe <xref:System.ServiceModel.Web.WebFaultException>, <xref:System.ServiceModel.Web.WebFaultException%601>, vous permet de retourner un type défini par l'utilisateur contenant des informations sur l'erreur qui s'est produite.</span><span class="sxs-lookup"><span data-stu-id="01b88-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="01b88-108">Cet objet personnalisé est sérialisé à l'aide du format spécifié par l'opération et retourné au client.</span><span class="sxs-lookup"><span data-stu-id="01b88-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="01b88-109">L'exemple suivant indique comment retourner un code d'état HTTP.</span><span class="sxs-lookup"><span data-stu-id="01b88-109">The following example shows how to return an HTTP status code.</span></span>  
  
```csharp
public string Operation1()
{
    // Operation logic  
   // ...
   throw new WebFaultException(HttpStatusCode.Forbidden);
}  
```  
  
 <span data-ttu-id="01b88-110">L'exemple suivant montre comment retourner un code d'état HTTP et une information supplémentaire dans un type défini par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01b88-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="01b88-111">`MyErrorDetail` est un type défini par l'utilisateur qui contient des informations supplémentaires à propos de l'erreur qui s'est produite.</span><span class="sxs-lookup"><span data-stu-id="01b88-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```csharp
public string Operation2()
{
   // Operation logic  
   // ...
   MyErrorDetail detail = new MyErrorDetail()
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="01b88-112">Le code précédent retourne une réponse HTTP avec le code d'état interdit et un corps qui contient une instance de l'objet `MyErrorDetails`.</span><span class="sxs-lookup"><span data-stu-id="01b88-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="01b88-113">Le format de l'objet `MyErrorDetails` est déterminé par :</span><span class="sxs-lookup"><span data-stu-id="01b88-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
- <span data-ttu-id="01b88-114">la valeur du paramètre `ResponseFormat` de l'attribut <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> spécifié sur l'opération de service ;</span><span class="sxs-lookup"><span data-stu-id="01b88-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
- <span data-ttu-id="01b88-115">la valeur de la propriété <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> ;</span><span class="sxs-lookup"><span data-stu-id="01b88-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
- <span data-ttu-id="01b88-116">la valeur de la propriété <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> en accédant à l'objet <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span><span class="sxs-lookup"><span data-stu-id="01b88-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 <span data-ttu-id="01b88-117">Pour plus d’informations sur la façon dont ces valeurs affectent la mise en forme de l’opération, consultez [mise en forme http Web WCF](wcf-web-http-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="01b88-117">For more information about how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="01b88-118"><xref:System.ServiceModel.Web.WebFaultException> est un <xref:System.ServiceModel.FaultException> et par conséquent peut être utilisé comme le modèle de programmation d'exception d'erreur pour les services qui exposent des points de terminaison SOAP, ainsi que des points de terminaison HTTP Web.</span><span class="sxs-lookup"><span data-stu-id="01b88-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b88-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01b88-119">See also</span></span>

- [<span data-ttu-id="01b88-120">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="01b88-120">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="01b88-121">Mise en forme HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="01b88-121">WCF Web HTTP Formatting</span></span>](wcf-web-http-formatting.md)
- [<span data-ttu-id="01b88-122">Définition et spécification des erreurs</span><span class="sxs-lookup"><span data-stu-id="01b88-122">Defining and Specifying Faults</span></span>](../defining-and-specifying-faults.md)
- [<span data-ttu-id="01b88-123">Gestion des exceptions et des erreurs</span><span class="sxs-lookup"><span data-stu-id="01b88-123">Handling Exceptions and Faults</span></span>](../extending/handling-exceptions-and-faults.md)
- [<span data-ttu-id="01b88-124">Envoi et réception des erreurs</span><span class="sxs-lookup"><span data-stu-id="01b88-124">Sending and Receiving Faults</span></span>](../sending-and-receiving-faults.md)
