---
title: 'Comment : configurer un client WCF pour interagir avec les services WSE 3.0'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3dadd7f1-d207-4ea5-a73b-3e8aa44407f8
ms.openlocfilehash: 7dd50fcc07c6c090042cf87acb4aa5d2b5321a68
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579577"
---
# <a name="how-to-configure-a-wcf-client-to-interoperate-with-wse30-services"></a><span data-ttu-id="a8a18-102">Comment : configurer un client WCF pour interagir avec les services WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="a8a18-102">How to: Configure a WCF Client to interoperate with WSE3.0 Services</span></span>
<span data-ttu-id="a8a18-103">Les clients Windows Communication Foundation (WCF) sont compatibles au niveau du câble avec les services Web Services Enhancements 3,0 for Microsoft .NET (WSE) lorsque les clients WCF sont configurés pour utiliser la version du 2004 d’août de la spécification WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="a8a18-103">Windows Communication Foundation (WCF) clients are wire-level compatible with Web Services Enhancements 3.0 for Microsoft .NET (WSE) services when WCF clients are configured to use the August 2004 version of the WS-Addressing specification.</span></span>  
  
### <a name="to-configure-a-wcf-client-to-interoperate-with-a-wse-30-web-service"></a><span data-ttu-id="a8a18-104">Configurer un client WCF pour interagir avec un service Web WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="a8a18-104">To configure a WCF client to interoperate with a WSE 3.0 Web service</span></span>  
  
1. <span data-ttu-id="a8a18-105">Exécutez l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un client WCF pour le service Web WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="a8a18-105">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a WCF client for the WSE 3.0 Web service.</span></span>  
  
     <span data-ttu-id="a8a18-106">Pour un service Web WSE, une classe de client WCF est créée.</span><span class="sxs-lookup"><span data-stu-id="a8a18-106">For a WSE Web service, a WCF client class is created.</span></span>  
  
     <span data-ttu-id="a8a18-107">Pour plus d’informations sur la création d’un client WCF, consultez la rubrique [Comment : créer un client](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="a8a18-107">For details about creating a WCF client, see the [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="a8a18-108">Créez une classe qui représente une liaison pouvant communiquer avec les services Web WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="a8a18-108">Create a class that represents a binding that can communicate with WSE 3.0 Web services.</span></span>  
  
     <span data-ttu-id="a8a18-109">La classe suivante fait partie de l’exemple [interopérabilité avec WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) .</span><span class="sxs-lookup"><span data-stu-id="a8a18-109">The following class is part of the [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) sample.</span></span>  
  
    1. <span data-ttu-id="a8a18-110">Créez une classe qui dérive de la classe <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="a8a18-110">Create a class that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         <span data-ttu-id="a8a18-111">L'exemple de code suivant crée une classe nommée `WseHttpBinding` qui dérive de la classe <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="a8a18-111">The following code example creates a class named `WseHttpBinding` that derives from the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. <span data-ttu-id="a8a18-112">Ajoutez à la classe des propriétés spécifiant l'assertion clé en main WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises, et les paramètres de protection des messages.</span><span class="sxs-lookup"><span data-stu-id="a8a18-112">Add properties to the class that specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings.</span></span>  
  
         <span data-ttu-id="a8a18-113">L’exemple de code suivant définit `SecurityAssertion` les `RequireDerivedKeys` Propriétés,, `EstablishSecurityContext` et `MessageProtectionOrder` .</span><span class="sxs-lookup"><span data-stu-id="a8a18-113">The following code example defines the `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext`, and `MessageProtectionOrder` properties.</span></span> <span data-ttu-id="a8a18-114">Ils spécifient l’assertion clé en main WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises et les paramètres de protection des messages, respectivement.</span><span class="sxs-lookup"><span data-stu-id="a8a18-114">They specify the WSE turnkey assertion, whether derived keys are required, whether secure sessions are used, whether signature confirmations are required, and the message protection settings, respectively.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. <span data-ttu-id="a8a18-115">Substituez la méthode <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> pour définir les propriétés de la liaison.</span><span class="sxs-lookup"><span data-stu-id="a8a18-115">Override the <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> method to set the binding properties.</span></span>  
  
         <span data-ttu-id="a8a18-116">L'exemple de code suivant spécifie le transport, l'encodage de message et les paramètres de protection des messages en obtenant les valeurs des propriétés `SecurityAssertion` et `MessageProtectionOrder`.</span><span class="sxs-lookup"><span data-stu-id="a8a18-116">The following code example specifies the transport, message encoding, and message protection settings by getting the values of the `SecurityAssertion` and `MessageProtectionOrder` properties.</span></span>  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. <span data-ttu-id="a8a18-117">Dans le code d’application cliente, ajoutez le code pour définir les propriétés de la liaison.</span><span class="sxs-lookup"><span data-stu-id="a8a18-117">In the client application code, add code to set the binding properties.</span></span>  
  
     <span data-ttu-id="a8a18-118">L’exemple de code suivant spécifie que le client WCF doit utiliser la protection des messages et l’authentification comme défini par l' `AnonymousForCertificate` assertion de sécurité clé en main WSE 3,0.</span><span class="sxs-lookup"><span data-stu-id="a8a18-118">The following code example specifies that the WCF client must use message protection and authentication as defined by the WSE 3.0 `AnonymousForCertificate` turnkey security assertion.</span></span> <span data-ttu-id="a8a18-119">En outre, des sessions sécurisées et des clés dérivées sont requises.</span><span class="sxs-lookup"><span data-stu-id="a8a18-119">Additionally, secure sessions and derived keys are required.</span></span>  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="a8a18-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="a8a18-120">Example</span></span>  
 <span data-ttu-id="a8a18-121">L'exemple de code suivant définit une liaison personnalisée qui expose des propriétés correspondant à celles d'une assertion de sécurité clé en main WSE 3.0.</span><span class="sxs-lookup"><span data-stu-id="a8a18-121">The following code example defines a custom binding that exposes properties that correspond to the properties of a WSE 3.0 turnkey security assertion.</span></span> <span data-ttu-id="a8a18-122">La liaison personnalisée, qui est nommée `WseHttpBinding` , est ensuite utilisée pour spécifier les propriétés de liaison d’un client WCF.</span><span class="sxs-lookup"><span data-stu-id="a8a18-122">The custom binding, which is named `WseHttpBinding`, is then used to specify the binding properties for a WCF client.</span></span>  

[!code-csharp[c_WCFClientToWSEService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#0)]
[!code-vb[c_WCFClientToWSEService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="a8a18-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8a18-123">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- [<span data-ttu-id="a8a18-124">Interoperating with WSE</span><span class="sxs-lookup"><span data-stu-id="a8a18-124">Interoperating with WSE</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
