---
title: ForEach non générique
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 9678d929375857a76d01f575e637a069b0911ae5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283573"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="b1e1e-102">ForEach non générique</span><span class="sxs-lookup"><span data-stu-id="b1e1e-102">Non-Generic ForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="b1e1e-103">fournit, dans sa boîte à outils, un ensemble d'activités de flux de contrôle, notamment <xref:System.Activities.Statements.ForEach%601>, qui permet l'itération au sein des collections <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="b1e1e-104"><xref:System.Activities.Statements.ForEach%601> requiert que sa propriété <xref:System.Activities.Statements.ForEach%601.Values%2A> soit de type <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b1e1e-105">Cela empêche les utilisateurs d'itérer au sein des structures de données qui implémentent l'interface <xref:System.Collections.Generic.IEnumerable%601> (par exemple, <xref:System.Collections.ArrayList>).</span><span class="sxs-lookup"><span data-stu-id="b1e1e-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="b1e1e-106">La version non générique de <xref:System.Activities.Statements.ForEach%601> passe outre cette exigence, aux dépens d’un runtime plus complexe afin de garantir la compatibilité des types des valeurs dans la collection.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="b1e1e-107">Cet exemple montre comment implémenter une activité <xref:System.Activities.Statements.ForEach%601> non générique et son concepteur.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="b1e1e-108">Cette activité peut être utilisée pour itérer au sein de <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="b1e1e-109">Activité ForEach</span><span class="sxs-lookup"><span data-stu-id="b1e1e-109">ForEach Activity</span></span>  

 <span data-ttu-id="b1e1e-110">L’instruction C#/Visual Basic `foreach` énumère les éléments d’une collection, en exécutant une instruction incorporée pour chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="b1e1e-111">Les activités [!INCLUDE[wf1](../../../../includes/wf1-md.md)] équivalentes de `foreach` sont <xref:System.Activities.Statements.ForEach%601> et <xref:System.Activities.Statements.ParallelForEach%601>.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="b1e1e-112">L'activité <xref:System.Activities.Statements.ForEach%601> contient une liste de valeurs et un corps.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="b1e1e-113">Au moment de l'exécution, la liste fait l'objet d'une itération et le corps est exécuté pour chaque valeur de la liste.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="b1e1e-114">Dans la plupart des cas, la version générique de l'activité doit être la solution par défaut, car elle couvre la plupart des scénarios dans lesquels elle est utilisée, et fournit la vérification des types au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="b1e1e-115">La version non générique peut être utilisée pour itérer au sein de types qui implémentent l'interface <xref:System.Collections.IEnumerable> non générique.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="b1e1e-116">Définition de classes</span><span class="sxs-lookup"><span data-stu-id="b1e1e-116">Class Definition</span></span>  

 <span data-ttu-id="b1e1e-117">L'exemple de code suivant illustre la définition d'une activité `ForEach` non générique.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }
}  
```  
  
 <span data-ttu-id="b1e1e-118">Body (facultatif)</span><span class="sxs-lookup"><span data-stu-id="b1e1e-118">Body (optional)</span></span>  
 <span data-ttu-id="b1e1e-119"><xref:System.Activities.ActivityAction> de type <xref:System.Object>, qui est exécuté pour chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="b1e1e-120">Chaque élément individuel est passé dans le corps (Body) via sa propriété `Argument`.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="b1e1e-121">Values (facultatif)</span><span class="sxs-lookup"><span data-stu-id="b1e1e-121">Values (optional)</span></span>  
 <span data-ttu-id="b1e1e-122">Collection des éléments sur lesquels est effectuée l’itération.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="b1e1e-123">La vérification que tous les éléments de la collection sont de types compatibles est effectuée au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="b1e1e-124">Exemple d'utilisation de ForEach</span><span class="sxs-lookup"><span data-stu-id="b1e1e-124">Example of Using ForEach</span></span>  

 <span data-ttu-id="b1e1e-125">Le code suivant montre comment utiliser l'activité ForEach dans une application.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
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
  
|<span data-ttu-id="b1e1e-126">Condition</span><span class="sxs-lookup"><span data-stu-id="b1e1e-126">Condition</span></span>|<span data-ttu-id="b1e1e-127">Message</span><span class="sxs-lookup"><span data-stu-id="b1e1e-127">Message</span></span>|<span data-ttu-id="b1e1e-128">severity</span><span class="sxs-lookup"><span data-stu-id="b1e1e-128">Severity</span></span>|<span data-ttu-id="b1e1e-129">Type d’exception</span><span class="sxs-lookup"><span data-stu-id="b1e1e-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="b1e1e-130">La valeur est `null`</span><span class="sxs-lookup"><span data-stu-id="b1e1e-130">Values is `null`</span></span>|<span data-ttu-id="b1e1e-131">La valeur d’un argument d’activité ’Values’ requis n’a pas été fournie.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="b1e1e-132">Error</span><span class="sxs-lookup"><span data-stu-id="b1e1e-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="b1e1e-133">Concepteur ForEach</span><span class="sxs-lookup"><span data-stu-id="b1e1e-133">ForEach Designer</span></span>  

 <span data-ttu-id="b1e1e-134">Le concepteur d'activités de l'exemple est semblable, en apparence, au concepteur fourni pour l'activité <xref:System.Activities.Statements.ForEach%601> intégrée.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="b1e1e-135">Le concepteur s’affiche dans la boîte à outils dans la catégorie **exemples**, **activités non génériques** .</span><span class="sxs-lookup"><span data-stu-id="b1e1e-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="b1e1e-136">Le concepteur est nommé **ForEachWithBodyFactory** dans la boîte à outils, car l’activité expose un <xref:System.Activities.Presentation.IActivityTemplateFactory> dans la boîte à outils, ce qui crée l’activité avec un correctement configuré <xref:System.Activities.ActivityAction> .</span><span class="sxs-lookup"><span data-stu-id="b1e1e-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
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
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="b1e1e-137">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="b1e1e-137">To run this sample</span></span>  
  
1. <span data-ttu-id="b1e1e-138">Définissez le projet de votre choix comme projet de démarrage de la solution :</span><span class="sxs-lookup"><span data-stu-id="b1e1e-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="b1e1e-139">**CodeTestClient** montre comment utiliser l’activité à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="b1e1e-140">**DesignerTestClient** montre comment utiliser l’activité dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="b1e1e-141">Générez et exécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b1e1e-142">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b1e1e-143">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b1e1e-144">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b1e1e-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b1e1e-145">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="b1e1e-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
