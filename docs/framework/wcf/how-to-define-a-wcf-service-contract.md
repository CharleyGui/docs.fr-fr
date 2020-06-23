---
title: 'Didacticiel : définir un contrat de service Windows Communication Foundation'
description: Découvrez comment définir un contrat de service dans le cadre d’une série d’articles qui vous aideront à créer une application WCF.
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5cb371da8c7180b8c4cbf5ac11468fbb8e0e13cc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246309"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Didacticiel : définir un contrat de service Windows Communication Foundation

Ce didacticiel décrit la première des cinq tâches requises pour créer une application de base Windows Communication Foundation (WCF). Pour obtenir une vue d’ensemble des didacticiels, consultez [Didacticiel : prise en main des applications Windows Communication Foundation](getting-started-tutorial.md).

Lorsque vous créez un service WCF, votre première tâche consiste à définir un contrat de service. Le contrat de service spécifie les opérations prises en charge par le service. Une opération peut être considérée comme une méthode de service Web. Vous créez des contrats de service en définissant une interface C# ou Visual Basic. Une interface possède les caractéristiques suivantes :

- Chaque méthode dans l'interface correspond à une opération de service spécifique.
- Pour chaque interface, vous devez appliquer l' <xref:System.ServiceModel.ServiceContractAttribute> attribut.
- Pour chaque opération/méthode, vous devez appliquer l' <xref:System.ServiceModel.OperationContractAttribute> attribut.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Créez un projet de **bibliothèque de service WCF** .
> - Définissez une interface de contrat de service.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Créer un projet de bibliothèque de service WCF et définir une interface de contrat de service

1. Ouvrez Visual Studio en tant qu’administrateur. Pour ce faire, sélectionnez le programme Visual Studio dans le menu **Démarrer** , puis sélectionnez **plus**  >  **exécuter en tant qu’administrateur** dans le menu contextuel.

2. Créez un projet de **bibliothèque de service WCF** .

   1. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

   2. Dans la boîte de dialogue **nouveau projet** , sur le côté gauche, développez **Visual C#** ou **Visual Basic**, puis sélectionnez la catégorie **WCF** . Visual Studio affiche une liste de modèles de projet dans la section centrale de la fenêtre. Sélectionnez **bibliothèque de services WCF**.

      > [!NOTE]
      > Si vous ne voyez pas la catégorie de modèle de projet **WCF** , vous devrez peut-être installer le composant **Windows Communication Foundation** de Visual Studio. Dans la boîte de dialogue **nouveau projet** , sélectionnez le lien **ouvrir le Visual Studio installer** sur le côté gauche. Sélectionnez l’onglet **composants individuels** , puis recherchez et sélectionnez **Windows Communication Foundation** sous la catégorie **activités de développement** . Choisissez **modifier** pour commencer l’installation du composant.

   3. Dans la section inférieure de la fenêtre, entrez *GettingStartedLib* pour le **nom** et *gettingstarted* pour le **nom**de la solution.

   4. Sélectionnez **OK**.

      Visual Studio crée le projet, qui contient trois fichiers : *IService1.cs* (ou *IService1. vb* pour un projet Visual Basic), *Service1.cs* (ou *Service1. vb* pour un projet Visual Basic) et *App.config*. Visual Studio définit ces fichiers comme suit :
      - Le fichier *IService1* contient la définition par défaut du contrat de service.
      - Le fichier *Service1* contient l’implémentation par défaut du contrat de service.
      - Le fichier *App.config* contient les informations de configuration nécessaires au chargement du service par défaut avec l’outil hôte de service WCF de Visual Studio. Pour plus d’informations sur l’outil hôte de service WCF, voir [hôte de service WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Si vous avez installé Visual Studio avec Visual Basic paramètres d’environnement de développement, la solution peut être masquée. Si c’est le cas, sélectionnez **options** dans le menu **Outils** , puis sélectionnez **projets et solutions**  >  **général** dans la fenêtre **options** . Sélectionnez **toujours afficher la solution**. Vérifiez également que l’option **enregistrer les nouveaux projets lors de la création** est sélectionnée.

3. À partir de **Explorateur de solutions**, ouvrez le fichier **IService1.cs** ou **IService1. vb** et remplacez son code par le code suivant :

    ```csharp
    using System;
    using System.ServiceModel;

    namespace GettingStartedLib
    {
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
            public interface ICalculator
            {
                [OperationContract]
                double Add(double n1, double n2);
                [OperationContract]
                double Subtract(double n1, double n2);
                [OperationContract]
                double Multiply(double n1, double n2);
                [OperationContract]
                double Divide(double n1, double n2);
            }
    }
    ```

    ```vb
    Imports System.ServiceModel

    Namespace GettingStartedLib

        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
        Public Interface ICalculator

            <OperationContract()> _
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
            <OperationContract()> _
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
        End Interface
    End Namespace
    ```

     Ce contrat définit une calculatrice en ligne. Notez `ICalculator` que l’interface est marquée avec l' <xref:System.ServiceModel.ServiceContractAttribute> attribut (simplifiée en tant que `ServiceContract` ). Cet attribut définit un espace de noms pour lever toute ambiguïté sur le nom du contrat. Le code marque chaque opération de calculatrice avec l' <xref:System.ServiceModel.OperationContractAttribute> attribut (simplifié comme `OperationContract` ).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Créez un projet de bibliothèque de service WCF.
> - Définissez une interface de contrat de service.

Passez au didacticiel suivant pour découvrir comment implémenter le contrat de service WCF.

> [!div class="nextstepaction"]
> [Didacticiel : implémenter un contrat de service WCF](how-to-implement-a-wcf-contract.md)
