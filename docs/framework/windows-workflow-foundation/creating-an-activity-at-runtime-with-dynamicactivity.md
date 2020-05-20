---
title: Création d'une activité en cours d'exécution avec DynamicActivity
description: DynamicActivity est une classe concrète et sealed avec un constructeur public. Utilisez la classe pour assembler les fonctionnalités d’activité au moment de l’exécution à l’aide d’un DOM d’activité.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: 17ee14be7df4801018c7afd2e91f1fb07c34e8e1
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421538"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="2a85d-104">Création d'une activité en cours d'exécution avec DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="2a85d-104">Creating an Activity at Runtime with DynamicActivity</span></span>
<span data-ttu-id="2a85d-105"><xref:System.Activities.DynamicActivity> est une classe concrète et scellée avec un constructeur public.</span><span class="sxs-lookup"><span data-stu-id="2a85d-105"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="2a85d-106"><xref:System.Activities.DynamicActivity> peut servir à assembler les fonctionnalités d'activité au moment de l'exécution à l'aide d'un DOM d'activité.</span><span class="sxs-lookup"><span data-stu-id="2a85d-106"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="2a85d-107">Fonctionnalités DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="2a85d-107">DynamicActivity Features</span></span>  
 <span data-ttu-id="2a85d-108">L'objet <xref:System.Activities.DynamicActivity> a accès aux propriétés d'exécution et aux arguments et variables, mais pas aux services d'exécution comme la planification d'activités enfants ou le suivi.</span><span class="sxs-lookup"><span data-stu-id="2a85d-108"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="2a85d-109">Les propriétés de niveau supérieur peuvent être définies à l'aide des objets <xref:System.Activities.Argument> du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="2a85d-109">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="2a85d-110">En code impératif, ces arguments sont créés à l'aide de propriétés CLR sur un nouveau type.</span><span class="sxs-lookup"><span data-stu-id="2a85d-110">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="2a85d-111">En XAML, ils sont déclarés à l’aide d’étiquettes `x:Class` et `x:Member`.</span><span class="sxs-lookup"><span data-stu-id="2a85d-111">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="2a85d-112">Les activités sont générées à l'aide de l'interface <xref:System.Activities.DynamicActivity> avec le concepteur utilisant l'objet <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="2a85d-112">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="2a85d-113">Les activités créées dans le concepteur peuvent être chargées dynamiquement à l'aide de la méthode <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, comme le montre la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="2a85d-113">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="2a85d-114">Pour créer une activité au moment de l'exécution à l'aide du code impératif</span><span class="sxs-lookup"><span data-stu-id="2a85d-114">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="2a85d-115">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="2a85d-115">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="2a85d-116">Sélectionnez **fichier**, **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="2a85d-116">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="2a85d-117">Sélectionnez **Workflow 4,0** sous **Visual C#** dans la fenêtre **types de projets** , puis sélectionnez le nœud **v2010** .</span><span class="sxs-lookup"><span data-stu-id="2a85d-117">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="2a85d-118">Sélectionnez **application console de workflow séquentiel** dans la fenêtre **modèles** .</span><span class="sxs-lookup"><span data-stu-id="2a85d-118">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="2a85d-119">Nommez le nouveau projet « DynamicActivitySample ».</span><span class="sxs-lookup"><span data-stu-id="2a85d-119">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="2a85d-120">Cliquez avec le bouton droit sur Workflow1. xaml dans le projet HelloActivity, puis sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="2a85d-120">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="2a85d-121">Ouvrez le fichier Program.cs.</span><span class="sxs-lookup"><span data-stu-id="2a85d-121">Open Program.cs.</span></span> <span data-ttu-id="2a85d-122">Ajoutez la directive suivante en début de fichier.</span><span class="sxs-lookup"><span data-stu-id="2a85d-122">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="2a85d-123">Remplacez le contenu de la méthode `Main` par le code ci-dessous. Ce dernier crée une activité <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> unique et l'affecte à la propriété <xref:System.Activities.DynamicActivity.Implementation%2A> d'une nouvelle activité dynamique.</span><span class="sxs-lookup"><span data-stu-id="2a85d-123">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6. <span data-ttu-id="2a85d-124">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="2a85d-124">Execute the application.</span></span> <span data-ttu-id="2a85d-125">Fenêtre de console avec le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="2a85d-125">A console window with the text "Hello World!"</span></span> <span data-ttu-id="2a85d-126">affiche.</span><span class="sxs-lookup"><span data-stu-id="2a85d-126">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="2a85d-127">Pour créer une activité au moment de l'exécution à l'aide de XAML</span><span class="sxs-lookup"><span data-stu-id="2a85d-127">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="2a85d-128">Ouvrez Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="2a85d-128">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="2a85d-129">Sélectionnez **fichier**, **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="2a85d-129">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="2a85d-130">Sélectionnez **Workflow 4,0** sous **Visual C#** dans la fenêtre **types de projets** , puis sélectionnez le nœud **v2010** .</span><span class="sxs-lookup"><span data-stu-id="2a85d-130">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="2a85d-131">Dans la fenêtre **modèles** , sélectionnez **application console de workflow** .</span><span class="sxs-lookup"><span data-stu-id="2a85d-131">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="2a85d-132">Nommez le nouveau projet « DynamicActivitySample ».</span><span class="sxs-lookup"><span data-stu-id="2a85d-132">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="2a85d-133">Dans le projet HelloActivity, ouvrez Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="2a85d-133">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="2a85d-134">Cliquez sur l’option **arguments** au bas du concepteur.</span><span class="sxs-lookup"><span data-stu-id="2a85d-134">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="2a85d-135">Créez un argument `In` appelé `TextToWrite` de type `String`.</span><span class="sxs-lookup"><span data-stu-id="2a85d-135">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="2a85d-136">Faites glisser une activité **WriteLine** de la section **primitives** de la boîte à outils vers l’aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="2a85d-136">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="2a85d-137">Assignez la valeur `TextToWrite` à la propriété **Text** de l’activité.</span><span class="sxs-lookup"><span data-stu-id="2a85d-137">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="2a85d-138">Ouvrez le fichier Program.cs.</span><span class="sxs-lookup"><span data-stu-id="2a85d-138">Open Program.cs.</span></span> <span data-ttu-id="2a85d-139">Ajoutez la directive suivante en début de fichier.</span><span class="sxs-lookup"><span data-stu-id="2a85d-139">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="2a85d-140">Remplacez le contenu de la méthode `Main` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2a85d-140">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="2a85d-141">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="2a85d-141">Execute the application.</span></span> <span data-ttu-id="2a85d-142">Fenêtre de console avec le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="2a85d-142">A console window with the text "Hello World!"</span></span> <span data-ttu-id="2a85d-143"> s’affiche.</span><span class="sxs-lookup"><span data-stu-id="2a85d-143">appears.</span></span>  
  
8. <span data-ttu-id="2a85d-144">Cliquez avec le bouton droit sur le fichier Workflow1. xaml dans le **Explorateur de solutions** , puis sélectionnez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="2a85d-144">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="2a85d-145">Notez que la classe d'activité est créée avec `x:Class` et que la propriété est créée avec `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="2a85d-145">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a85d-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a85d-146">See also</span></span>

- [<span data-ttu-id="2a85d-147">Création de workflows, d’activités et d’expressions à l’aide du code impératif</span><span class="sxs-lookup"><span data-stu-id="2a85d-147">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
