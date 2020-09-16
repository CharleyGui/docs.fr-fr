---
title: Création de services pouvant interagir avec le profil Basic Profile 1.1 de WS-I
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- configuration [WCF], interoperable services
ms.assetid: 91b70a21-8f5c-4679-808c-2ed5fa6b2013
ms.openlocfilehash: 5fc29432bdd55daff2d60d641a4cea4925278032
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543015"
---
# <a name="creating-ws-i-basic-profile-11-interoperable-services"></a><span data-ttu-id="c2abd-102">Création de services pouvant interagir avec le profil Basic Profile 1.1 de WS-I</span><span class="sxs-lookup"><span data-stu-id="c2abd-102">Creating WS-I Basic Profile 1.1 Interoperable Services</span></span>
<span data-ttu-id="c2abd-103">Pour configurer un point de terminaison de service WCF pour qu’il puisse être interopérable avec les clients de service Web ASP.NET :</span><span class="sxs-lookup"><span data-stu-id="c2abd-103">To configure a WCF service endpoint to be interoperable with ASP.NET Web service clients:</span></span>  
  
- <span data-ttu-id="c2abd-104">Utilisez le type <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> comme type de liaison pour votre point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="c2abd-104">Use the <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> type as the binding type for your service endpoint.</span></span>  
  
- <span data-ttu-id="c2abd-105">N'utilisez pas les fonctionnalités de rappel et de contrat de session, ni les comportements de transaction sur votre point de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="c2abd-105">Do not use callback and session contract features or transaction behaviors on your service endpoint</span></span>  
  
<span data-ttu-id="c2abd-106">Vous pouvez éventuellement activer la prise en charge du protocole HTTPS et de l'authentification du client au niveau du transport sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="c2abd-106">You can optionally enable support for HTTPS and transport-level client authentication on the binding.</span></span>  
  
<span data-ttu-id="c2abd-107">Les fonctionnalités suivantes de la classe <xref:System.ServiceModel.BasicHttpBinding> requièrent des fonctionnalités qui dépassent le profil Basic Profile 1.1 de WS-I :</span><span class="sxs-lookup"><span data-stu-id="c2abd-107">The following features of the <xref:System.ServiceModel.BasicHttpBinding> class require functionality beyond WS-I Basic Profile 1.1:</span></span>  
  
- <span data-ttu-id="c2abd-108">Encodage des messages MTOM (Message Transmission Optimisation Mechanism) contrôlé par la propriété <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c2abd-108">Message Transmission Optimization Mechanism (MTOM) message encoding controlled by the <xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="c2abd-109">Conservez la valeur par défaut de cette propriété, à savoir <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> pour ne pas utiliser MTOM.</span><span class="sxs-lookup"><span data-stu-id="c2abd-109">Leave  this property at its default value, which is <xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType> to not use MTOM.</span></span>  
  
- <span data-ttu-id="c2abd-110">La sécurité du message contrôlée par la valeur <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> fournit une prise en charge de WS-Security conforme à WS-I Basic Security Profile 1.0.</span><span class="sxs-lookup"><span data-stu-id="c2abd-110">Message security controlled by the <xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> value provides WS-Security support compliant with WS-I Basic Security Profile 1.0.</span></span> <span data-ttu-id="c2abd-111">Conservez la valeur par défaut de cette propriété, à savoir <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> pour ne pas utiliser WS-Security.</span><span class="sxs-lookup"><span data-stu-id="c2abd-111">Leave this property at its default value, which is <xref:System.ServiceModel.SecurityMode.Transport?displayProperty=nameWithType> to not use WS-Security.</span></span>  
  
<span data-ttu-id="c2abd-112">Pour rendre les métadonnées d’un service WCF disponibles pour ASP.NET, utilisez les outils de génération de client de service Web : [Web Services Description Language (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [outil de découverte de Services Web (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100))et la fonctionnalité **Ajouter une référence Web** dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c2abd-112">To make the metadata for a WCF service available to ASP.NET, use the Web service client generation tools: [Web Services Description Language Tool (Wsdl.exe)](/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100)), [Web Services Discovery Tool (Disco.exe)](/previous-versions/dotnet/netframework-4.0/cy2a3ybs(v=vs.100)), and the **Add Web Reference** feature in Visual Studio.</span></span> <span data-ttu-id="c2abd-113">Activez la publication des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c2abd-113">Enable metadata publication.</span></span> <span data-ttu-id="c2abd-114">Pour plus d’informations, consultez [publication de points de terminaison de métadonnées](publishing-metadata-endpoints.md).</span><span class="sxs-lookup"><span data-stu-id="c2abd-114">For more information, see [Publishing Metadata Endpoints](publishing-metadata-endpoints.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2abd-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c2abd-115">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c2abd-116">Description</span><span class="sxs-lookup"><span data-stu-id="c2abd-116">Description</span></span>  
 <span data-ttu-id="c2abd-117">L’exemple de code suivant montre comment ajouter un point de terminaison WCF compatible avec les clients de service Web ASP.NET dans le code et, alternativement, dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="c2abd-117">The following example code demonstrates how to add a WCF endpoint that is compatible with ASP.NET Web service clients in code and, alternatively, in a configuration file.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c2abd-118">Code</span><span class="sxs-lookup"><span data-stu-id="c2abd-118">Code</span></span>  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)]
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)]  
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c2abd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2abd-119">See also</span></span>

- [<span data-ttu-id="c2abd-120">Interopérabilité avec les services Web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c2abd-120">Interoperability with ASP.NET Web Services</span></span>](./feature-details/interop-with-aspnet-web-services.md)
