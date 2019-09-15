---
title: 'Procédure : spécifier une liaison de client dans le code'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6bee5da4-adf7-42e6-8f78-63a9e5c6dbad
ms.openlocfilehash: 37769a84ca623e2f7f246d36180aa17537e90bfa
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990232"
---
# <a name="how-to-specify-a-client-binding-in-code"></a><span data-ttu-id="d7c2e-102">Procédure : spécifier une liaison de client dans le code</span><span class="sxs-lookup"><span data-stu-id="d7c2e-102">How to: Specify a Client Binding in Code</span></span>
<span data-ttu-id="d7c2e-103">Dans cet exemple, un client est créé afin d’utiliser un service de calculatrice et la liaison du client est spécifiée de manière impérative dans le code.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-103">In this example, a client is created to use a calculator service and the binding for that client is specified imperatively in code.</span></span> <span data-ttu-id="d7c2e-104">Le client accède au service `CalculatorService`, lequel implémente l'interface `ICalculator`. Le service et le client utilisent la classe <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-104">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="d7c2e-105">Cette procédure part du principe que le service de calculatrice est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-105">This procedure assumes that the calculator service is running.</span></span> <span data-ttu-id="d7c2e-106">Pour plus d’informations sur la création du [service, consultez Procédure : Spécifiez une liaison de service](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-106">For information about building the service, see [How to: Specify a Service Binding in Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="d7c2e-107">Il utilise également l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) fournit pour générer automatiquement les composants du client.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-107">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="d7c2e-108">Cet outil génère le code client permettant d'accéder au service.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-108">The tool generates the client code for accessing the service.</span></span>  
  
 <span data-ttu-id="d7c2e-109">La construction du client se divise en deux parties.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-109">The client is built in two parts.</span></span> <span data-ttu-id="d7c2e-110">L'outil Svcutil.exe génère la calculatrice `ClientCalculator` qui implémente l'interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-110">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="d7c2e-111">Cette application cliente est ensuite créée en construisant une instance de `ClientCalculator`, puis en spécifiant la liaison et l'adresse du service dans le code.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-111">This client application is then constructed by constructing an instance of `ClientCalculator` and then specifying the binding and the address for the service in code.</span></span>  
  
 <span data-ttu-id="d7c2e-112">Pour obtenir la copie source de cet exemple, consultez l’exemple [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d7c2e-112">For the source copy of this example, see the [BasicBinding](../../../docs/framework/wcf/samples/basicbinding.md) sample.</span></span>  
  
### <a name="to-specify-a-custom-binding-in-code"></a><span data-ttu-id="d7c2e-113">Pour spécifier une liaison personnalisée dans le code</span><span class="sxs-lookup"><span data-stu-id="d7c2e-113">To specify a custom binding in code</span></span>  
  
1. <span data-ttu-id="d7c2e-114">Utilisez l'outil Svcutil.exe depuis la ligne de commande pour générer le code à partir des métadonnées de service.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-114">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. <span data-ttu-id="d7c2e-115">Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-115">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#1)]
     [!code-vb[C_HowTo_CodeClientBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#1)]  
  
3. <span data-ttu-id="d7c2e-116">Le client généré contient également l'implémentation de `ClientCalculator`.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-116">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#2)]
     [!code-vb[C_HowTo_CodeClientBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#2)]  
  
4. <span data-ttu-id="d7c2e-117">Créez une instance de `ClientCalculator` qui utilise la classe <xref:System.ServiceModel.BasicHttpBinding> dans une application cliente. Appelez ensuite les opérations de service au niveau de l'adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-117">Create an instance of the `ClientCalculator` that uses the <xref:System.ServiceModel.BasicHttpBinding> class in a client application, and then call the service operations at the specified address.</span></span>  
  
     [!code-csharp[C_HowTo_CodeClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeclientbinding/cs/client.cs#3)]
     [!code-vb[C_HowTo_CodeClientBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeclientbinding/vb/client.vb#3)]  
  
5. <span data-ttu-id="d7c2e-118">Compilez, puis exécutez le client.</span><span class="sxs-lookup"><span data-stu-id="d7c2e-118">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7c2e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7c2e-119">See also</span></span>

- [<span data-ttu-id="d7c2e-120">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d7c2e-120">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
