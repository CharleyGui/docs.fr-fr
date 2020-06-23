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
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="bba84-103">Didacticiel : définir un contrat de service Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="bba84-103">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="bba84-104">Ce didacticiel décrit la première des cinq tâches requises pour créer une application de base Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bba84-104">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="bba84-105">Pour obtenir une vue d’ensemble des didacticiels, consultez [Didacticiel : prise en main des applications Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="bba84-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="bba84-106">Lorsque vous créez un service WCF, votre première tâche consiste à définir un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="bba84-106">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="bba84-107">Le contrat de service spécifie les opérations prises en charge par le service.</span><span class="sxs-lookup"><span data-stu-id="bba84-107">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="bba84-108">Une opération peut être considérée comme une méthode de service Web.</span><span class="sxs-lookup"><span data-stu-id="bba84-108">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="bba84-109">Vous créez des contrats de service en définissant une interface C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bba84-109">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="bba84-110">Une interface possède les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="bba84-110">An interface has the following characteristics:</span></span>

- <span data-ttu-id="bba84-111">Chaque méthode dans l'interface correspond à une opération de service spécifique.</span><span class="sxs-lookup"><span data-stu-id="bba84-111">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="bba84-112">Pour chaque interface, vous devez appliquer l' <xref:System.ServiceModel.ServiceContractAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="bba84-112">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="bba84-113">Pour chaque opération/méthode, vous devez appliquer l' <xref:System.ServiceModel.OperationContractAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="bba84-113">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="bba84-114">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="bba84-114">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bba84-115">Créez un projet de **bibliothèque de service WCF** .</span><span class="sxs-lookup"><span data-stu-id="bba84-115">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="bba84-116">Définissez une interface de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="bba84-116">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="bba84-117">Créer un projet de bibliothèque de service WCF et définir une interface de contrat de service</span><span class="sxs-lookup"><span data-stu-id="bba84-117">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="bba84-118">Ouvrez Visual Studio en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="bba84-118">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="bba84-119">Pour ce faire, sélectionnez le programme Visual Studio dans le menu **Démarrer** , puis sélectionnez **plus**  >  **exécuter en tant qu’administrateur** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="bba84-119">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="bba84-120">Créez un projet de **bibliothèque de service WCF** .</span><span class="sxs-lookup"><span data-stu-id="bba84-120">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="bba84-121">Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="bba84-121">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="bba84-122">Dans la boîte de dialogue **nouveau projet** , sur le côté gauche, développez **Visual C#** ou **Visual Basic**, puis sélectionnez la catégorie **WCF** .</span><span class="sxs-lookup"><span data-stu-id="bba84-122">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="bba84-123">Visual Studio affiche une liste de modèles de projet dans la section centrale de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="bba84-123">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="bba84-124">Sélectionnez **bibliothèque de services WCF**.</span><span class="sxs-lookup"><span data-stu-id="bba84-124">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="bba84-125">Si vous ne voyez pas la catégorie de modèle de projet **WCF** , vous devrez peut-être installer le composant **Windows Communication Foundation** de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bba84-125">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="bba84-126">Dans la boîte de dialogue **nouveau projet** , sélectionnez le lien **ouvrir le Visual Studio installer** sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="bba84-126">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="bba84-127">Sélectionnez l’onglet **composants individuels** , puis recherchez et sélectionnez **Windows Communication Foundation** sous la catégorie **activités de développement** .</span><span class="sxs-lookup"><span data-stu-id="bba84-127">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="bba84-128">Choisissez **modifier** pour commencer l’installation du composant.</span><span class="sxs-lookup"><span data-stu-id="bba84-128">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="bba84-129">Dans la section inférieure de la fenêtre, entrez *GettingStartedLib* pour le **nom** et *gettingstarted* pour le **nom**de la solution.</span><span class="sxs-lookup"><span data-stu-id="bba84-129">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="bba84-130">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="bba84-130">Select **OK**.</span></span>

      <span data-ttu-id="bba84-131">Visual Studio crée le projet, qui contient trois fichiers : *IService1.cs* (ou *IService1. vb* pour un projet Visual Basic), *Service1.cs* (ou *Service1. vb* pour un projet Visual Basic) et *App.config*. Visual Studio définit ces fichiers comme suit :</span><span class="sxs-lookup"><span data-stu-id="bba84-131">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="bba84-132">Le fichier *IService1* contient la définition par défaut du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="bba84-132">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="bba84-133">Le fichier *Service1* contient l’implémentation par défaut du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="bba84-133">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="bba84-134">Le fichier *App.config* contient les informations de configuration nécessaires au chargement du service par défaut avec l’outil hôte de service WCF de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bba84-134">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="bba84-135">Pour plus d’informations sur l’outil hôte de service WCF, voir [hôte de service WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bba84-135">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="bba84-136">Si vous avez installé Visual Studio avec Visual Basic paramètres d’environnement de développement, la solution peut être masquée.</span><span class="sxs-lookup"><span data-stu-id="bba84-136">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="bba84-137">Si c’est le cas, sélectionnez **options** dans le menu **Outils** , puis sélectionnez **projets et solutions**  >  **général** dans la fenêtre **options** .</span><span class="sxs-lookup"><span data-stu-id="bba84-137">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="bba84-138">Sélectionnez **toujours afficher la solution**.</span><span class="sxs-lookup"><span data-stu-id="bba84-138">Select **Always show solution**.</span></span> <span data-ttu-id="bba84-139">Vérifiez également que l’option **enregistrer les nouveaux projets lors de la création** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="bba84-139">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="bba84-140">À partir de **Explorateur de solutions**, ouvrez le fichier **IService1.cs** ou **IService1. vb** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="bba84-140">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="bba84-141">Ce contrat définit une calculatrice en ligne.</span><span class="sxs-lookup"><span data-stu-id="bba84-141">This contract defines an online calculator.</span></span> <span data-ttu-id="bba84-142">Notez `ICalculator` que l’interface est marquée avec l' <xref:System.ServiceModel.ServiceContractAttribute> attribut (simplifiée en tant que `ServiceContract` ).</span><span class="sxs-lookup"><span data-stu-id="bba84-142">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="bba84-143">Cet attribut définit un espace de noms pour lever toute ambiguïté sur le nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="bba84-143">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="bba84-144">Le code marque chaque opération de calculatrice avec l' <xref:System.ServiceModel.OperationContractAttribute> attribut (simplifié comme `OperationContract` ).</span><span class="sxs-lookup"><span data-stu-id="bba84-144">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bba84-145">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="bba84-145">Next steps</span></span>

<span data-ttu-id="bba84-146">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="bba84-146">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="bba84-147">Créez un projet de bibliothèque de service WCF.</span><span class="sxs-lookup"><span data-stu-id="bba84-147">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="bba84-148">Définissez une interface de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="bba84-148">Define a service contract interface.</span></span>

<span data-ttu-id="bba84-149">Passez au didacticiel suivant pour découvrir comment implémenter le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="bba84-149">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bba84-150">Didacticiel : implémenter un contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="bba84-150">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
