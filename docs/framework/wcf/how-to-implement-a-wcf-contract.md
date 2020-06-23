---
title: 'Didacticiel : implémenter un contrat de service Windows Communication Foundation'
description: Découvrez comment ajouter du code pour implémenter une interface de service WCF dans le cadre d’une série d’articles qui vous permettent de commencer à créer une application WCF.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 89f97610cccd42c2a5d298baa667327d077fd472
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244645"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="cecf0-103">Didacticiel : implémenter un contrat de service Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="cecf0-103">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="cecf0-104">Ce didacticiel décrit la deuxième des cinq tâches nécessaires à la création d’une application de base Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="cecf0-104">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="cecf0-105">Pour obtenir une vue d’ensemble des didacticiels, consultez [Didacticiel : prise en main des applications Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="cecf0-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="cecf0-106">L’étape suivante de la création d’une application WCF consiste à ajouter du code pour implémenter l’interface de service WCF que vous avez créée à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="cecf0-106">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="cecf0-107">Dans cette étape, vous allez créer une classe nommée `CalculatorService` qui implémente l’interface définie par l’utilisateur `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="cecf0-107">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="cecf0-108">Chaque méthode dans le code suivant appelle une opération de calculatrice et écrit du texte dans la console pour la tester.</span><span class="sxs-lookup"><span data-stu-id="cecf0-108">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="cecf0-109">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="cecf0-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="cecf0-110">Ajoutez du code pour implémenter le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="cecf0-110">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="cecf0-111">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="cecf0-111">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="cecf0-112">Ajouter du code pour implémenter le contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="cecf0-112">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="cecf0-113">Dans **GettingStartedLib**, ouvrez le fichier **Service1.cs** ou **Service1. vb** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="cecf0-113">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="cecf0-114">Modifier App.config</span><span class="sxs-lookup"><span data-stu-id="cecf0-114">Edit App.config</span></span>

<span data-ttu-id="cecf0-115">Modifiez **App.config** dans **GettingStartedLib** pour refléter les modifications que vous avez apportées au code.</span><span class="sxs-lookup"><span data-stu-id="cecf0-115">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="cecf0-116">Pour les projets Visual C# :</span><span class="sxs-lookup"><span data-stu-id="cecf0-116">For Visual C# projects:</span></span>
  - <span data-ttu-id="cecf0-117">Remplacez la ligne 14 par`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="cecf0-117">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="cecf0-118">Remplacez la ligne 17 par`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="cecf0-118">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="cecf0-119">Remplacez la ligne 22 par`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="cecf0-119">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="cecf0-120">Pour les projets Visual Basic :</span><span class="sxs-lookup"><span data-stu-id="cecf0-120">For Visual Basic projects:</span></span>
  - <span data-ttu-id="cecf0-121">Remplacez la ligne 14 par`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="cecf0-121">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="cecf0-122">Remplacez la ligne 17 par`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="cecf0-122">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="cecf0-123">Remplacez la ligne 22 par`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="cecf0-123">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="cecf0-124">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="cecf0-124">Compile the code</span></span>

<span data-ttu-id="cecf0-125">Générez la solution pour vérifier qu’il n’y a pas d’erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="cecf0-125">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="cecf0-126">Si vous utilisez Visual Studio, dans le menu **générer** , sélectionnez **générer la solution** (ou appuyez sur **CTRL** + **MAJ** + **B**).</span><span class="sxs-lookup"><span data-stu-id="cecf0-126">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="cecf0-127">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="cecf0-127">Next steps</span></span>

<span data-ttu-id="cecf0-128">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="cecf0-128">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="cecf0-129">Ajoutez du code pour implémenter le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="cecf0-129">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="cecf0-130">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="cecf0-130">Build the solution.</span></span>

<span data-ttu-id="cecf0-131">Passez au didacticiel suivant pour découvrir comment exécuter le service WCF.</span><span class="sxs-lookup"><span data-stu-id="cecf0-131">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cecf0-132">Didacticiel : héberger et exécuter un service WCF de base</span><span class="sxs-lookup"><span data-stu-id="cecf0-132">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
