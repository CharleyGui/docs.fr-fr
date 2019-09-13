---
title: 'Tutoriel : Implémenter un contrat de service Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 05923dc0a2223da5e5fcda483abc1ee1dd2d643f
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928712"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Tutoriel : Implémenter un contrat de service Windows Communication Foundation

Ce didacticiel décrit la deuxième des cinq tâches nécessaires à la création d’une application de base Windows Communication Foundation (WCF). Pour obtenir une vue d’ensemble des didacticiels, consultez [didacticiel : Prise en main des applications](getting-started-tutorial.md)Windows Communication Foundation.

L’étape suivante de la création d’une application WCF consiste à ajouter du code pour implémenter l’interface de service WCF que vous avez créée à l’étape précédente. Dans cette étape, vous allez créer une classe `CalculatorService` nommée qui implémente l’interface définie `ICalculator` par l’utilisateur. Chaque méthode dans le code suivant appelle une opération de calculatrice et écrit du texte dans la console pour la tester. 

Ce tutoriel vous montre comment effectuer les opérations suivantes :
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

## <a name="edit-appconfig"></a>Modifier le fichier app. config

Modifiez le **fichier app. config** dans **GettingStartedLib** pour refléter les modifications que vous avez apportées au code.

- Pour les C# projets visuels :
  - Remplacez la ligne 14 par`<service name="GettingStartedLib.CalculatorService">`
  - Remplacez la ligne 17 par`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Remplacez la ligne 22 par`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Pour les projets Visual Basic :
  - Remplacez la ligne 14 par`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Remplacez la ligne 17 par`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Remplacez la ligne 22 par`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Compiler le code

Générez la solution pour vérifier qu’il n’y a pas d’erreurs de compilation. Si vous utilisez Visual Studio, dans le menu **générer** , sélectionnez **générer la solution** (ou appuyez sur **CTRL**+**MAJ**+**B**).

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris à :
> [!div class="checklist"]
>
> - Ajoutez du code pour implémenter le contrat de service WCF.
> - Générez la solution.

Passez au didacticiel suivant pour découvrir comment exécuter le service WCF.

> [!div class="nextstepaction"]
> [Tutoriel : Héberger et exécuter un service WCF de base](how-to-host-and-run-a-basic-wcf-service.md)
