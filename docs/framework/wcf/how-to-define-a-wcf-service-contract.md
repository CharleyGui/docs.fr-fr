---
title: 'Tutorial: Définir un contrat de service Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184093"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a>Tutorial: Définir un contrat de service Windows Communication Foundation

Ce tutoriel décrit la première des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF). Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).

Lorsque vous créez un service WCF, votre première tâche est de définir un contrat de service. Le contrat de service spécifie les opérations prises en charge par le service. Une opération peut être considérée comme une méthode de service Web. Vous créez des contrats de service en définissant une interface de base visuelle ou C. Une interface a les caractéristiques suivantes :

- Chaque méthode dans l'interface correspond à une opération de service spécifique.
- Pour chaque interface, vous <xref:System.ServiceModel.ServiceContractAttribute> devez appliquer l’attribut.
- Pour chaque opération/méthode, vous <xref:System.ServiceModel.OperationContractAttribute> devez appliquer l’attribut.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Créez un projet **de bibliothèque de services WCF.**
> - Définissez une interface de contrat de service.

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a>Créer un projet de bibliothèque de services WCF et définir une interface de contrat de service

1. Ouvrez Visual Studio en tant qu’administrateur. Pour ce faire, sélectionnez le programme Visual Studio dans le menu **Démarrer,** puis sélectionnez **More** > **Run comme administrateur** du menu raccourci.

2. Créez un projet **de bibliothèque de services WCF.**

   1. Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.

   2. Dans le **dialogue du nouveau projet,** sur le côté gauche, étendre **Visual C ou** **Visual Basic**, puis sélectionnez la catégorie **WCF.** Visual Studio affiche une liste de modèles de projet dans la section centrale de la fenêtre. Sélectionnez **WCF Service Library**.

      > [!NOTE]
      > Si vous ne voyez pas la catégorie du modèle de projet **WCF,** vous devrez peut-être installer le composant **Windows Communication Foundation** de Visual Studio. Dans la boîte de dialogue **New Project,** sélectionnez le lien **Open Visual Studio Install** sur le côté gauche. Sélectionnez **l’onglet Composants individuels,** puis trouvez et sélectionnez **la Fondation de communication Windows** dans la catégorie des activités de **développement.** Choisissez **Modifier** pour commencer à installer le composant.

   3. Dans la partie inférieure de la fenêtre, entrez *GettingStartedLib* pour le **nom** et *GettingStarted* pour le **nom solution**.

   4. Sélectionnez **OK**.

      Visual Studio crée le projet, qui dispose de trois fichiers: *IService1.cs* (ou *IService1.vb* pour un projet visual Basic), *Service1.cs* (ou *Service1.vb* pour un projet de base visuelle), et *App.config*. Visual Studio définit ces fichiers comme suit :
      - Le fichier *IService1* contient la définition par défaut du contrat de service.
      - Le fichier *Service1* contient la mise en œuvre par défaut du contrat de service.
      - Le fichier *App.config* contient les informations de configuration nécessaires pour charger le service par défaut avec l’outil Visual Studio WCF Service Host. Pour plus d’informations sur l’outil WCF Service Host, voir [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).

      > [!NOTE]
      > Si vous avez installé Visual Studio avec les paramètres de l’environnement du développeur Visual Basic, la solution peut être cachée. Si tel est le cas, sélectionnez **options** dans le menu **Tools,** sélectionnez **projets et solutions** > **générales** dans la fenêtre **Options.** Sélectionnez **Toujours afficher la solution**. Vérifiez également que **enregistrer de nouveaux projets une fois créé** est sélectionné.

3. De **Solution Explorer**, ouvrez le fichier **IService1.cs** ou **IService1.vb,** et remplacez son code par le code suivant :

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

     Ce contrat définit une calculatrice en ligne. Notez `ICalculator` que l’interface est marquée avec l’attribut <xref:System.ServiceModel.ServiceContractAttribute> (simplifié comme `ServiceContract`). Cet attribut définit un espace de nom pour désambiguer le nom du contrat. Le code marque chaque <xref:System.ServiceModel.OperationContractAttribute> opération de `OperationContract`calculatrice avec l’attribut (simplifié comme ).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Créez un projet de bibliothèque de services WCF.
> - Définissez une interface de contrat de service.

Avancez au tutoriel suivant pour apprendre à mettre en œuvre le contrat de service WCF.

> [!div class="nextstepaction"]
> [Tutorial: Mettre en œuvre un contrat de service WCF](how-to-implement-a-wcf-contract.md)
