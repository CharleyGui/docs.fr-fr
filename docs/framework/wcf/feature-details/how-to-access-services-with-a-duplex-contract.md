---
title: 'Comment : accéder aux services à l’aide d’un contrat duplex'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 746a9d64-f21c-426c-b85d-972e916ec6c5
ms.openlocfilehash: bc42792b827b49265a0b1addf959de2fa1a041e3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597213"
---
# <a name="how-to-access-services-with-a-duplex-contract"></a><span data-ttu-id="166bd-102">Comment : accéder aux services à l’aide d’un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="166bd-102">How to: Access services with a duplex contract</span></span>

<span data-ttu-id="166bd-103">L’une des fonctionnalités de Windows Communication Foundation (WCF) est la possibilité de créer un service qui utilise un modèle de messagerie duplex.</span><span class="sxs-lookup"><span data-stu-id="166bd-103">One feature of Windows Communication Foundation (WCF) is the ability to create a service that uses a duplex messaging pattern.</span></span> <span data-ttu-id="166bd-104">Ce modèle permet à un service de communiquer avec un client via un rappel.</span><span class="sxs-lookup"><span data-stu-id="166bd-104">This pattern allows a service to communicate with the client through a callback.</span></span> <span data-ttu-id="166bd-105">Cette rubrique présente les étapes de création d’un client WCF dans une classe de client qui implémente l’interface de rappel.</span><span class="sxs-lookup"><span data-stu-id="166bd-105">This topic shows the steps to create a WCF client in a client class that implements the callback interface.</span></span>

<span data-ttu-id="166bd-106">Une liaison double expose l'adresse IP du client au service.</span><span class="sxs-lookup"><span data-stu-id="166bd-106">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="166bd-107">Ce client doit utiliser un mode de sécurité afin de garantir sa connexion à un service fiable.</span><span class="sxs-lookup"><span data-stu-id="166bd-107">The client should use security to ensure that it connects only to services it trusts.</span></span>

<span data-ttu-id="166bd-108">Pour obtenir un didacticiel sur la création d’un client et d’un service WCF de base, consultez [prise en main didacticiel](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="166bd-108">For a tutorial on creating a basic WCF service and client, see [Getting Started Tutorial](../getting-started-tutorial.md).</span></span>

## <a name="to-access-a-duplex-service"></a><span data-ttu-id="166bd-109">Pour accéder à un service duplex</span><span class="sxs-lookup"><span data-stu-id="166bd-109">To access a duplex service</span></span>

1. <span data-ttu-id="166bd-110">Créez un service qui contient deux interfaces.</span><span class="sxs-lookup"><span data-stu-id="166bd-110">Create a service that contains two interfaces.</span></span> <span data-ttu-id="166bd-111">La première interface est pour le service, la deuxième est pour le rappel.</span><span class="sxs-lookup"><span data-stu-id="166bd-111">The first interface is for the service, the second is for the callback.</span></span> <span data-ttu-id="166bd-112">Pour plus d’informations sur la création d’un service duplex, consultez [Comment : créer un contrat duplex](how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="166bd-112">For more information about creating a duplex service, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>

2. <span data-ttu-id="166bd-113">Exécutez le service.</span><span class="sxs-lookup"><span data-stu-id="166bd-113">Run the service.</span></span>

3. <span data-ttu-id="166bd-114">Utilisez l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer des contrats (interfaces) pour le client.</span><span class="sxs-lookup"><span data-stu-id="166bd-114">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate contracts (interfaces) for the client.</span></span> <span data-ttu-id="166bd-115">Pour plus d’informations sur la façon de procéder, consultez [Comment : créer un client](../how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="166bd-115">For information about how to do this, see  [How to: Create a Client](../how-to-create-a-wcf-client.md).</span></span>

4. <span data-ttu-id="166bd-116">Implémentez l'interface de rappel dans la classe client, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="166bd-116">Implement the callback interface in the client class, as shown in the following example.</span></span>

    ```csharp
    public class CallbackHandler : ICalculatorDuplexCallback
    {
        public void Result(double result)
        {
            Console.WriteLine("Result ({0})", result);
        }
        public void Equation(string equation)
        {
            Console.WriteLine("Equation({0})", equation);
        }
    }
    ```

    ```vb
    Public Class CallbackHandler
    Implements ICalculatorDuplexCallback
       Public Sub Result (ByVal result As Double)
          Console.WriteLine("Result ({0})", result)
       End Sub
        Public Sub Equation(ByVal equation As String)
            Console.WriteLine("Equation({0})", equation)
        End Sub
    End Class
    ```

5. <span data-ttu-id="166bd-117">Créez une instance de la classe <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="166bd-117">Create an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="166bd-118">Le constructeur a besoin d'une instance de la classe client.</span><span class="sxs-lookup"><span data-stu-id="166bd-118">The constructor requires an instance of the client class.</span></span>

    ```csharp
    InstanceContext site = new InstanceContext(new CallbackHandler());
    ```

    ```vb
    Dim site As InstanceContext = New InstanceContext(new CallbackHandler())
    ```

6. <span data-ttu-id="166bd-119">Créez une instance du client WCF à l’aide du constructeur qui requiert un <xref:System.ServiceModel.InstanceContext> objet.</span><span class="sxs-lookup"><span data-stu-id="166bd-119">Create an instance of the WCF client using the constructor that requires an <xref:System.ServiceModel.InstanceContext> object.</span></span> <span data-ttu-id="166bd-120">Le second paramètre du constructeur correspond au nom du point de terminaison trouvé dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="166bd-120">The second parameter of the constructor is the name of an endpoint found in the configuration file.</span></span>

    ```csharp
    CalculatorDuplexClient wcfClient = new CalculatorDuplexClient(site, "default");
    ```

    ```vb
    Dim wcfClient As New CalculatorDuplexClient(site, "default")
    ```

7. <span data-ttu-id="166bd-121">Appelez les méthodes du client WCF selon les besoins.</span><span class="sxs-lookup"><span data-stu-id="166bd-121">Call the methods of the WCF client as required.</span></span>

## <a name="example"></a><span data-ttu-id="166bd-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="166bd-122">Example</span></span>

<span data-ttu-id="166bd-123">L'exemple de code suivant illustre comment créer une classe client qui accède à un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="166bd-123">The following code example demonstrates how to create a client class that accesses a duplex contract.</span></span>

[!code-csharp[S_DuplexClients#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_duplexclients/cs/client.cs#1)]
[!code-vb[S_DuplexClients#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_duplexclients/vb/client.vb#1)]

## <a name="see-also"></a><span data-ttu-id="166bd-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="166bd-124">See also</span></span>

- [<span data-ttu-id="166bd-125">Didacticiel Prise en main</span><span class="sxs-lookup"><span data-stu-id="166bd-125">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="166bd-126">Comment : créer un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="166bd-126">How to: Create a Duplex Contract</span></span>](how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="166bd-127">Outil Service Model Metadata Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="166bd-127">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="166bd-128">Guide pratique pour créer un client</span><span class="sxs-lookup"><span data-stu-id="166bd-128">How to: Create a Client</span></span>](../how-to-create-a-wcf-client.md)
- [<span data-ttu-id="166bd-129">Comment : utiliser la classe ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="166bd-129">How to: Use the ChannelFactory</span></span>](how-to-use-the-channelfactory.md)
