---
title: 'Tutoriel : Définir un contrat de service Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: ba88fc6ba4cba8d46ed1b43080d471b1b7c4bd75
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928873"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="723f6-102">Tutoriel : Définir un contrat de service Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="723f6-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="723f6-103">Ce didacticiel décrit la première des cinq tâches requises pour créer une application de base Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="723f6-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="723f6-104">Pour obtenir une vue d’ensemble des didacticiels, consultez [didacticiel : Prise en main des applications](getting-started-tutorial.md)Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="723f6-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="723f6-105">Lorsque vous créez un service WCF, votre première tâche consiste à définir un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="723f6-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="723f6-106">Le contrat de service spécifie les opérations prises en charge par le service.</span><span class="sxs-lookup"><span data-stu-id="723f6-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="723f6-107">Une opération peut être considérée comme une méthode de service Web.</span><span class="sxs-lookup"><span data-stu-id="723f6-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="723f6-108">Vous créez des contrats de service en définissant une interface Visual C# ou Visual Basic (VB).</span><span class="sxs-lookup"><span data-stu-id="723f6-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="723f6-109">Une interface possède les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="723f6-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="723f6-110">Chaque méthode dans l'interface correspond à une opération de service spécifique.</span><span class="sxs-lookup"><span data-stu-id="723f6-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="723f6-111">Pour chaque interface, vous devez appliquer l' <xref:System.ServiceModel.ServiceContractAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="723f6-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="723f6-112">Pour chaque opération/méthode, vous devez appliquer l' <xref:System.ServiceModel.OperationContractAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="723f6-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="723f6-113">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="723f6-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="723f6-114">Créez un projet de **bibliothèque de service WCF** .</span><span class="sxs-lookup"><span data-stu-id="723f6-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="723f6-115">Définissez une interface de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="723f6-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="723f6-116">Créer un projet de bibliothèque de service WCF et définir une interface de contrat de service</span><span class="sxs-lookup"><span data-stu-id="723f6-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="723f6-117">Ouvrez Visual Studio en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="723f6-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="723f6-118">Pour ce faire, sélectionnez le programme Visual Studio dans le menu **Démarrer** , puis sélectionnez **plus** > **exécuter en tant qu’administrateur** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="723f6-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="723f6-119">Créez un projet de **bibliothèque de service WCF** .</span><span class="sxs-lookup"><span data-stu-id="723f6-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="723f6-120">Dans le menu **Fichier**, sélectionnez **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="723f6-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="723f6-121">Dans la boîte de dialogue **nouveau projet** , sur le côté gauche, développez  **C# Visual** ou **Visual Basic**, puis sélectionnez la catégorie **WCF** .</span><span class="sxs-lookup"><span data-stu-id="723f6-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="723f6-122">Visual Studio affiche une liste de modèles de projet dans la section centrale de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="723f6-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="723f6-123">Sélectionnez **bibliothèque de services WCF**.</span><span class="sxs-lookup"><span data-stu-id="723f6-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="723f6-124">Si vous ne voyez pas la catégorie de modèle de projet **WCF** , vous devrez peut-être installer le composant **Windows Communication Foundation** de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="723f6-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="723f6-125">Dans la boîte de dialogue **nouveau projet** , sélectionnez le lien **ouvrir le Visual Studio installer** sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="723f6-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="723f6-126">Sélectionnez l’onglet **composants individuels** , puis recherchez et sélectionnez **Windows Communication Foundation** sous la catégorie **activités de développement** .</span><span class="sxs-lookup"><span data-stu-id="723f6-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="723f6-127">Choisissez **modifier** pour commencer l’installation du composant.</span><span class="sxs-lookup"><span data-stu-id="723f6-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="723f6-128">Dans la section inférieure de la fenêtre, entrez *GettingStartedLib* pour le **nom** et *gettingstarted* pour le **nom**de la solution.</span><span class="sxs-lookup"><span data-stu-id="723f6-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="723f6-129">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="723f6-129">Select **OK**.</span></span>

      <span data-ttu-id="723f6-130">Visual Studio crée le projet, qui contient trois fichiers : *IService1.cs* (ou *IService1. vb* pour un projet Visual Basic), *Service1.cs* (ou *Service1. vb* pour un projet Visual Basic) et *app. config*. Visual Studio définit ces fichiers comme suit :</span><span class="sxs-lookup"><span data-stu-id="723f6-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="723f6-131">Le fichier *IService1* contient la définition par défaut du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="723f6-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="723f6-132">Le fichier *Service1* contient l’implémentation par défaut du contrat de service.</span><span class="sxs-lookup"><span data-stu-id="723f6-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="723f6-133">Le fichier *app. config* contient les informations de configuration nécessaires au chargement du service par défaut avec l’outil hôte de service WCF de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="723f6-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="723f6-134">Pour plus d’informations sur l’outil hôte de service WCF, consultez [hôte de service WCF (WcfSvcHost. exe)](wcf-service-host-wcfsvchost-exe.md).</span><span class="sxs-lookup"><span data-stu-id="723f6-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="723f6-135">Si vous avez installé Visual Studio avec Visual Basic paramètres d’environnement de développement, la solution peut être masquée.</span><span class="sxs-lookup"><span data-stu-id="723f6-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="723f6-136">Si c’est le cas, sélectionnez **options** dans le menu **Outils** , puis sélectionnez **projets et solutions** > **général** dans la fenêtre **options** .</span><span class="sxs-lookup"><span data-stu-id="723f6-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="723f6-137">Sélectionnez **toujours afficher la solution**.</span><span class="sxs-lookup"><span data-stu-id="723f6-137">Select **Always show solution**.</span></span> <span data-ttu-id="723f6-138">Vérifiez également que l’option **enregistrer les nouveaux projets lors de la création** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="723f6-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="723f6-139">À partir de **Explorateur de solutions**, ouvrez le fichier **IService1.cs** ou **IService1. vb** et remplacez son code par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="723f6-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="723f6-140">Ce contrat définit une calculatrice en ligne.</span><span class="sxs-lookup"><span data-stu-id="723f6-140">This contract defines an online calculator.</span></span> <span data-ttu-id="723f6-141">Notez que `ICalculator` l’interface est marquée avec <xref:System.ServiceModel.ServiceContractAttribute> l’attribut (simplifiée en tant que `ServiceContract`).</span><span class="sxs-lookup"><span data-stu-id="723f6-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="723f6-142">Cet attribut définit un espace de noms pour lever toute ambiguïté sur le nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="723f6-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="723f6-143">Le code marque chaque opération de calculatrice avec <xref:System.ServiceModel.OperationContractAttribute> l’attribut (simplifié `OperationContract`comme).</span><span class="sxs-lookup"><span data-stu-id="723f6-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="723f6-144">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="723f6-144">Next steps</span></span>

<span data-ttu-id="723f6-145">Dans ce tutoriel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="723f6-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="723f6-146">Créez un projet de bibliothèque de service WCF.</span><span class="sxs-lookup"><span data-stu-id="723f6-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="723f6-147">Définissez une interface de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="723f6-147">Define a service contract interface.</span></span>

<span data-ttu-id="723f6-148">Passez au didacticiel suivant pour découvrir comment implémenter le contrat de service WCF.</span><span class="sxs-lookup"><span data-stu-id="723f6-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="723f6-149">Tutoriel : Implémenter un contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="723f6-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
