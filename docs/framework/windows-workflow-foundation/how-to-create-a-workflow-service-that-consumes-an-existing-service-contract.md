---
title: 'Procédure : créer un service de workflow qui consomme un contrat de service existant'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 05c59bde424049eb5bef8f8bd09c472b58eaa9ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248823"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="3979a-102">Procédure : créer un service de workflow qui consomme un contrat de service existant</span><span class="sxs-lookup"><span data-stu-id="3979a-102">How to: Create a workflow service that consumes an existing service contract</span></span>

<span data-ttu-id="3979a-103">.NET Framework 4,5 offre une meilleure intégration entre les services Web et les workflows sous la forme d’un développement de workflow contrat en premier.</span><span class="sxs-lookup"><span data-stu-id="3979a-103">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="3979a-104">L'outil de développement de workflow Contrat en premier vous permet de concevoir le contrat dans le code en premier.</span><span class="sxs-lookup"><span data-stu-id="3979a-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="3979a-105">L'outil génère automatiquement un modèle d'activité dans la boîte à outils pour les opérations du contrat.</span><span class="sxs-lookup"><span data-stu-id="3979a-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3979a-106">Cette rubrique fournit des instructions pas à pas pour créer un service de workflow contrat en premier.</span><span class="sxs-lookup"><span data-stu-id="3979a-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="3979a-107">Pour plus d’informations sur le développement d’un service de workflow contrat en premier, consultez développement d’un [service de flux de travail en premier contrat](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="3979a-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="3979a-108">Création du projet de workflow</span><span class="sxs-lookup"><span data-stu-id="3979a-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="3979a-109">Dans Visual Studio, sélectionnez **Fichier**, **Nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="3979a-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="3979a-110">Sélectionnez le nœud **WCF** sous le nœud **C#** dans l’arborescence **modèles** , puis sélectionnez le modèle application de service de flux de **travail WCF** .</span><span class="sxs-lookup"><span data-stu-id="3979a-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="3979a-111">Nommez le nouveau projet `ContractFirst` , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3979a-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="3979a-112">Création du contrat de service</span><span class="sxs-lookup"><span data-stu-id="3979a-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="3979a-113">Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter**, **nouvel élément...**.</span><span class="sxs-lookup"><span data-stu-id="3979a-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="3979a-114">Sélectionnez le nœud **code** sur la gauche, et le modèle de **classe** à droite.</span><span class="sxs-lookup"><span data-stu-id="3979a-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="3979a-115">Nommez la nouvelle classe `IBookService` , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3979a-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="3979a-116">En haut de la fenêtre de code qui apparaît, ajoutez une instruction Using à `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="3979a-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="3979a-117">Remplacez la définition d'exemple de classe par la définition d'interface suivante.</span><span class="sxs-lookup"><span data-stu-id="3979a-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="3979a-118">Générez le projet en appuyant sur **Ctrl + Maj + B**.</span><span class="sxs-lookup"><span data-stu-id="3979a-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="3979a-119">Importation du contrat de service</span><span class="sxs-lookup"><span data-stu-id="3979a-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="3979a-120">Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis sélectionnez **importer le contrat de service**.</span><span class="sxs-lookup"><span data-stu-id="3979a-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="3979a-121">Sous **\<Current Project>** , ouvrez tous les sous-nœuds et sélectionnez **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="3979a-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="3979a-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3979a-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="3979a-123">Une boîte de dialogue s'ouvre indiquant que l'opération s'est achevée avec succès et que les activités personnalisées générées s'afficheront dans la boîte à outils une fois le projet construit.</span><span class="sxs-lookup"><span data-stu-id="3979a-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="3979a-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3979a-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="3979a-125">Générez le projet en appuyant sur **Ctrl + Maj + B**, afin que les activités importées s’affichent dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="3979a-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="3979a-126">Dans **Explorateur de solutions**, ouvrez Service1. xamlx.</span><span class="sxs-lookup"><span data-stu-id="3979a-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="3979a-127">Le service de workflow apparaît dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="3979a-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="3979a-128">Sélectionnez l’activité **séquence** .</span><span class="sxs-lookup"><span data-stu-id="3979a-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="3979a-129">Dans le Fenêtre Propriétés, cliquez sur **...**</span><span class="sxs-lookup"><span data-stu-id="3979a-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="3979a-130">dans la propriété **ImplementedContract** .</span><span class="sxs-lookup"><span data-stu-id="3979a-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="3979a-131">Dans la fenêtre de l' **éditeur de collections type** qui s’affiche, cliquez sur la liste déroulante **type** , puis sélectionnez **Rechercher des types...**</span><span class="sxs-lookup"><span data-stu-id="3979a-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="3979a-132">mention.</span><span class="sxs-lookup"><span data-stu-id="3979a-132">entry.</span></span> <span data-ttu-id="3979a-133">Dans la boîte de dialogue **Rechercher et sélectionner un type .net** , sous **\<Current Project>** , ouvrez tous les sous-nœuds et sélectionnez **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="3979a-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="3979a-134">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3979a-134">Click **OK**.</span></span> <span data-ttu-id="3979a-135">Dans la boîte de dialogue **éditeur de collections de types** , cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3979a-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="3979a-136">Sélectionnez et supprimez les activités **ReceiveRequest** et **SendResponse** .</span><span class="sxs-lookup"><span data-stu-id="3979a-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="3979a-137">À partir de la boîte à outils, faites glisser un **Buy_ReceiveAndSendReply** et une activité de **Checkout_Receive** sur l’activité de **service séquentielle** .</span><span class="sxs-lookup"><span data-stu-id="3979a-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
