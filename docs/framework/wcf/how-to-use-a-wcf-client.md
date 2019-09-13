---
title: 'Tutoriel : Utiliser un client Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c280933c81ef54ba58181e3005e30775b9b8e42
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928887"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="ede3c-102">Tutoriel : Utiliser un client Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ede3c-102">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="ede3c-103">Ce didacticiel décrit la dernière des cinq tâches nécessaires à la création d’une application de base Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ede3c-103">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="ede3c-104">Pour obtenir une vue d’ensemble des didacticiels, consultez [didacticiel : Prise en main des applications](getting-started-tutorial.md)Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="ede3c-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="ede3c-105">Une fois que vous avez créé et configuré un proxy Windows Communication Foundation (WCF), vous créez une instance cliente et compilez l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="ede3c-105">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="ede3c-106">Vous l’utilisez ensuite pour communiquer avec le service WCF.</span><span class="sxs-lookup"><span data-stu-id="ede3c-106">You then use it to communicate with the WCF service.</span></span> 

<span data-ttu-id="ede3c-107">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ede3c-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ede3c-108">Ajoutez du code pour utiliser le client WCF.</span><span class="sxs-lookup"><span data-stu-id="ede3c-108">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="ede3c-109">Testez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="ede3c-109">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="ede3c-110">Ajouter du code pour utiliser le client WCF</span><span class="sxs-lookup"><span data-stu-id="ede3c-110">Add code to use the WCF client</span></span>

<span data-ttu-id="ede3c-111">Le code client effectue les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="ede3c-111">The client code does the following steps:</span></span>

- <span data-ttu-id="ede3c-112">Instancie le client WCF.</span><span class="sxs-lookup"><span data-stu-id="ede3c-112">Instantiates the WCF client.</span></span>
- <span data-ttu-id="ede3c-113">Appelle les opérations de service à partir du proxy généré.</span><span class="sxs-lookup"><span data-stu-id="ede3c-113">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="ede3c-114">Ferme le client une fois l’appel d’opération terminé.</span><span class="sxs-lookup"><span data-stu-id="ede3c-114">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="ede3c-115">Ouvrez le fichier **Program.cs** ou **Module1. vb** à partir du projet **GettingStartedClient** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="ede3c-115">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

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
Imports System
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

<span data-ttu-id="ede3c-116">Notez l' `using` instruction (pour C#Visual) `Imports` ou (pour Visual Basic) qui importe `GettingStartedClient.ServiceReference1`.</span><span class="sxs-lookup"><span data-stu-id="ede3c-116">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="ede3c-117">Cette instruction importe le code généré par Visual Studio avec la fonction **Ajouter une référence de service** .</span><span class="sxs-lookup"><span data-stu-id="ede3c-117">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="ede3c-118">Le code instancie le proxy WCF et appelle chacune des opérations de service exposées par le service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="ede3c-118">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="ede3c-119">Il ferme ensuite le proxy et met fin au programme.</span><span class="sxs-lookup"><span data-stu-id="ede3c-119">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="ede3c-120">Tester le client WCF</span><span class="sxs-lookup"><span data-stu-id="ede3c-120">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="ede3c-121">Tester l’application à partir de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ede3c-121">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="ede3c-122">Enregistrez et générez la solution.</span><span class="sxs-lookup"><span data-stu-id="ede3c-122">Save and build the solution.</span></span>

2. <span data-ttu-id="ede3c-123">Sélectionnez le dossier **GettingStartedLib** , puis sélectionnez **définir comme projet de démarrage** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="ede3c-123">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="ede3c-124">Dans **projets de démarrage**, sélectionnez **GettingStartedLib** dans la liste déroulante, puis sélectionnez **exécuter** ou appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="ede3c-124">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="ede3c-125">Tester l’application à partir d’une invite de commandes</span><span class="sxs-lookup"><span data-stu-id="ede3c-125">Test the application from a command prompt</span></span>

1. <span data-ttu-id="ede3c-126">Ouvrez une invite de commandes en tant qu’administrateur, puis accédez au répertoire de votre solution Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ede3c-126">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span> 

2. <span data-ttu-id="ede3c-127">Pour démarrer le service : Entrez *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span><span class="sxs-lookup"><span data-stu-id="ede3c-127">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="ede3c-128">Pour démarrer le client : Ouvrez une autre invite de commandes, accédez au répertoire de votre solution Visual Studio, puis entrez *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="ede3c-128">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="ede3c-129">*GettingStartedHost. exe* génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ede3c-129">*GettingStartedHost.exe* produces the following output:</span></span>

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

   <span data-ttu-id="ede3c-130">*GettingStartedClient. exe* génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="ede3c-130">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="ede3c-131">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ede3c-131">Next steps</span></span>

<span data-ttu-id="ede3c-132">Vous avez maintenant terminé toutes les tâches du didacticiel de prise en main de WCF.</span><span class="sxs-lookup"><span data-stu-id="ede3c-132">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="ede3c-133">Dans ce tutoriel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="ede3c-133">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="ede3c-134">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="ede3c-134">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ede3c-135">Ajoutez du code pour utiliser le client WCF.</span><span class="sxs-lookup"><span data-stu-id="ede3c-135">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="ede3c-136">Testez le client WCF.</span><span class="sxs-lookup"><span data-stu-id="ede3c-136">Test the WCF client.</span></span>

<span data-ttu-id="ede3c-137">Si vous rencontrez des problèmes ou des erreurs dans l’une de ces étapes, suivez les étapes de l’article sur la résolution des problèmes pour les corriger.</span><span class="sxs-lookup"><span data-stu-id="ede3c-137">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ede3c-138">Résoudre les problèmes liés aux didacticiels prise en main de WCF</span><span class="sxs-lookup"><span data-stu-id="ede3c-138">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
