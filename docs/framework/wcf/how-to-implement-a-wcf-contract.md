---
title: 'Tutorial: Mettre en œuvre un contrat de service Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: debdeeac7064f5bae21622b2d9de84a4d8a0e66f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184068"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="70de1-102">Tutorial: Mettre en œuvre un contrat de service Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="70de1-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="70de1-103">Ce tutoriel décrit la deuxième des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="70de1-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="70de1-104">Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="70de1-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="70de1-105">La prochaine étape pour la création d’une application WCF est d’ajouter du code pour implémenter l’interface de service WCF que vous avez créée dans l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="70de1-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="70de1-106">Dans cette étape, vous `CalculatorService` créez une classe nommée `ICalculator` qui implémente l’interface définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="70de1-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="70de1-107">Chaque méthode dans le code suivant appelle une opération de calculatrice et écrit du texte à la console pour la tester.</span><span class="sxs-lookup"><span data-stu-id="70de1-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="70de1-108">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="70de1-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="70de1-109">Ajouter du code pour implémenter le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="70de1-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="70de1-110">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="70de1-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="70de1-111">Ajouter du code pour implémenter le contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="70de1-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="70de1-112">Dans **GettingStartedLib**, ouvrez le fichier **Service1.cs** ou **Service1.vb** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="70de1-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

## <a name="edit-appconfig"></a><span data-ttu-id="70de1-113">Modifier App.config</span><span class="sxs-lookup"><span data-stu-id="70de1-113">Edit App.config</span></span>

<span data-ttu-id="70de1-114">Modifier **App.config** dans **GettingStartedLib** pour refléter les modifications que vous avez apportées au code.</span><span class="sxs-lookup"><span data-stu-id="70de1-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="70de1-115">Pour les projets Visual CM :</span><span class="sxs-lookup"><span data-stu-id="70de1-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="70de1-116">Changez la ligne 14 à`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="70de1-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="70de1-117">Changez la ligne 17 à`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="70de1-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="70de1-118">Changez la ligne 22 à`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="70de1-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="70de1-119">Pour les projets Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="70de1-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="70de1-120">Changez la ligne 14 à`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="70de1-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="70de1-121">Changez la ligne 17 à`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="70de1-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="70de1-122">Changez la ligne 22 à`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="70de1-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="70de1-123">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="70de1-123">Compile the code</span></span>

<span data-ttu-id="70de1-124">Construisez la solution pour vérifier qu’il n’y a pas d’erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="70de1-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="70de1-125">Si vous utilisez Visual Studio, sur le menu **Build** Select **Build Solution** (ou appuyez sur **Ctrl**+**Shift**+**B**).</span><span class="sxs-lookup"><span data-stu-id="70de1-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="70de1-126">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="70de1-126">Next steps</span></span>

<span data-ttu-id="70de1-127">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="70de1-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="70de1-128">Ajouter du code pour implémenter le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="70de1-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="70de1-129">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="70de1-129">Build the solution.</span></span>

<span data-ttu-id="70de1-130">Avancez au tutoriel suivant pour apprendre à exécuter le service WCF.</span><span class="sxs-lookup"><span data-stu-id="70de1-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="70de1-131">Tutorial: Hôte et exécuter un service de base WCF</span><span class="sxs-lookup"><span data-stu-id="70de1-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
