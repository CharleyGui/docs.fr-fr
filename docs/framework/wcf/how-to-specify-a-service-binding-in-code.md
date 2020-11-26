---
title: 'Procédure : spécifier une liaison de service dans le code'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
ms.openlocfilehash: 7cf54754661182dca1e91c75b158d9b0a34a1f5e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236479"
---
# <a name="how-to-specify-a-service-binding-in-code"></a><span data-ttu-id="3ad4e-102">Procédure : spécifier une liaison de service dans le code</span><span class="sxs-lookup"><span data-stu-id="3ad4e-102">How to: Specify a Service Binding in Code</span></span>

<span data-ttu-id="3ad4e-103">Dans cet exemple, un contrat `ICalculator` est défini pour un service de calculatrice, le service est implémenté dans la classe `CalculatorService`, puis son point de terminaison est défini dans du code, où il est spécifié que le service doit utiliser la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-103">In this example, an `ICalculator` contract is defined for a calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is defined in code, where it is specified that the service must use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="3ad4e-104">Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d'adresse dans la configuration plutôt que de manière impérative dans le code.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-104">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="3ad4e-105">La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-105">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="3ad4e-106">Plus généralement, le fait de laisser les informations de liaison et d’adresse hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-106">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="3ad4e-107">Pour obtenir une description de la façon de configurer ce service à l’aide d’éléments de configuration au lieu de code, consultez [Comment : spécifier une liaison de service dans la configuration](how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="3ad4e-107">For a description of how to configure this service using configuration elements instead of code, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
### <a name="to-specify-in-code-to-use-the-basichttpbinding-for-the-service"></a><span data-ttu-id="3ad4e-108">Pour spécifier l'utilisation de BasicHttpBinding dans du code pour le service</span><span class="sxs-lookup"><span data-stu-id="3ad4e-108">To specify in code to use the BasicHttpBinding for the service</span></span>  
  
1. <span data-ttu-id="3ad4e-109">Définissez un contrat de service pour le type de service.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-109">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="3ad4e-110">Implémentez le contrat de service dans une classe de service.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-110">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3. <span data-ttu-id="3ad4e-111">Dans l’application d’hébergement, créez l’adresse de base pour le service et la liaison à utiliser avec le service.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-111">In the hosting application, create the base address for the service and the binding to use with the service.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4. <span data-ttu-id="3ad4e-112">Créez l'hôte pour le service, ajoutez le point de terminaison, puis ouvrez l'hôte.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-112">Create the host for the service, add the endpoint, and then open the host.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="3ad4e-113">Pour modifier les valeurs par défaut des propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="3ad4e-113">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="3ad4e-114">Pour modifier l’une des valeurs de propriété par défaut de la classe <xref:System.ServiceModel.BasicHttpBinding>, affectez la nouvelle valeur de propriété sur la liaison avant de créer l’hôte.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-114">To modify one of the default property values of the <xref:System.ServiceModel.BasicHttpBinding> class, set the property value on the binding to the new value before creating the host.</span></span> <span data-ttu-id="3ad4e-115">Par exemple, pour modifier les valeurs par défaut de délai d'attente d'ouverture et de fermeture de 1 minute à 2 minutes, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="3ad4e-115">For example, to change the default open and close timeout values of 1 minute to 2 minutes, use the following.</span></span>  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3ad4e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ad4e-116">See also</span></span>

- [<span data-ttu-id="3ad4e-117">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="3ad4e-117">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3ad4e-118">Spécification d'une adresse de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="3ad4e-118">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
