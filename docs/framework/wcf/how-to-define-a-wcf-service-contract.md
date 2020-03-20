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
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="90e00-102">Tutorial: Définir un contrat de service Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="90e00-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="90e00-103">Ce tutoriel décrit la première des cinq tâches requises pour créer une application de base de la Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="90e00-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="90e00-104">Pour un aperçu des tutoriels, voir [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="90e00-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="90e00-105">Lorsque vous créez un service WCF, votre première tâche est de définir un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="90e00-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="90e00-106">Le contrat de service spécifie les opérations prises en charge par le service.</span><span class="sxs-lookup"><span data-stu-id="90e00-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="90e00-107">Une opération peut être considérée comme une méthode de service Web.</span><span class="sxs-lookup"><span data-stu-id="90e00-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="90e00-108">Vous créez des contrats de service en définissant une interface de base visuelle ou C.</span><span class="sxs-lookup"><span data-stu-id="90e00-108">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="90e00-109">Une interface a les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="90e00-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="90e00-110">Chaque méthode dans l'interface correspond à une opération de service spécifique.</span><span class="sxs-lookup"><span data-stu-id="90e00-110">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="90e00-111">Pour chaque interface, vous <xref:System.ServiceModel.ServiceContractAttribute> devez appliquer l’attribut.</span><span class="sxs-lookup"><span data-stu-id="90e00-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="90e00-112">Pour chaque opération/méthode, vous <xref:System.ServiceModel.OperationContractAttribute> devez appliquer l’attribut.</span><span class="sxs-lookup"><span data-stu-id="90e00-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="90e00-113">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="90e00-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="90e00-114">Créez un projet **de bibliothèque de services WCF.**</span><span class="sxs-lookup"><span data-stu-id="90e00-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="90e00-115">Définissez une interface de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="90e00-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="90e00-116">Créer un projet de bibliothèque de services WCF et définir une interface de contrat de service</span><span class="sxs-lookup"><span data-stu-id="90e00-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="90e00-117">Ouvrez Visual Studio en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="90e00-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="90e00-118">Pour ce faire, sélectionnez le programme Visual Studio dans le menu **Démarrer,** puis sélectionnez **More** > **Run comme administrateur** du menu raccourci.</span><span class="sxs-lookup"><span data-stu-id="90e00-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="90e00-119">Créez un projet **de bibliothèque de services WCF.**</span><span class="sxs-lookup"><span data-stu-id="90e00-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="90e00-120">Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="90e00-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="90e00-121">Dans le **dialogue du nouveau projet,** sur le côté gauche, étendre **Visual C ou** **Visual Basic**, puis sélectionnez la catégorie **WCF.**</span><span class="sxs-lookup"><span data-stu-id="90e00-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="90e00-122">Visual Studio affiche une liste de modèles de projet dans la section centrale de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="90e00-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="90e00-123">Sélectionnez **WCF Service Library**.</span><span class="sxs-lookup"><span data-stu-id="90e00-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="90e00-124">Si vous ne voyez pas la catégorie du modèle de projet **WCF,** vous devrez peut-être installer le composant **Windows Communication Foundation** de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e00-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="90e00-125">Dans la boîte de dialogue **New Project,** sélectionnez le lien **Open Visual Studio Install** sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="90e00-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="90e00-126">Sélectionnez **l’onglet Composants individuels,** puis trouvez et sélectionnez **la Fondation de communication Windows** dans la catégorie des activités de **développement.**</span><span class="sxs-lookup"><span data-stu-id="90e00-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="90e00-127">Choisissez **Modifier** pour commencer à installer le composant.</span><span class="sxs-lookup"><span data-stu-id="90e00-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="90e00-128">Dans la partie inférieure de la fenêtre, entrez *GettingStartedLib* pour le **nom** et *GettingStarted* pour le **nom solution**.</span><span class="sxs-lookup"><span data-stu-id="90e00-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="90e00-129">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="90e00-129">Select **OK**.</span></span>

      <span data-ttu-id="90e00-130">Visual Studio crée le projet, qui dispose de trois fichiers: *IService1.cs* (ou *IService1.vb* pour un projet visual Basic), *Service1.cs* (ou *Service1.vb* pour un projet de base visuelle), et *App.config*. Visual Studio définit ces fichiers comme suit :</span><span class="sxs-lookup"><span data-stu-id="90e00-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="90e00-131">Le fichier *IService1* contient la définition par défaut du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="90e00-131">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="90e00-132">Le fichier *Service1* contient la mise en œuvre par défaut du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="90e00-132">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="90e00-133">Le fichier *App.config* contient les informations de configuration nécessaires pour charger le service par défaut avec l’outil Visual Studio WCF Service Host.</span><span class="sxs-lookup"><span data-stu-id="90e00-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="90e00-134">Pour plus d’informations sur l’outil WCF Service Host, voir [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="90e00-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="90e00-135">Si vous avez installé Visual Studio avec les paramètres de l’environnement du développeur Visual Basic, la solution peut être cachée.</span><span class="sxs-lookup"><span data-stu-id="90e00-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="90e00-136">Si tel est le cas, sélectionnez **options** dans le menu **Tools,** sélectionnez **projets et solutions** > **générales** dans la fenêtre **Options.**</span><span class="sxs-lookup"><span data-stu-id="90e00-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="90e00-137">Sélectionnez **Toujours afficher la solution**.</span><span class="sxs-lookup"><span data-stu-id="90e00-137">Select **Always show solution**.</span></span> <span data-ttu-id="90e00-138">Vérifiez également que **enregistrer de nouveaux projets une fois créé** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="90e00-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="90e00-139">De **Solution Explorer**, ouvrez le fichier **IService1.cs** ou **IService1.vb,** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="90e00-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="90e00-140">Ce contrat définit une calculatrice en ligne.</span><span class="sxs-lookup"><span data-stu-id="90e00-140">This contract defines an online calculator.</span></span> <span data-ttu-id="90e00-141">Notez `ICalculator` que l’interface est marquée avec l’attribut <xref:System.ServiceModel.ServiceContractAttribute> (simplifié comme `ServiceContract`).</span><span class="sxs-lookup"><span data-stu-id="90e00-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="90e00-142">Cet attribut définit un espace de nom pour désambiguer le nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="90e00-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="90e00-143">Le code marque chaque <xref:System.ServiceModel.OperationContractAttribute> opération de `OperationContract`calculatrice avec l’attribut (simplifié comme ).</span><span class="sxs-lookup"><span data-stu-id="90e00-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="90e00-144">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="90e00-144">Next steps</span></span>

<span data-ttu-id="90e00-145">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="90e00-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="90e00-146">Créez un projet de bibliothèque de services WCF.</span><span class="sxs-lookup"><span data-stu-id="90e00-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="90e00-147">Définissez une interface de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="90e00-147">Define a service contract interface.</span></span>

<span data-ttu-id="90e00-148">Avancez au tutoriel suivant pour apprendre à mettre en œuvre le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="90e00-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="90e00-149">Tutorial: Mettre en œuvre un contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="90e00-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
