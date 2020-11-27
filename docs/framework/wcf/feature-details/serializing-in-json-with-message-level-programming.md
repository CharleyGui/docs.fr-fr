---
title: Sérialisation dans JSON avec programmation de niveau message
ms.date: 03/30/2017
ms.assetid: 5f940ba2-57ee-4c49-a779-957c5e7e71fa
ms.openlocfilehash: 8343f7a8aa3c01557aae7df420351fa318cbb4b5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253932"
---
# <a name="serializing-in-json-with-message-level-programming"></a><span data-ttu-id="ed5c3-102">Sérialisation dans JSON avec programmation de niveau message</span><span class="sxs-lookup"><span data-stu-id="ed5c3-102">Serializing in Json with Message Level Programming</span></span>

<span data-ttu-id="ed5c3-103">WCF prend en charge la sérialisation des données au format JSON.</span><span class="sxs-lookup"><span data-stu-id="ed5c3-103">WCF supports serializing data in JSON format.</span></span> <span data-ttu-id="ed5c3-104">Cette rubrique explique comment indiquer à WCF de sérialiser vos types à l'aide de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ed5c3-104">This topic describes how to tell WCF to serialize your types using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="typed-message-programming"></a><span data-ttu-id="ed5c3-105">Programmation de message typé</span><span class="sxs-lookup"><span data-stu-id="ed5c3-105">Typed Message Programming</span></span>  

 <span data-ttu-id="ed5c3-106"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> est utilisé lorsque <xref:System.ServiceModel.Web.WebGetAttribute> ou <xref:System.ServiceModel.Web.WebInvokeAttribute> est appliqué à une opération de service.</span><span class="sxs-lookup"><span data-stu-id="ed5c3-106">The <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> is used when the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute> is applied to a service operation.</span></span> <span data-ttu-id="ed5c3-107">Les deux attributs vous permettent de spécifier `RequestFormat` et `ResponseFormat`.</span><span class="sxs-lookup"><span data-stu-id="ed5c3-107">Both of these attributes allow you to specify the `RequestFormat` and `ResponseFormat`.</span></span> <span data-ttu-id="ed5c3-108">Pour utiliser JSON pour les demandes et les réponses.</span><span class="sxs-lookup"><span data-stu-id="ed5c3-108">To use JSON for requests and responses.</span></span> <span data-ttu-id="ed5c3-109">Définissez les deux sur `WebMessageFormat.Json` .</span><span class="sxs-lookup"><span data-stu-id="ed5c3-109">set both of these to `WebMessageFormat.Json`.</span></span>  <span data-ttu-id="ed5c3-110">Pour utiliser JSON, vous devez utiliser le <xref:System.ServiceModel.WebHttpBinding> , qui configure automatiquement le <xref:System.ServiceModel.Description.WebHttpBehavior> .</span><span class="sxs-lookup"><span data-stu-id="ed5c3-110">In order to use JSON, you must use the <xref:System.ServiceModel.WebHttpBinding>, which automatically configures the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span> <span data-ttu-id="ed5c3-111">Pour plus d’informations sur la sérialisation WCF, consultez [sérialisation et désérialisation](serialization-and-deserialization.md).</span><span class="sxs-lookup"><span data-stu-id="ed5c3-111">For more information about WCF serialization, see [Serialization and Deserialization](serialization-and-deserialization.md).</span></span> <span data-ttu-id="ed5c3-112">Pour plus d’informations sur JSON et WCF, consultez [station de service-introduction aux services RESTful avec WCF](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).</span><span class="sxs-lookup"><span data-stu-id="ed5c3-112">For more information about JSON and WCF, see [Service Station - An Introduction To RESTful Services With WCF](/archive/msdn-magazine/2009/january/service-station-an-introduction-to-restful-services-with-wcf).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ed5c3-113">L'utilisation de JSON requiert l'utilisation de <xref:System.ServiceModel.WebHttpBinding> et <xref:System.ServiceModel.Description.WebHttpBehavior> qui ne prennent pas en charge la communication SOAP.</span><span class="sxs-lookup"><span data-stu-id="ed5c3-113">Using JSON requires use of <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> which do not support SOAP communication.</span></span> <span data-ttu-id="ed5c3-114">Les services qui communiquent avec <xref:System.ServiceModel.WebHttpBinding> ne prennent pas en charge l’exposition des métadonnées de service. ainsi, vous ne pourrez pas utiliser les fonctionnalités de ajouter une référence de service de Visual Studio ou l’outil de ligne de commande Svcutil pour générer un proxy côté client.</span><span class="sxs-lookup"><span data-stu-id="ed5c3-114">Services that communicate with the <xref:System.ServiceModel.WebHttpBinding> do not support exposing service metadata so you will not be able to use Visual Studio’s Add Service Reference functionality or the svcutil command-line tool to generate a client-side proxy.</span></span> <span data-ttu-id="ed5c3-115">Pour plus d’informations sur la façon dont vous pouvez appeler par programmation des services qui utilisent <xref:System.ServiceModel.WebHttpBinding> , consultez [comment utiliser les services REST avec WCF](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).</span><span class="sxs-lookup"><span data-stu-id="ed5c3-115">For more information how you can programmatically call services that use <xref:System.ServiceModel.WebHttpBinding>, see [How to Consume REST Services with WCF](/archive/blogs/pedram/how-to-consume-rest-services-with-wcf).</span></span>  
  
## <a name="untyped-message-programming"></a><span data-ttu-id="ed5c3-116">Programmation de message non typé</span><span class="sxs-lookup"><span data-stu-id="ed5c3-116">Untyped Message Programming</span></span>  

 <span data-ttu-id="ed5c3-117">Lorsque utilisez directement des objets du message non typé, vous devez définir explicitement les propriétés sur le message non typé pour le sérialiser comme JSON.</span><span class="sxs-lookup"><span data-stu-id="ed5c3-117">When working directly with untyped Message objects, you must explicitly set the properties on the untyped message to serialize it as JSON.</span></span> <span data-ttu-id="ed5c3-118">L'extrait de code suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="ed5c3-118">The following code snippet shows how to do this.</span></span>  
  
```csharp
 Message response = Message.CreateMessage(  
                  MessageVersion.None,    // No SOAP message version  
                             "*",                     // SOAP action, ignored since this is JSON  
                             "Response string: JSON format specified", // Message body  
                             new DataContractJsonSerializer(typeof(string))); // Specify DataContractJsonSerializer  
      response.Properties.Add( WebBodyFormatMessageProperty.Name,
                    new WebBodyFormatMessageProperty(WebContentFormat.Json)); // Use JSON format  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed5c3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed5c3-119">See also</span></span>

- [<span data-ttu-id="ed5c3-120">Intégration d'AJAX et prise en charge de JSON</span><span class="sxs-lookup"><span data-stu-id="ed5c3-120">AJAX Integration and JSON Support</span></span>](ajax-integration-and-json-support.md)
- [<span data-ttu-id="ed5c3-121">Sérialisation JSON autonome</span><span class="sxs-lookup"><span data-stu-id="ed5c3-121">Stand-Alone JSON Serialization</span></span>](stand-alone-json-serialization.md)
- [<span data-ttu-id="ed5c3-122">Sérialisation JSON</span><span class="sxs-lookup"><span data-stu-id="ed5c3-122">JSON Serialization</span></span>](../samples/json-serialization.md)
