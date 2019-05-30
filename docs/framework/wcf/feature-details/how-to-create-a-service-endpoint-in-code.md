---
title: 'Procédure : créer un point de terminaison de Service dans le code'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fbb22fa-2930-48b8-b437-def1de87c6a0
ms.openlocfilehash: 9b7b983122b9e30fd7c6b0d0c517a9483b8881c5
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301467"
---
# <a name="how-to-create-a-service-endpoint-in-code"></a><span data-ttu-id="18d6e-102">Procédure : créer un point de terminaison de Service dans le code</span><span class="sxs-lookup"><span data-stu-id="18d6e-102">How to: Create a Service Endpoint in Code</span></span>
<span data-ttu-id="18d6e-103">Dans cet exemple, un contrat `ICalculator` est défini pour un service de calculatrice, le service est implémenté dans la classe `CalculatorService`, puis son point de terminaison est défini dans du code, où il est spécifié que le service doit utiliser la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="18d6e-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="18d6e-104">Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d'adresse dans la configuration plutôt que de manière impérative dans le code.</span><span class="sxs-lookup"><span data-stu-id="18d6e-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="18d6e-105">La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service.</span><span class="sxs-lookup"><span data-stu-id="18d6e-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="18d6e-106">Plus généralement, le fait de laisser les informations de liaison et d’adresse hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application.</span><span class="sxs-lookup"><span data-stu-id="18d6e-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
#### <a name="to-create-a-service-endpoint-in-code"></a><span data-ttu-id="18d6e-107">Pour créer un point de terminaison de service dans le code</span><span class="sxs-lookup"><span data-stu-id="18d6e-107">To create a service endpoint in code</span></span>  
  
1. <span data-ttu-id="18d6e-108">Créez l'interface qui définit le contrat de service.</span><span class="sxs-lookup"><span data-stu-id="18d6e-108">Create the interface that defines the service contract.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[c_HowTo_CodeServiceBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="18d6e-109">Implémentez le contrat de service défini dans l'étape 1.</span><span class="sxs-lookup"><span data-stu-id="18d6e-109">Implement the service contract defined in step 1.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[c_HowTo_CodeServiceBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="18d6e-110">Dans l’application d’hébergement, créez l’adresse de base pour le service et la liaison à utiliser avec le service.</span><span class="sxs-lookup"><span data-stu-id="18d6e-110">In the hosting application, create the base address for the service and the binding to be used with the service.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[c_HowTo_CodeServiceBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="18d6e-111">Créez l'hôte et appelez <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> ou une des autres surcharges pour ajouter le point de terminaison de service pour l'hôte.</span><span class="sxs-lookup"><span data-stu-id="18d6e-111">Create the host and call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%28System.Type%2CSystem.ServiceModel.Channels.Binding%2CSystem.String%29?displayProperty=nameWithType> or one of the other overloads to add the service endpoint for the host.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#6)]
     [!code-vb[c_HowTo_CodeServiceBinding#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#6)]  
  
     <span data-ttu-id="18d6e-112">Spécifier la liaison dans le code, mais utiliser les points de terminaison par défaut fournis par le runtime, transmettre l’adresse de base au constructeur lors de la création du <xref:System.ServiceModel.ServiceHost>et n’appelez pas <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="18d6e-112">To specify the binding in code but to use the default endpoints provided by the runtime, pass the base address into the constructor when creating the <xref:System.ServiceModel.ServiceHost>, and do not call <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#7)]
     [!code-vb[c_HowTo_CodeServiceBinding#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#7)]  
  
     <span data-ttu-id="18d6e-113">Pour plus d’informations sur les points de terminaison par défaut, consultez [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) et [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="18d6e-113">For more information about default endpoints, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d6e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18d6e-114">See also</span></span>

- [<span data-ttu-id="18d6e-115">Guide pratique pour Spécifier une liaison de Service dans le Code</span><span class="sxs-lookup"><span data-stu-id="18d6e-115">How to: Specify a Service Binding in Code</span></span>](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
