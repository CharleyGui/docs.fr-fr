---
title: 'Tutorial: Utilisez un client de la Fondation De communication Windows'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: d2357c134aef8da204dcdb19d6c1fc93cfdc068c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184013"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="90f43-102">Tutorial: Utilisez un client de la Fondation De communication Windows</span><span class="sxs-lookup"><span data-stu-id="90f43-102">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="90f43-103">Ce tutoriel décrit la dernière des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="90f43-103">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="90f43-104">Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="90f43-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="90f43-105">Une fois que vous avez créé et configuré un proxy de la Windows Communication Foundation (WCF), vous créez une instance client et compilez l’application client.</span><span class="sxs-lookup"><span data-stu-id="90f43-105">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="90f43-106">Vous l’utilisez ensuite pour communiquer avec le service WCF.</span><span class="sxs-lookup"><span data-stu-id="90f43-106">You then use it to communicate with the WCF service.</span></span>

<span data-ttu-id="90f43-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="90f43-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="90f43-108">Ajoutez du code pour utiliser le client WCF.</span><span class="sxs-lookup"><span data-stu-id="90f43-108">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="90f43-109">Testez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="90f43-109">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="90f43-110">Ajouter du code pour utiliser le client WCF</span><span class="sxs-lookup"><span data-stu-id="90f43-110">Add code to use the WCF client</span></span>

<span data-ttu-id="90f43-111">Le code client fait les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="90f43-111">The client code does the following steps:</span></span>

- <span data-ttu-id="90f43-112">Instantanéise le client WCF.</span><span class="sxs-lookup"><span data-stu-id="90f43-112">Instantiates the WCF client.</span></span>
- <span data-ttu-id="90f43-113">Appelle les opérations de service à partir du proxy généré.</span><span class="sxs-lookup"><span data-stu-id="90f43-113">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="90f43-114">Ferme le client une fois l’appel d’opération terminé.</span><span class="sxs-lookup"><span data-stu-id="90f43-114">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="90f43-115">Ouvrez le fichier **Program.cs** ou **Module1.vb** du projet **GettingStartedClient** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="90f43-115">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

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

<span data-ttu-id="90f43-116">Notez `using` l’énoncé (pour `Imports` le visuel CMD) `GettingStartedClient.ServiceReference1`ou (pour Visual Basic) qui importe .</span><span class="sxs-lookup"><span data-stu-id="90f43-116">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="90f43-117">Cette déclaration importe le code généré par Visual Studio avec la fonction **Add Service Reference.**</span><span class="sxs-lookup"><span data-stu-id="90f43-117">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="90f43-118">Le code instantanéise le proxy WCF et appelle chacune des opérations de service que le service de calculatrice expose.</span><span class="sxs-lookup"><span data-stu-id="90f43-118">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="90f43-119">Il ferme ensuite le proxy et met fin au programme.</span><span class="sxs-lookup"><span data-stu-id="90f43-119">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="90f43-120">Testez le client WCF</span><span class="sxs-lookup"><span data-stu-id="90f43-120">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="90f43-121">Testez l’application de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="90f43-121">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="90f43-122">Enregistrez et générez la solution.</span><span class="sxs-lookup"><span data-stu-id="90f43-122">Save and build the solution.</span></span>

2. <span data-ttu-id="90f43-123">Sélectionnez le dossier **GettingStartedLib,** puis sélectionnez **Set comme startup Project** à partir du menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="90f43-123">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="90f43-124">De **Startup Projects**, **sélectionnez GettingStartedLib** de la liste d’abandon, puis sélectionnez **Run** ou appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="90f43-124">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="90f43-125">Testez l’application à partir d’une invite de commande</span><span class="sxs-lookup"><span data-stu-id="90f43-125">Test the application from a command prompt</span></span>

1. <span data-ttu-id="90f43-126">Ouvrez une invite de commande en tant qu’administrateur, puis naviguez vers votre répertoire de solution Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90f43-126">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span>

2. <span data-ttu-id="90f43-127">Pour commencer le service: Entrez *GettingStartedHost-bin-debug-GettingStartedHost.exe*.</span><span class="sxs-lookup"><span data-stu-id="90f43-127">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="90f43-128">Pour démarrer le client : Ouvrez une autre invite de commande, naviguez vers votre répertoire de solutions Visual Studio, puis entrez *GettingStartedClient-bin-debug-GettingStartedClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="90f43-128">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="90f43-129">*GettingStartedHost.exe* produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="90f43-129">*GettingStartedHost.exe* produces the following output:</span></span>

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

   <span data-ttu-id="90f43-130">*GettingStartedClient.exe* produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="90f43-130">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="90f43-131">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="90f43-131">Next steps</span></span>

<span data-ttu-id="90f43-132">Vous avez maintenant terminé toutes les tâches dans le tutoriel WCF commencer.</span><span class="sxs-lookup"><span data-stu-id="90f43-132">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="90f43-133">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="90f43-133">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="90f43-134">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="90f43-134">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="90f43-135">Ajoutez du code pour utiliser le client WCF.</span><span class="sxs-lookup"><span data-stu-id="90f43-135">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="90f43-136">Testez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="90f43-136">Test the WCF client.</span></span>

<span data-ttu-id="90f43-137">Si vous avez des problèmes ou des erreurs dans l’une des étapes, suivez les étapes de l’article de dépannage pour les corriger.</span><span class="sxs-lookup"><span data-stu-id="90f43-137">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="90f43-138">Dépannage de la Get a commencé avec des tutoriels WCF</span><span class="sxs-lookup"><span data-stu-id="90f43-138">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
