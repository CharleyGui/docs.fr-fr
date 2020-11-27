---
title: Création de l'activité de workflow à l'aide de la classe CodeActivity
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 714e0971a006db20d002b0f3a486533b1357fba7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293817"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a><span data-ttu-id="69d59-102">Création de l'activité de workflow à l'aide de la classe CodeActivity</span><span class="sxs-lookup"><span data-stu-id="69d59-102">Workflow Activity Authoring Using the CodeActivity Class</span></span>

<span data-ttu-id="69d59-103">Les activités créées en héritant de <xref:System.Activities.CodeActivity> peuvent implémenter un comportement impératif de base en remplaçant la méthode <xref:System.Activities.CodeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="69d59-103">Activities created by inheriting from <xref:System.Activities.CodeActivity> can implement basic imperative behavior by overriding the <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

## <a name="using-codeactivitycontext"></a><span data-ttu-id="69d59-104">Utilisation de CodeActivityContext</span><span class="sxs-lookup"><span data-stu-id="69d59-104">Using CodeActivityContext</span></span>

 <span data-ttu-id="69d59-105">Les fonctionnalités de l'exécution du workflow sont accessibles à partir de la méthode <xref:System.Activities.CodeActivity.Execute%2A> en utilisant les membres du paramètre `context`, de type <xref:System.Activities.CodeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="69d59-105">Features of the workflow runtime can be accessed from within the <xref:System.Activities.CodeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.CodeActivityContext>.</span></span> <span data-ttu-id="69d59-106">Les fonctionnalités disponibles via <xref:System.Activities.CodeActivityContext> sont notamment :</span><span class="sxs-lookup"><span data-stu-id="69d59-106">The features available through <xref:System.Activities.CodeActivityContext> include the following:</span></span>

- <span data-ttu-id="69d59-107">Obtention et définition des valeurs de variables et d’arguments.</span><span class="sxs-lookup"><span data-stu-id="69d59-107">Getting and setting the values of variables and arguments.</span></span>

- <span data-ttu-id="69d59-108">Fonctionnalités de suivi personnalisées à l'aide de <xref:System.Activities.CodeActivityContext.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="69d59-108">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="69d59-109">Accès aux propriétés d'exécution de l'activité à l'aide de <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="69d59-109">Access to the activity’s execution properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A>.</span></span>

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a><span data-ttu-id="69d59-110">Pour créer une activité personnalisée qui hérite de CodeActivity</span><span class="sxs-lookup"><span data-stu-id="69d59-110">To create a custom activity that inherits from CodeActivity</span></span>

1. <span data-ttu-id="69d59-111">Ouvrez Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="69d59-111">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="69d59-112">Sélectionnez **fichier**, **nouveau**, puis **projet**.</span><span class="sxs-lookup"><span data-stu-id="69d59-112">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="69d59-113">Sélectionnez **Workflow 4,0** sous **Visual C#** dans la fenêtre **types de projets** , puis sélectionnez le nœud **v2010** .</span><span class="sxs-lookup"><span data-stu-id="69d59-113">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="69d59-114">Sélectionnez **bibliothèque d’activités** dans la fenêtre **modèles** .</span><span class="sxs-lookup"><span data-stu-id="69d59-114">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="69d59-115">Nommez le nouveau projet HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="69d59-115">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="69d59-116">Cliquez avec le bouton droit sur Activity1. xaml dans le projet HelloActivity, puis sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="69d59-116">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="69d59-117">Cliquez avec le bouton droit sur le projet HelloActivity et sélectionnez **Ajouter** , puis **classe**.</span><span class="sxs-lookup"><span data-stu-id="69d59-117">Right-click the HelloActivity project and select **Add** , and then **Class**.</span></span> <span data-ttu-id="69d59-118">Nommez la nouvelle classe HelloActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="69d59-118">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="69d59-119">Dans le fichier HelloActivity.cs, ajoutez les directives `using` suivantes.</span><span class="sxs-lookup"><span data-stu-id="69d59-119">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="69d59-120">Faites en sorte que la nouvelle classe hérite de <xref:System.Activities.CodeActivity> en ajoutant une classe de base à la déclaration de classe.</span><span class="sxs-lookup"><span data-stu-id="69d59-120">Make the new class inherit from <xref:System.Activities.CodeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. <span data-ttu-id="69d59-121">Ajoutez des fonctionnalités à la classe en ajoutant une méthode <xref:System.Activities.CodeActivity.Execute%2A>.</span><span class="sxs-lookup"><span data-stu-id="69d59-121">Add functionality to the class by adding an <xref:System.Activities.CodeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="69d59-122">Utilisez le <xref:System.Activities.CodeActivityContext> pour créer un enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="69d59-122">Use the <xref:System.Activities.CodeActivityContext> to create a tracking record.</span></span>

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
