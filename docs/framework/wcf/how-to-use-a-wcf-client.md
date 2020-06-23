---
title: 'Didacticiel : utiliser un client Windows Communication Foundation'
description: Apprenez à créer une instance de client, à compiler l’application et à communiquer avec un service dans le cadre d’une série d’articles sur la création d’une application WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c94d5f8af679580c4194aaaadeda759098953d2
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244333"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="a3e1a-103">Didacticiel : utiliser un client Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a3e1a-103">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="a3e1a-104">Ce didacticiel décrit la dernière des cinq tâches nécessaires à la création d’une application de base Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a3e1a-104">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="a3e1a-105">Pour obtenir une vue d’ensemble des didacticiels, consultez [Didacticiel : prise en main des applications Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a3e1a-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="a3e1a-106">Une fois que vous avez créé et configuré un proxy Windows Communication Foundation (WCF), vous créez une instance cliente et compilez l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-106">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="a3e1a-107">Vous l’utilisez ensuite pour communiquer avec le service WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-107">You then use it to communicate with the WCF service.</span></span>

<span data-ttu-id="a3e1a-108">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="a3e1a-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a3e1a-109">Ajoutez du code pour utiliser le client WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-109">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="a3e1a-110">Testez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-110">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="a3e1a-111">Ajouter du code pour utiliser le client WCF</span><span class="sxs-lookup"><span data-stu-id="a3e1a-111">Add code to use the WCF client</span></span>

<span data-ttu-id="a3e1a-112">Le code client effectue les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a3e1a-112">The client code does the following steps:</span></span>

- <span data-ttu-id="a3e1a-113">Instancie le client WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-113">Instantiates the WCF client.</span></span>
- <span data-ttu-id="a3e1a-114">Appelle les opérations de service à partir du proxy généré.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-114">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="a3e1a-115">Ferme le client une fois l’appel d’opération terminé.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-115">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="a3e1a-116">Ouvrez le fichier **Program.cs** ou **Module1. vb** à partir du projet **GettingStartedClient** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a3e1a-116">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using GettingStartedClient.ServiceReference1;

namespace GettingStartedClient
{
    class Program
    {
        static void Main(string[] args)
        {
            //Step 1: Create an instance of the WCF proxy.
            CalculatorClient client = new CalculatorClient();

            // Step 2: Call the service operations.
            // Call the Add service operation.
            double value1 = 100.00D;
            double value2 = 15.99D;
            double result = client.Add(value1, value2);
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

            // Call the Subtract service operation.
            value1 = 145.00D;
            value2 = 76.54D;
            result = client.Subtract(value1, value2);
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

            // Call the Multiply service operation.
            value1 = 9.00D;
            value2 = 81.25D;
            result = client.Multiply(value1, value2);
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

            // Call the Divide service operation.
            value1 = 22.00D;
            value2 = 7.00D;
            result = client.Divide(value1, value2);
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
            client.Close();
        }
    }
}
```

```vb
Imports System.Collections.Generic
Imports System.Text
Imports System.ServiceModel
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

<span data-ttu-id="a3e1a-117">Notez l' `using` instruction (pour Visual C#) ou `Imports` (pour Visual Basic) qui importe `GettingStartedClient.ServiceReference1` .</span><span class="sxs-lookup"><span data-stu-id="a3e1a-117">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="a3e1a-118">Cette instruction importe le code généré par Visual Studio avec la fonction **Ajouter une référence de service** .</span><span class="sxs-lookup"><span data-stu-id="a3e1a-118">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="a3e1a-119">Le code instancie le proxy WCF et appelle chacune des opérations de service exposées par le service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-119">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="a3e1a-120">Il ferme ensuite le proxy et met fin au programme.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-120">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="a3e1a-121">Tester le client WCF</span><span class="sxs-lookup"><span data-stu-id="a3e1a-121">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="a3e1a-122">Tester l’application à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a3e1a-122">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="a3e1a-123">Enregistrez et générez la solution.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-123">Save and build the solution.</span></span>

2. <span data-ttu-id="a3e1a-124">Sélectionnez le dossier **GettingStartedLib** , puis sélectionnez **définir comme projet de démarrage** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-124">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="a3e1a-125">Dans **projets de démarrage**, sélectionnez **GettingStartedLib** dans la liste déroulante, puis sélectionnez **exécuter** ou appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-125">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="a3e1a-126">Tester l’application à partir d’une invite de commandes</span><span class="sxs-lookup"><span data-stu-id="a3e1a-126">Test the application from a command prompt</span></span>

1. <span data-ttu-id="a3e1a-127">Ouvrez une invite de commandes en tant qu’administrateur, puis accédez au répertoire de votre solution Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-127">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span>

2. <span data-ttu-id="a3e1a-128">Pour démarrer le service : entrez *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-128">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="a3e1a-129">Pour démarrer le client : Ouvrez une autre invite de commandes, accédez au répertoire de votre solution Visual Studio, puis entrez *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-129">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="a3e1a-130">*GettingStartedHost.exe* produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a3e1a-130">*GettingStartedHost.exe* produces the following output:</span></span>

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   <span data-ttu-id="a3e1a-131">*GettingStartedClient.exe* produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="a3e1a-131">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="a3e1a-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a3e1a-132">Next steps</span></span>

<span data-ttu-id="a3e1a-133">Vous avez maintenant terminé toutes les tâches du didacticiel de prise en main de WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-133">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="a3e1a-134">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="a3e1a-134">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="a3e1a-135">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="a3e1a-135">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a3e1a-136">Ajoutez du code pour utiliser le client WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-136">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="a3e1a-137">Testez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-137">Test the WCF client.</span></span>

<span data-ttu-id="a3e1a-138">Si vous rencontrez des problèmes ou des erreurs dans l’une de ces étapes, suivez les étapes de l’article sur la résolution des problèmes pour les corriger.</span><span class="sxs-lookup"><span data-stu-id="a3e1a-138">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a3e1a-139">Résoudre les problèmes liés aux didacticiels prise en main de WCF</span><span class="sxs-lookup"><span data-stu-id="a3e1a-139">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
