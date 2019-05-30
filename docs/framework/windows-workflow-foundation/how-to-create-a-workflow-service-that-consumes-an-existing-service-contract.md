---
title: 'Procédure : créer un service de workflow qui consomme un contrat de service existant'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 82c9ccc21600ae0b9ff8c514a51ec9b97f8f1d37
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378129"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="2af50-102">Procédure : créer un service de workflow qui consomme un contrat de service existant</span><span class="sxs-lookup"><span data-stu-id="2af50-102">How to: Create a workflow service that consumes an existing service contract</span></span>
<span data-ttu-id="2af50-103">Fonctionnalités de .NET framework 4.5 une meilleure intégration entre les services web et les workflows sous la forme du développement de workflow contrat en premier.</span><span class="sxs-lookup"><span data-stu-id="2af50-103">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="2af50-104">L'outil de développement de workflow Contrat en premier vous permet de concevoir le contrat dans le code en premier.</span><span class="sxs-lookup"><span data-stu-id="2af50-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="2af50-105">L'outil génère automatiquement un modèle d'activité dans la boîte à outils pour les opérations du contrat.</span><span class="sxs-lookup"><span data-stu-id="2af50-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2af50-106">Cette rubrique fournit des instructions pas à pas pour créer un service de workflow contrat en premier.</span><span class="sxs-lookup"><span data-stu-id="2af50-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="2af50-107">Pour plus d’informations sur le développement de service de workflow contrat en premier, consultez [contrat premier Workflow Service développement](contract-first-workflow-service-development.md).</span><span class="sxs-lookup"><span data-stu-id="2af50-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="2af50-108">Création du projet de workflow</span><span class="sxs-lookup"><span data-stu-id="2af50-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="2af50-109">Dans Visual Studio, sélectionnez **fichier**, **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="2af50-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="2af50-110">Sélectionnez le **WCF** nœud sous la **C#** nœud dans le **modèles** arborescence, puis sélectionnez le **Application de Service de Workflow WCF** modèle.</span><span class="sxs-lookup"><span data-stu-id="2af50-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="2af50-111">Nommez le nouveau projet `ContractFirst` et cliquez sur **Ok**.</span><span class="sxs-lookup"><span data-stu-id="2af50-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="2af50-112">Création du contrat de service</span><span class="sxs-lookup"><span data-stu-id="2af50-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="2af50-113">Cliquez sur le projet dans **l’Explorateur de solutions** et sélectionnez **ajouter**, **un nouvel élément...** .</span><span class="sxs-lookup"><span data-stu-id="2af50-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="2af50-114">Sélectionnez le **Code** nœud sur la gauche et le **classe** modèle sur la droite.</span><span class="sxs-lookup"><span data-stu-id="2af50-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="2af50-115">Nommez la nouvelle classe `IBookService` et cliquez sur **Ok**.</span><span class="sxs-lookup"><span data-stu-id="2af50-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="2af50-116">En haut de la fenêtre de code qui apparaît, ajoutez une instruction Using à `System.Servicemodel`.</span><span class="sxs-lookup"><span data-stu-id="2af50-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="2af50-117">Remplacez la définition d'exemple de classe par la définition d'interface suivante.</span><span class="sxs-lookup"><span data-stu-id="2af50-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="2af50-118">Générez le projet en appuyant sur **Ctrl + Maj + B**.</span><span class="sxs-lookup"><span data-stu-id="2af50-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="2af50-119">Importation du contrat de service</span><span class="sxs-lookup"><span data-stu-id="2af50-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="2af50-120">Cliquez sur le projet dans **l’Explorateur de solutions** et sélectionnez **importer le contrat de Service**.</span><span class="sxs-lookup"><span data-stu-id="2af50-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="2af50-121">Sous  **\<projet actif >** , ouvrez tous les sous-nœuds et sélectionnez **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="2af50-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="2af50-122">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2af50-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="2af50-123">Une boîte de dialogue s'ouvre indiquant que l'opération s'est achevée avec succès et que les activités personnalisées générées s'afficheront dans la boîte à outils une fois le projet construit.</span><span class="sxs-lookup"><span data-stu-id="2af50-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="2af50-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2af50-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="2af50-125">Générez le projet en appuyant sur **Ctrl + Maj + B**, de sorte que les activités importées s’affichent dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="2af50-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="2af50-126">Dans **l’Explorateur de solutions**, ouvrez Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="2af50-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="2af50-127">Le service de workflow apparaît dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="2af50-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="2af50-128">Sélectionnez le **séquence** activité.</span><span class="sxs-lookup"><span data-stu-id="2af50-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="2af50-129">Dans la fenêtre Propriétés, cliquez sur le **...**</span><span class="sxs-lookup"><span data-stu-id="2af50-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="2af50-130">bouton dans le **ImplementedContract** propriété.</span><span class="sxs-lookup"><span data-stu-id="2af50-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="2af50-131">Dans le **éditeur de collections de Type** fenêtre qui s’affiche, cliquez sur le **Type** liste déroulante, puis sélectionnez le **rechercher des Types...**</span><span class="sxs-lookup"><span data-stu-id="2af50-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="2af50-132">entrée.</span><span class="sxs-lookup"><span data-stu-id="2af50-132">entry.</span></span> <span data-ttu-id="2af50-133">Dans le **rechercher et sélectionner un Type .NET** boîte de dialogue, sous  **\<projet actif >** , ouvrez tous les sous-nœuds et sélectionnez **IBookService**.</span><span class="sxs-lookup"><span data-stu-id="2af50-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="2af50-134">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2af50-134">Click **OK**.</span></span> <span data-ttu-id="2af50-135">Dans le **éditeur de collections de Type** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2af50-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="2af50-136">Sélectionnez et supprimez le **ReceiveRequest** et **SendResponse** activités.</span><span class="sxs-lookup"><span data-stu-id="2af50-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="2af50-137">Dans la boîte à outils, faites glisser un **Buy_ReceiveAndSendReply** et un **Checkout_Receive** activité sur le **Service séquentiel** activité.</span><span class="sxs-lookup"><span data-stu-id="2af50-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
