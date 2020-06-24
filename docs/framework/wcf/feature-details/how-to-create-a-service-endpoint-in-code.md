---
title: 'Comment : créer un point de terminaison de service dans le code'
description: Découvrez comment implémenter un service dans une classe et définir son point de terminaison par programme. Dans WCF, les points de terminaison sont généralement définis dans un fichier de configuration.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 3b2ff2a17975bc381db61edc2c0f85f67edd3325
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247050"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a><span data-ttu-id="be375-104">Comment : créer un point de terminaison de service dans le code</span><span class="sxs-lookup"><span data-stu-id="be375-104">How to: Create a Service Endpoint in Code</span></span>
<span data-ttu-id="be375-105">Dans cet exemple, un contrat `ICalculator` est défini pour un service de calculatrice, le service est implémenté dans la classe `CalculatorService`, puis son point de terminaison est défini dans du code, où il est spécifié que le service doit utiliser la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="be375-105">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="be375-106">Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d'adresse dans la configuration plutôt que de manière impérative dans le code.</span><span class="sxs-lookup"><span data-stu-id="be375-106">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="be375-107">La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service.</span><span class="sxs-lookup"><span data-stu-id="be375-107">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="be375-108">Plus généralement, le fait de laisser les informations de liaison et d’adresse hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application.</span><span class="sxs-lookup"><span data-stu-id="be375-108">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
#### <a name="to-create-a-service-endpoint-in-code"></a><span data-ttu-id="be375-109">Pour créer un point de terminaison de service dans le code</span><span class="sxs-lookup"><span data-stu-id="be375-109">To create a service endpoint in code</span></span>  
  
1. <span data-ttu-id="be375-110">Créez l'interface qui définit le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="be375-110">Create the interface that defines the service contract.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="be375-111">Implémentez le contrat de service défini dans l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="be375-111">Implement the service contract defined in step 1.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="be375-112">Dans l’application d’hébergement, créez l’adresse de base pour le service et la liaison à utiliser avec le service.</span><span class="sxs-lookup"><span data-stu-id="be375-112">In the hosting application, create the base address for the service and the binding to be used with the service.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="be375-113">Créez l'hôte et appelez <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> ou une des autres surcharges pour ajouter le point de terminaison de service pour l'hôte.</span><span class="sxs-lookup"><span data-stu-id="be375-113">Create the host and call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> or one of the other overloads to add the service endpoint for the host.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     <span data-ttu-id="be375-114">Pour spécifier la liaison dans le code, mais pour utiliser les points de terminaison par défaut fournis par le runtime, transmettez l’adresse de base au constructeur lors de la création de <xref:System.ServiceModel.ServiceHost> et n’appelez pas <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="be375-114">To specify the binding in code but to use the default endpoints provided by the runtime, pass the base address into the constructor when creating the <xref:System.ServiceModel.ServiceHost>, and do not call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     <span data-ttu-id="be375-115">Pour plus d’informations sur les points de terminaison par défaut, consultez [configuration simplifiée](../simplified-configuration.md) et [configuration simplifiée pour les services WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="be375-115">For more information about default endpoints, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be375-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be375-116">See also</span></span>

- [<span data-ttu-id="be375-117">Guide pratique pour spécifier une liaison de service dans le code</span><span class="sxs-lookup"><span data-stu-id="be375-117">How to: Specify a Service Binding in Code</span></span>](../how-to-specify-a-service-binding-in-code.md)
