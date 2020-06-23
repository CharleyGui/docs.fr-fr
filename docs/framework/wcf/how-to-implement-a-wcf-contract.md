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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Didacticiel : implémenter un contrat de service Windows Communication Foundation

Ce didacticiel décrit la deuxième des cinq tâches nécessaires à la création d’une application de base Windows Communication Foundation (WCF). Pour obtenir une vue d’ensemble des didacticiels, consultez [Didacticiel : prise en main des applications Windows Communication Foundation](getting-started-tutorial.md).

L’étape suivante de la création d’une application WCF consiste à ajouter du code pour implémenter l’interface de service WCF que vous avez créée à l’étape précédente. Dans cette étape, vous allez créer une classe nommée `CalculatorService` qui implémente l’interface définie par l’utilisateur `ICalculator` . Chaque méthode dans le code suivant appelle une opération de calculatrice et écrit du texte dans la console pour la tester.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Ajoutez du code pour implémenter le contrat de service WCF.
> - Générez la solution.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Ajouter du code pour implémenter le contrat de service WCF

Dans **GettingStartedLib**, ouvrez le fichier **Service1.cs** ou **Service1. vb** et remplacez son code par le code suivant :

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

## <a name="edit-appconfig"></a>Modifier App.config

Modifiez **App.config** dans **GettingStartedLib** pour refléter les modifications que vous avez apportées au code.

- Pour les projets Visual C# :
  - Remplacez la ligne 14 par`<service name="GettingStartedLib.CalculatorService">`
  - Remplacez la ligne 17 par`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Remplacez la ligne 22 par`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Pour les projets Visual Basic :
  - Remplacez la ligne 14 par`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Remplacez la ligne 17 par`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Remplacez la ligne 22 par`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Compiler le code

Générez la solution pour vérifier qu’il n’y a pas d’erreurs de compilation. Si vous utilisez Visual Studio, dans le menu **générer** , sélectionnez **générer la solution** (ou appuyez sur **CTRL** + **MAJ** + **B**).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Ajoutez du code pour implémenter le contrat de service WCF.
> - Générez la solution.

Passez au didacticiel suivant pour découvrir comment exécuter le service WCF.

> [!div class="nextstepaction"]
> [Didacticiel : héberger et exécuter un service WCF de base](how-to-host-and-run-a-basic-wcf-service.md)
