---
title: Création d'une activité en cours d'exécution avec DynamicActivity
description: DynamicActivity est une classe concrète et sealed avec un constructeur public. Utilisez la classe pour assembler les fonctionnalités d’activité au moment de l’exécution à l’aide d’un DOM d’activité.
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: b65d7e385690b77d44c73e7a8a4ed38b04f30ea6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242095"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="d6430-104">Création d'une activité en cours d'exécution avec DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="d6430-104">Creating an Activity at Runtime with DynamicActivity</span></span>

<span data-ttu-id="d6430-105"><xref:System.Activities.DynamicActivity> est une classe concrète et scellée avec un constructeur public.</span><span class="sxs-lookup"><span data-stu-id="d6430-105"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="d6430-106"><xref:System.Activities.DynamicActivity> peut servir à assembler les fonctionnalités d'activité au moment de l'exécution à l'aide d'un DOM d'activité.</span><span class="sxs-lookup"><span data-stu-id="d6430-106"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="d6430-107">Fonctionnalités DynamicActivity</span><span class="sxs-lookup"><span data-stu-id="d6430-107">DynamicActivity Features</span></span>  

 <span data-ttu-id="d6430-108">L'objet <xref:System.Activities.DynamicActivity> a accès aux propriétés d'exécution et aux arguments et variables, mais pas aux services d'exécution comme la planification d'activités enfants ou le suivi.</span><span class="sxs-lookup"><span data-stu-id="d6430-108"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="d6430-109">Les propriétés de niveau supérieur peuvent être définies à l'aide des objets <xref:System.Activities.Argument> du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="d6430-109">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="d6430-110">En code impératif, ces arguments sont créés à l'aide de propriétés CLR sur un nouveau type.</span><span class="sxs-lookup"><span data-stu-id="d6430-110">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="d6430-111">En XAML, ils sont déclarés à l’aide d’étiquettes `x:Class` et `x:Member`.</span><span class="sxs-lookup"><span data-stu-id="d6430-111">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="d6430-112">Les activités sont générées à l'aide de l'interface <xref:System.Activities.DynamicActivity> avec le concepteur utilisant l'objet <xref:System.ComponentModel.ICustomTypeDescriptor>.</span><span class="sxs-lookup"><span data-stu-id="d6430-112">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="d6430-113">Les activités créées dans le concepteur peuvent être chargées dynamiquement à l'aide de la méthode <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, comme le montre la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="d6430-113">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="d6430-114">Pour créer une activité au moment de l'exécution à l'aide du code impératif</span><span class="sxs-lookup"><span data-stu-id="d6430-114">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="d6430-115">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="d6430-115">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="d6430-116">Sélectionnez **fichier**, **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="d6430-116">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="d6430-117">Sélectionnez **Workflow 4,0** sous **Visual C#** dans la fenêtre **types de projets** , puis sélectionnez le nœud **v2010** .</span><span class="sxs-lookup"><span data-stu-id="d6430-117">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="d6430-118">Sélectionnez **application console de workflow séquentiel** dans la fenêtre **modèles** .</span><span class="sxs-lookup"><span data-stu-id="d6430-118">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="d6430-119">Nommez le nouveau projet « DynamicActivitySample ».</span><span class="sxs-lookup"><span data-stu-id="d6430-119">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="d6430-120">Cliquez avec le bouton droit sur Workflow1. xaml dans le projet HelloActivity, puis sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="d6430-120">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="d6430-121">Ouvrez le fichier Program.cs.</span><span class="sxs-lookup"><span data-stu-id="d6430-121">Open Program.cs.</span></span> <span data-ttu-id="d6430-122">Ajoutez la directive suivante en début de fichier.</span><span class="sxs-lookup"><span data-stu-id="d6430-122">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="d6430-123">Remplacez le contenu de la méthode `Main` par le code ci-dessous. Ce dernier crée une activité <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> unique et l'affecte à la propriété <xref:System.Activities.DynamicActivity.Implementation%2A> d'une nouvelle activité dynamique.</span><span class="sxs-lookup"><span data-stu-id="d6430-123">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
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
  
6. <span data-ttu-id="d6430-124">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d6430-124">Execute the application.</span></span> <span data-ttu-id="d6430-125">Fenêtre de console avec le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="d6430-125">A console window with the text "Hello World!"</span></span> <span data-ttu-id="d6430-126">affiche.</span><span class="sxs-lookup"><span data-stu-id="d6430-126">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="d6430-127">Pour créer une activité au moment de l'exécution à l'aide de XAML</span><span class="sxs-lookup"><span data-stu-id="d6430-127">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="d6430-128">Ouvrez Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="d6430-128">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="d6430-129">Sélectionnez **fichier**, **nouveau**, **projet**.</span><span class="sxs-lookup"><span data-stu-id="d6430-129">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="d6430-130">Sélectionnez **Workflow 4,0** sous **Visual C#** dans la fenêtre **types de projets** , puis sélectionnez le nœud **v2010** .</span><span class="sxs-lookup"><span data-stu-id="d6430-130">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="d6430-131">Dans la fenêtre **modèles** , sélectionnez **application console de workflow** .</span><span class="sxs-lookup"><span data-stu-id="d6430-131">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="d6430-132">Nommez le nouveau projet « DynamicActivitySample ».</span><span class="sxs-lookup"><span data-stu-id="d6430-132">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="d6430-133">Dans le projet HelloActivity, ouvrez Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="d6430-133">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="d6430-134">Cliquez sur l’option **arguments** au bas du concepteur.</span><span class="sxs-lookup"><span data-stu-id="d6430-134">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="d6430-135">Créez un argument `In` appelé `TextToWrite` de type `String`.</span><span class="sxs-lookup"><span data-stu-id="d6430-135">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="d6430-136">Faites glisser une activité **WriteLine** de la section **primitives** de la boîte à outils vers l’aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="d6430-136">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="d6430-137">Assignez la valeur `TextToWrite` à la propriété **Text** de l’activité.</span><span class="sxs-lookup"><span data-stu-id="d6430-137">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="d6430-138">Ouvrez le fichier Program.cs.</span><span class="sxs-lookup"><span data-stu-id="d6430-138">Open Program.cs.</span></span> <span data-ttu-id="d6430-139">Ajoutez la directive suivante en début de fichier.</span><span class="sxs-lookup"><span data-stu-id="d6430-139">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="d6430-140">Remplacez le contenu de la méthode `Main` par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d6430-140">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="d6430-141">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="d6430-141">Execute the application.</span></span> <span data-ttu-id="d6430-142">Fenêtre de console avec le texte « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="d6430-142">A console window with the text "Hello World!"</span></span> <span data-ttu-id="d6430-143"> s’affiche.</span><span class="sxs-lookup"><span data-stu-id="d6430-143">appears.</span></span>  
  
8. <span data-ttu-id="d6430-144">Cliquez avec le bouton droit sur le fichier Workflow1. xaml dans le **Explorateur de solutions** , puis sélectionnez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="d6430-144">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="d6430-145">Notez que la classe d'activité est créée avec `x:Class` et que la propriété est créée avec `x:Property`.</span><span class="sxs-lookup"><span data-stu-id="d6430-145">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6430-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6430-146">See also</span></span>

- [<span data-ttu-id="d6430-147">Création de workflows, d'activités et d'expressions à l'aide du code impératif</span><span class="sxs-lookup"><span data-stu-id="d6430-147">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
