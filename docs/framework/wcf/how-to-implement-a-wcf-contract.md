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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Tutorial: Mettre en œuvre un contrat de service Windows Communication Foundation

Ce tutoriel décrit la deuxième des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF). Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).

La prochaine étape pour la création d’une application WCF est d’ajouter du code pour implémenter l’interface de service WCF que vous avez créée dans l’étape précédente. Dans cette étape, vous `CalculatorService` créez une classe nommée `ICalculator` qui implémente l’interface définie par l’utilisateur. Chaque méthode dans le code suivant appelle une opération de calculatrice et écrit du texte à la console pour la tester.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Ajouter du code pour implémenter le contrat de service WCF.
> - Générez la solution.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Ajouter du code pour implémenter le contrat de service WCF

Dans **GettingStartedLib**, ouvrez le fichier **Service1.cs** ou **Service1.vb** et remplacez son code par le code suivant :

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

Modifier **App.config** dans **GettingStartedLib** pour refléter les modifications que vous avez apportées au code.

- Pour les projets Visual CM :
  - Changez la ligne 14 à`<service name="GettingStartedLib.CalculatorService">`
  - Changez la ligne 17 à`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Changez la ligne 22 à`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Pour les projets Visual Basic :
  - Changez la ligne 14 à`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Changez la ligne 17 à`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Changez la ligne 22 à`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Compiler le code

Construisez la solution pour vérifier qu’il n’y a pas d’erreurs de compilation. Si vous utilisez Visual Studio, sur le menu **Build** Select **Build Solution** (ou appuyez sur **Ctrl**+**Shift**+**B**).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Ajouter du code pour implémenter le contrat de service WCF.
> - Générez la solution.

Avancez au tutoriel suivant pour apprendre à exécuter le service WCF.

> [!div class="nextstepaction"]
> [Tutorial: Hôte et exécuter un service de base WCF](how-to-host-and-run-a-basic-wcf-service.md)
