---
title: ParallelForEach non générique
ms.date: 03/30/2017
ms.assetid: de17e7a2-257b-48b3-91a1-860e2e9bf6e6
ms.openlocfilehash: ea7f57b8812dca3dfcb4908730dd788182d50c5c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347619"
---
# <a name="non-generic-parallelforeach"></a><span data-ttu-id="b14e8-102">ParallelForEach non générique</span><span class="sxs-lookup"><span data-stu-id="b14e8-102">Non-generic ParallelForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="b14e8-103">fournit, dans sa boîte à outils, un ensemble d'activités de flux de contrôle, notamment <xref:System.Activities.Statements.ParallelForEach%601>, qui permet l'itération au sein des collections <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b14e8-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ParallelForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>

<span data-ttu-id="b14e8-104"><xref:System.Activities.Statements.ParallelForEach%601> nécessite que sa propriété <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> soit de type <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b14e8-104"><xref:System.Activities.Statements.ParallelForEach%601> requires its <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> property to be of type  <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b14e8-105">Cela empêche les utilisateurs d'itérer au sein des structures de données qui implémentent l'interface <xref:System.Collections.Generic.IEnumerable%601> (par exemple, <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="b14e8-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="b14e8-106">La version non générique de <xref:System.Activities.Statements.ParallelForEach%601> passe outre cette exigence, aux dépens d’un runtime plus complexe afin de garantir la compatibilité des types des valeurs dans la collection.</span><span class="sxs-lookup"><span data-stu-id="b14e8-106">The non-generic version of <xref:System.Activities.Statements.ParallelForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>

<span data-ttu-id="b14e8-107">Cet exemple montre comment implémenter une activité <xref:System.Activities.Statements.ParallelForEach%601> non générique et son concepteur.</span><span class="sxs-lookup"><span data-stu-id="b14e8-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ParallelForEach%601> activity and its designer.</span></span> <span data-ttu-id="b14e8-108">Cette activité peut être utilisée pour itérer au sein de <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="b14e8-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>

## <a name="parallelforeach-activity"></a><span data-ttu-id="b14e8-109">Activité ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="b14e8-109">ParallelForEach activity</span></span>

<span data-ttu-id="b14e8-110">L' C#instruction/visual Basic `foreach` énumère les éléments d’une collection, en exécutant une instruction incorporée pour chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="b14e8-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="b14e8-111">Les activités [!INCLUDE[wf1](../../../../includes/wf1-md.md)] équivalentes sont <xref:System.Activities.Statements.ForEach%601> et <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="b14e8-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="b14e8-112">L'activité <xref:System.Activities.Statements.ForEach%601> contient une liste de valeurs et un corps.</span><span class="sxs-lookup"><span data-stu-id="b14e8-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="b14e8-113">Au moment de l'exécution, la liste fait l'objet d'une itération et le corps est exécuté pour chaque valeur de la liste.</span><span class="sxs-lookup"><span data-stu-id="b14e8-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>

<span data-ttu-id="b14e8-114"><xref:System.Activities.Statements.ParallelForEach%601> a un <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> afin que l'activité <xref:System.Activities.Statements.ParallelForEach%601> puisse se terminer tôt si l'évaluation du <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> retourne la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="b14e8-114"><xref:System.Activities.Statements.ParallelForEach%601> has a <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>, so that the <xref:System.Activities.Statements.ParallelForEach%601> activity could complete early if the evaluation of the <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> returns `true`.</span></span> <span data-ttu-id="b14e8-115">Le <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> est évalué à l'issue de chaque itération.</span><span class="sxs-lookup"><span data-stu-id="b14e8-115">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> is evaluated after each iteration is completed.</span></span>

<span data-ttu-id="b14e8-116">Dans la plupart des cas, la version générique de l'activité doit être la solution par défaut, car elle couvre la plupart des scénarios dans lesquels elle est utilisée, et fournit la vérification des types au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b14e8-116">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it is used and provides type checking at compile time.</span></span> <span data-ttu-id="b14e8-117">La version non générique peut être utilisée pour itérer au sein de types qui implémentent l'interface <xref:System.Collections.IEnumerable> non générique.</span><span class="sxs-lookup"><span data-stu-id="b14e8-117">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>

## <a name="class-definition"></a><span data-ttu-id="b14e8-118">Définition de classe</span><span class="sxs-lookup"><span data-stu-id="b14e8-118">Class definition</span></span>

<span data-ttu-id="b14e8-119">L'exemple de code suivant illustre la définition d'une activité `ParallelForEach` non générique.</span><span class="sxs-lookup"><span data-stu-id="b14e8-119">The following code example shows the definition of a non-generic `ParallelForEach` activity is.</span></span>

```csharp
[ContentProperty("Body")]
public class ParallelForEach : NativeActivity
{
    [RequiredArgument]
    [DefaultValue(null)]
    InArgument<IEnumerable> Values { get; set; }

    [DefaultValue(null)]
    [DependsOn("Values")]
    public Activity<bool> CompletionCondition
    [DefaultValue(null)]
    [DependsOn("CompletionCondition")]
    ActivityAction<object> Body { get; set; }
}
```

<span data-ttu-id="b14e8-120">Corps (facultatif) </span><span class="sxs-lookup"><span data-stu-id="b14e8-120">Body (optional)</span></span>\
<span data-ttu-id="b14e8-121"><xref:System.Activities.ActivityAction> de type <xref:System.Object>, qui est exécuté pour chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="b14e8-121">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="b14e8-122">Chaque élément individuel est passé dans le corps (Body) via sa propriété Argument.</span><span class="sxs-lookup"><span data-stu-id="b14e8-122">Each individual element is passed into the Body through its Argument property.</span></span>

<span data-ttu-id="b14e8-123">Valeurs (facultatif) </span><span class="sxs-lookup"><span data-stu-id="b14e8-123">Values (optional)</span></span>\
<span data-ttu-id="b14e8-124">Collection des éléments sur lesquels est effectuée l’itération.</span><span class="sxs-lookup"><span data-stu-id="b14e8-124">The collection of elements that are iterated over.</span></span> <span data-ttu-id="b14e8-125">La vérification que tous les éléments de la collection sont de types compatibles est effectuée au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="b14e8-125">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>

<span data-ttu-id="b14e8-126">CompletionCondition (facultatif) </span><span class="sxs-lookup"><span data-stu-id="b14e8-126">CompletionCondition (optional)</span></span>\
<span data-ttu-id="b14e8-127">La propriété <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> est évaluée à l'issue de toute itération.</span><span class="sxs-lookup"><span data-stu-id="b14e8-127">The <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> property is evaluated after any iteration completes.</span></span> <span data-ttu-id="b14e8-128">Si sa valeur est `true`, les itérations en attente planifiées sont annulées.</span><span class="sxs-lookup"><span data-stu-id="b14e8-128">If it evaluates to `true`, then the scheduled pending iterations are canceled.</span></span> <span data-ttu-id="b14e8-129">Si cette propriété n’est pas définie, toutes les activités de la collection Branches s’exécutent jusqu’à la fin.</span><span class="sxs-lookup"><span data-stu-id="b14e8-129">If this property is not set, all activities in the Branches collection execute until completion.</span></span>

## <a name="example-of-using-parallelforeach"></a><span data-ttu-id="b14e8-130">Exemple d’utilisation de ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="b14e8-130">Example of using ParallelForEach</span></span>

<span data-ttu-id="b14e8-131">Le code suivant montre comment utiliser l'activité ParallelForEach dans une application.</span><span class="sxs-lookup"><span data-stu-id="b14e8-131">The following code demonstrates how to use the ParallelForEach activity in an application.</span></span>

```csharp
string[] names = { "bill", "steve", "ray" };

DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };

Activity sampleUsage =
    new ParallelForEach
    {
       Values = new InArgument<IEnumerable>(c=> names),
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,
           Handler = new WriteLine
           {
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))
           }
       }
   };
```

## <a name="parallelforeach-designer"></a><span data-ttu-id="b14e8-132">Concepteur ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="b14e8-132">ParallelForEach designer</span></span>

<span data-ttu-id="b14e8-133">Le concepteur d'activités de l'exemple est semblable, en apparence, au concepteur fourni pour l'activité <xref:System.Activities.Statements.ParallelForEach%601> intégrée.</span><span class="sxs-lookup"><span data-stu-id="b14e8-133">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span> <span data-ttu-id="b14e8-134">Le concepteur s’affiche dans la boîte à outils dans la catégorie **exemples**, **activités non génériques** .</span><span class="sxs-lookup"><span data-stu-id="b14e8-134">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="b14e8-135">Le concepteur est nommé **ParallelForEachWithBodyFactory** dans la boîte à outils, car l’activité expose un <xref:System.Activities.Presentation.IActivityTemplateFactory> dans la boîte à outils qui crée l’activité avec un <xref:System.Activities.ActivityAction>correctement configuré.</span><span class="sxs-lookup"><span data-stu-id="b14e8-135">The designer is named **ParallelForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox that creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>

```csharp
public sealed class ParallelForEachWithBodyFactory : IActivityTemplateFactory
{
    public Activity Create(DependencyObject target)
    {
        return new Microsoft.Samples.Activities.Statements.ParallelForEach()
        {
            Body = new ActivityAction<object>()
            {
                Argument = new DelegateInArgument<object>()
                {
                    Name = "item"
                }
            }
        };
    }
}
```

## <a name="to-run-the-sample"></a><span data-ttu-id="b14e8-136">Pour exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="b14e8-136">To run the sample</span></span>

1. <span data-ttu-id="b14e8-137">Définissez le projet de votre choix comme projet de démarrage de la solution.</span><span class="sxs-lookup"><span data-stu-id="b14e8-137">Set the project of your choice as the startup project of the solution.</span></span>

    1. <span data-ttu-id="b14e8-138">**CodeTestClient** montre comment utiliser l’activité à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="b14e8-138">**CodeTestClient** shows how to use the activity using code.</span></span>

    2. <span data-ttu-id="b14e8-139">**DesignerTestClient** montre comment utiliser l’activité dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="b14e8-139">**DesignerTestClient** shows how to use the activity within the designer.</span></span>

2. <span data-ttu-id="b14e8-140">Générez et exécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="b14e8-140">Build and run the project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b14e8-141">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b14e8-141">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b14e8-142">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b14e8-142">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b14e8-143">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b14e8-143">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b14e8-144">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="b14e8-144">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericParallelForEach`
