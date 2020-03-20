---
title: Appel de la validation d'activité
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 1241e6445cde20a192581e8132e563e0f7ca8d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182884"
---
# <a name="invoking-activity-validation"></a><span data-ttu-id="07d53-102">Appel de la validation d'activité</span><span class="sxs-lookup"><span data-stu-id="07d53-102">Invoking Activity Validation</span></span>
<span data-ttu-id="07d53-103">La validation d’activité offre une méthode d’identification et de signalisation des erreurs dans la configuration de toute activité, avant son exécution.</span><span class="sxs-lookup"><span data-stu-id="07d53-103">Activity validation provides a method to identify and report errors in any activity’s configuration prior to its execution.</span></span> <span data-ttu-id="07d53-104">La validation a lieu lorsque, dans le Concepteur de Workflow, un workflow est modifié et que l'ensemble des erreurs ou avertissements de validation sont affichés.</span><span class="sxs-lookup"><span data-stu-id="07d53-104">Validation occurs when a workflow is modified in the workflow designer and any validation errors or warnings are displayed in the workflow designer.</span></span> <span data-ttu-id="07d53-105">La validation se produit également au moment de l’exécution lorsqu’un workflow est appelé et si des erreurs de validation se produisent, <xref:System.Activities.InvalidWorkflowException> est levée par la logique de validation par défaut.</span><span class="sxs-lookup"><span data-stu-id="07d53-105">Validation also occurs at run time when a workflow is invoked and if any validation errors occur, an <xref:System.Activities.InvalidWorkflowException> is thrown by the default validation logic.</span></span> <span data-ttu-id="07d53-106">Windows Workflow Foundation (WF) fournit la classe qui peut être utilisée par les <xref:System.Activities.Validation.ActivityValidationServices> développeurs d’applications de flux de travail et d’outillage pour valider explicitement une activité.</span><span class="sxs-lookup"><span data-stu-id="07d53-106">Windows Workflow Foundation (WF) provides the <xref:System.Activities.Validation.ActivityValidationServices> class that can be used by workflow application and tooling developers to explicitly validate an activity.</span></span> <span data-ttu-id="07d53-107">Cette rubrique décrit comment utiliser la classe <xref:System.Activities.Validation.ActivityValidationServices> pour valider une activité.</span><span class="sxs-lookup"><span data-stu-id="07d53-107">This topic describes how to use <xref:System.Activities.Validation.ActivityValidationServices> to perform activity validation.</span></span>  
  
## <a name="using-activityvalidationservices"></a><span data-ttu-id="07d53-108">Utilisation de la classe ActivityValidationServices</span><span class="sxs-lookup"><span data-stu-id="07d53-108">Using ActivityValidationServices</span></span>  
 <span data-ttu-id="07d53-109">La classe <xref:System.Activities.Validation.ActivityValidationServices> compte deux surcharges <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, utilisées pour appeler la logique de validation d'une activité.</span><span class="sxs-lookup"><span data-stu-id="07d53-109"><xref:System.Activities.Validation.ActivityValidationServices> has two <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> overloads that are used to invoke an activity’s validation logic.</span></span> <span data-ttu-id="07d53-110">La première surcharge prend l’activité racine à valider et retourne une collection d’erreurs et avertissements de validation.</span><span class="sxs-lookup"><span data-stu-id="07d53-110">The first overload takes the root activity to be validated and returns a collection of validation errors and warnings.</span></span> <span data-ttu-id="07d53-111">Dans l’exemple suivant, une activité `Add` personnalisée qui compte deux arguments requis est utilisée.</span><span class="sxs-lookup"><span data-stu-id="07d53-111">In the following example, a custom `Add` activity is used that has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="07d53-112">L'activité `Add` est utilisée dans un objet <xref:System.Activities.Statements.Sequence>, mais ses deux arguments requis ne sont pas liés, comme indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="07d53-112">The `Add` activity is used inside a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound, as shown in the following example.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int>{ Default = 10 };  
Variable<int> Operand2 = new Variable<int>{ Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="07d53-113">Ce flux de travail peut être validé en appelant <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d53-113">This workflow can be validated by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="07d53-114">La méthode <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> retourne une collection de l'ensemble des erreurs ou avertissements de validation contenus dans l'activité et tout enfant, comme indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="07d53-114"><xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> returns a collection of any validation errors or warnings contained by the activity and any children, as shown in the following example.</span></span>  
  
```csharp  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="07d53-115">Lorsque la méthode <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> est appelée sur cet exemple de flux de travail, deux erreurs de validation sont retournées.</span><span class="sxs-lookup"><span data-stu-id="07d53-115">When <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> is called on this sample workflow, two validation errors are returned.</span></span>  
  
 <span data-ttu-id="07d53-116">**Erreur : La valeur pour un argument d'activité 'Operand2' requis n'a pas été fournie.**</span><span class="sxs-lookup"><span data-stu-id="07d53-116">**Error: Value for a required activity argument 'Operand2' was not supplied.**</span></span>  
<span data-ttu-id="07d53-117">**Erreur : La valeur pour un argument d'activité 'Operand1' requis n'a pas été fournie.**</span><span class="sxs-lookup"><span data-stu-id="07d53-117">**Error: Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="07d53-118">Si ce workflow était appelé, un <xref:System.Activities.InvalidWorkflowException> serait levé, comme indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="07d53-118">If this workflow was invoked, an <xref:System.Activities.InvalidWorkflowException> would be thrown, as shown in the following example.</span></span>  
  
```csharp  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="07d53-119">**System.Activities.InvalidWorkflowException :**</span><span class="sxs-lookup"><span data-stu-id="07d53-119">**System.Activities.InvalidWorkflowException:**</span></span>  
<span data-ttu-id="07d53-120">**Les erreurs suivantes ont été rencontrées lors du traitement de l’arbre de flux de travail:**
 **«Ajouter»: La valeur pour un argument d’activité requis «Operand2» n’a pas été fournie.** 
 **'Ajouter': La valeur pour un argument d’activité requis 'Operand1' n’a pas été fournie.**</span><span class="sxs-lookup"><span data-stu-id="07d53-120">**The following errors were encountered while processing the workflow tree:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="07d53-121">Pour que cet exemple de workflow soit valide, les deux arguments requis de l’activité `Add` doivent être liés.</span><span class="sxs-lookup"><span data-stu-id="07d53-121">For this example workflow to be valid, the two required arguments of the `Add` activity must be bound.</span></span> <span data-ttu-id="07d53-122">Dans l’exemple suivant, les deux arguments requis sont liés aux variables de flux de travail, tout comme la valeur de résultat.</span><span class="sxs-lookup"><span data-stu-id="07d53-122">In the following example, the two required arguments are bound to workflow variables along with the result value.</span></span> <span data-ttu-id="07d53-123">Dans cet exemple, l'argument <xref:System.Activities.Activity%601.Result%2A> est lié, ainsi que les deux arguments requis.</span><span class="sxs-lookup"><span data-stu-id="07d53-123">In this example the <xref:System.Activities.Activity%601.Result%2A> argument is bound along with the two required arguments.</span></span> <span data-ttu-id="07d53-124">L'argument <xref:System.Activities.Activity%601.Result%2A> ne doit pas forcément être lié et ne provoque pas d'erreur de validation s'il ne l'est pas.</span><span class="sxs-lookup"><span data-stu-id="07d53-124">The <xref:System.Activities.Activity%601.Result%2A> argument is not required to be bound and does not cause a validation error if it is not.</span></span> <span data-ttu-id="07d53-125">Il incombe à l'auteur du workflow de lier l'objet <xref:System.Activities.Activity%601.Result%2A>, si sa valeur est utilisée ailleurs dans le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="07d53-125">It is the responsibility of the workflow author to bind <xref:System.Activities.Activity%601.Result%2A> if its value is used elsewhere in the workflow.</span></span>  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a><span data-ttu-id="07d53-126">Validation des arguments requis à l’activité racine</span><span class="sxs-lookup"><span data-stu-id="07d53-126">Validating Required Arguments on the Root Activity</span></span>  
 <span data-ttu-id="07d53-127">Si l'activité racine d'un workflow possède des arguments, ils ne sont pas liés jusqu'à ce que le workflow soit appelé et les paramètres passés au workflow.</span><span class="sxs-lookup"><span data-stu-id="07d53-127">If the root activity of a workflow has arguments, these are not bound until the workflow is invoked and parameters are passed to the workflow.</span></span> <span data-ttu-id="07d53-128">Le workflow suivant passe la validation, mais une exception est levée si le workflow est appelé sans passer les arguments requis, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="07d53-128">The following workflow passes validation, but an exception is thrown if the workflow is invoked without passing in the required arguments, as shown in the following example.</span></span>  
  
```csharp  
Activity wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, but when the workflow  
// is invoked, an InvalidWorkflowException is thrown.  
try  
{  
    WorkflowInvoker.Invoke(wf);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
 <span data-ttu-id="07d53-129">**System.ArgumentException : les paramètres de l'argument de l'activité racine sont incorrects.**</span><span class="sxs-lookup"><span data-stu-id="07d53-129">**System.ArgumentException: The root activity's argument settings are incorrect.**</span></span>  
<span data-ttu-id="07d53-130">**Fixez la définition du flux de travail ou fournissez des valeurs d’entrée pour corriger ces erreurs :**
 **« Ajouter » : La valeur d’un argument d’activité requis « Operand2 » n’a pas été fournie.** 
 **'Ajouter': La valeur pour un argument d’activité requis 'Operand1' n’a pas été fournie.**</span><span class="sxs-lookup"><span data-stu-id="07d53-130">**Either fix the workflow definition or supply input values to fix these errors:**
 **'Add': Value for a required activity argument 'Operand2' was not supplied.**
 **'Add': Value for a required activity argument 'Operand1' was not supplied.**</span></span>  <span data-ttu-id="07d53-131">Une fois les arguments appropriés passés, le flux de travail se termine correctement, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="07d53-131">After the correct arguments are passed, the workflow completes successfully, as shown in the following example.</span></span>  
  
```csharp  
Add wf = new Add();  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
// results has no errors or warnings, and the workflow completes  
// successfully because the required arguments were passed.  
try  
{  
    Dictionary<string, object> wfparams = new Dictionary<string, object>  
    {  
        { "Operand1", 10 },  
        { "Operand2", 15 }  
    };  
  
    int result = WorkflowInvoker.Invoke(wf, wfparams);  
    Console.WriteLine("Result: {0}", result);  
}  
catch (Exception ex)  
{  
    Console.WriteLine(ex);  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="07d53-132">Dans cet exemple, l'activité racine a été déclarée comme activité `Add` plutôt qu'`Activity` comme dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="07d53-132">In this example, the root activity was declared as `Add` instead of `Activity` as in the previous example.</span></span> <span data-ttu-id="07d53-133">La méthode `WorkflowInvoker.Invoke` peut ainsi retourner un entier unique qui représente les résultats de l’activité `Add`, au lieu d’un dictionnaire d’arguments `out`.</span><span class="sxs-lookup"><span data-stu-id="07d53-133">This allows the `WorkflowInvoker.Invoke` method to return a single integer that represents the results of the `Add` activity instead of a dictionary of `out` arguments.</span></span> <span data-ttu-id="07d53-134">La variable `wf` aurait également pu être déclarée comme `Activity<int>`.</span><span class="sxs-lookup"><span data-stu-id="07d53-134">The variable `wf` could also have been declared as `Activity<int>`.</span></span>  
  
 <span data-ttu-id="07d53-135">Lors de la validation d’arguments racines, il incombe à l’application hôte de vérifier que tous les arguments requis sont passés pendant l’appel du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="07d53-135">When validating root arguments, it is the responsibility of the host application to ensure that all required arguments are passed when the workflow is invoked.</span></span>  
  
### <a name="invoking-imperative-code-based-validation"></a><span data-ttu-id="07d53-136">Appel de validation basée sur le code impératif</span><span class="sxs-lookup"><span data-stu-id="07d53-136">Invoking Imperative Code-Based Validation</span></span>

<span data-ttu-id="07d53-137">La validation basée sur le code impératif offre un moyen simple de valider une activité ainsi que les activités dérivées de <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> et <xref:System.Activities.NativeActivity>.</span><span class="sxs-lookup"><span data-stu-id="07d53-137">Imperative code-based validation provides a simple way for an activity to provide validation about itself, and is available for activities that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, and <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="07d53-138">Le code de validation est ajouté à l’activité qui détermine les erreurs ou avertissements de validation ajoutés à l’activité.</span><span class="sxs-lookup"><span data-stu-id="07d53-138">Validation code that determines any validation errors or warnings is added to the activity.</span></span> <span data-ttu-id="07d53-139">Lorsque la validation est appelée sur l’activité, ces avertissements ou erreurs sont contenus dans la collection retournée par l’appel à <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d53-139">When validation is invoked on the activity, these warnings or errors are contained in the collection returned by the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="07d53-140">Dans l'exemple suivant, une activité `CreateProduct` est définie.</span><span class="sxs-lookup"><span data-stu-id="07d53-140">In the following example, a `CreateProduct` activity is defined.</span></span> <span data-ttu-id="07d53-141">Si la valeur `Cost` est supérieure à la valeur `Price`, une erreur de validation est ajoutée aux métadonnées dans la substitution <xref:System.Activities.CodeActivity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d53-141">If the `Cost` is greater than the `Price`, a validation error is added to the metadata in the <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span>  
  
```csharp  
public sealed class CreateProduct : CodeActivity  
{  
    public double Price { get; set; }  
    public double Cost { get; set; }  
  
    // [RequiredArgument] attribute will generate a validation error
    // if the Description argument is not set.  
    [RequiredArgument]  
    public InArgument<string> Description { get; set; }  
  
    protected override void CacheMetadata(CodeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        // Determine when the activity has been configured in an invalid way.  
        if (this.Cost > this.Price)  
        {  
            // Add a validation error with a custom message.  
            metadata.AddValidationError("The Cost must be less than or equal to the Price.");  
        }  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // Not needed for the sample.  
    }  
}  
```  
  
 <span data-ttu-id="07d53-142">Dans cet exemple, un workflow est configuré à l'aide de l'activité `CreateProduct`.</span><span class="sxs-lookup"><span data-stu-id="07d53-142">In this example, a workflow is configured using the `CreateProduct` activity.</span></span> <span data-ttu-id="07d53-143">Dans ce workflow, la valeur `Cost` est supérieure à la valeur `Price`, et l’argument `Description` requis n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="07d53-143">In this workflow, the `Cost` is greater than the `Price`, and the required `Description` argument is not set.</span></span> <span data-ttu-id="07d53-144">Lorsque la validation est appelée, les erreurs suivantes sont retournées.</span><span class="sxs-lookup"><span data-stu-id="07d53-144">When validation is invoked, the following errors are returned.</span></span>  
  
```csharp  
Activity wf = new Sequence  
{  
    Activities =
    {  
        new CreateProduct  
        {  
            Cost = 75.00,  
            Price = 55.00  
            // Cost > Price and required Description argument not set.  
        },  
        new WriteLine  
        {  
            Text = "Product added."  
        }  
    }  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="07d53-145">**Erreur : le coût doit être inférieur ou égal au prix.**</span><span class="sxs-lookup"><span data-stu-id="07d53-145">**Error: The Cost must be less than or equal to the Price.**</span></span>  
<span data-ttu-id="07d53-146">**Erreur : la valeur pour un argument d'activité 'Description' requis n'a pas été fournie.**</span><span class="sxs-lookup"><span data-stu-id="07d53-146">**Error: Value for a required activity argument 'Description' was not supplied.**</span></span>
> [!NOTE]
> <span data-ttu-id="07d53-147">Les auteurs d’activités personnalisées peuvent fournir la logique de validation dans la substitution de la méthode <xref:System.Activities.CodeActivity.CacheMetadata%2A> d’une activité.</span><span class="sxs-lookup"><span data-stu-id="07d53-147">Custom activity authors can provide validation logic in an activity's <xref:System.Activities.CodeActivity.CacheMetadata%2A> override.</span></span> <span data-ttu-id="07d53-148">Toutes les exceptions levées à partir de <xref:System.Activities.CodeActivity.CacheMetadata%2A> ne sont pas traitées comme des erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="07d53-148">Any exceptions that are thrown from <xref:System.Activities.CodeActivity.CacheMetadata%2A> are not treated as validation errors.</span></span> <span data-ttu-id="07d53-149">Ces exceptions ne seront pas détectées par l'appel à <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> et doivent être gérées par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="07d53-149">These exceptions will escape from the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> and must be handled by the caller.</span></span>  
  
## <a name="using-validationsettings"></a><span data-ttu-id="07d53-150">Utilisation de ValidationSettings</span><span class="sxs-lookup"><span data-stu-id="07d53-150">Using ValidationSettings</span></span>  
 <span data-ttu-id="07d53-151">Par défaut, toutes les activités dans l'arborescence d'activité sont évaluées lorsque la validation est appelée par <xref:System.Activities.Validation.ActivityValidationServices>.</span><span class="sxs-lookup"><span data-stu-id="07d53-151">By default, all activities in the activity tree are evaluated when validation is invoked by <xref:System.Activities.Validation.ActivityValidationServices>.</span></span> <span data-ttu-id="07d53-152"><xref:System.Activities.Validation.ValidationSettings> vous permet de personnaliser la validation de plusieurs façons différentes en configurant ses trois propriétés.</span><span class="sxs-lookup"><span data-stu-id="07d53-152"><xref:System.Activities.Validation.ValidationSettings> allows the validation to be customized in several different ways by configuring its three properties.</span></span> <span data-ttu-id="07d53-153"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> spécifie si le validateur doit parcourir l'arborescence d'activité entière ou uniquement appliquer la logique de validation à l'activité fournie.</span><span class="sxs-lookup"><span data-stu-id="07d53-153"><xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> specifies whether the validator should walk the entire activity tree or only apply validation logic to the supplied activity.</span></span> <span data-ttu-id="07d53-154">La valeur par défaut pour ce paramètre est `false`.</span><span class="sxs-lookup"><span data-stu-id="07d53-154">The default for this value is `false`.</span></span> <span data-ttu-id="07d53-155"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> spécifie un mappage de contraintes supplémentaires, d'un type vers une liste de contraintes.</span><span class="sxs-lookup"><span data-stu-id="07d53-155"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> specifies additional constraint mapping from a type to a list of constraints.</span></span> <span data-ttu-id="07d53-156">Pour le type de base de chaque activité de l'arborescence en cours de validation, il existe une recherche dans la propriété <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d53-156">For the base type of each activity in the activity tree being validated there is a lookup into <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="07d53-157">Si une liste de contraintes correspondante est trouvée, toutes les contraintes de la liste sont évaluées pour l'activité.</span><span class="sxs-lookup"><span data-stu-id="07d53-157">If a matching constraint list is found, all constraints in the list are evaluated for the activity.</span></span> <span data-ttu-id="07d53-158"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> spécifie si le validateur doit évaluer toutes les contraintes ou seulement celles spécifiées dans la propriété <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d53-158"><xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> specifies whether the validator should evaluate all constraints or only those specified in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>.</span></span> <span data-ttu-id="07d53-159">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="07d53-159">The default value is `false`.</span></span> <span data-ttu-id="07d53-160">Grâce aux propriétés <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> et <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>, les auteurs hôtes de flux de travail peuvent ajouter une validation supplémentaire pour les flux de travail comme les contraintes de stratégie pour les outils tels que FxCop.</span><span class="sxs-lookup"><span data-stu-id="07d53-160"><xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> and <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> are useful for workflow host authors to add additional validation for workflows, such as policy constraints for tools such as FxCop.</span></span> <span data-ttu-id="07d53-161">Pour plus d’informations sur les contraintes, voir [Contraintes déclaratives](declarative-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="07d53-161">For more information about constraints, see [Declarative Constraints](declarative-constraints.md).</span></span>  
  
 <span data-ttu-id="07d53-162">Pour utiliser l'objet <xref:System.Activities.Validation.ValidationSettings>, configurez les propriétés de votre choix, puis passez-le dans l'appel à la méthode <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="07d53-162">To use <xref:System.Activities.Validation.ValidationSettings>, configure the desired properties, and then pass it in the call to <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="07d53-163">Dans cet exemple, un flux de travail, qui consiste en un objet <xref:System.Activities.Statements.Sequence> avec une activité `Add` personnalisée, est validé.</span><span class="sxs-lookup"><span data-stu-id="07d53-163">In this example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> with a custom `Add` activity is validated.</span></span> <span data-ttu-id="07d53-164">L’activité `Add` compte deux arguments requis.</span><span class="sxs-lookup"><span data-stu-id="07d53-164">The `Add` activity has two required arguments.</span></span>  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 <span data-ttu-id="07d53-165">L’activité `Add` suivante est utilisée dans un objet <xref:System.Activities.Statements.Sequence>, mais ses deux arguments requis ne sont pas liés.</span><span class="sxs-lookup"><span data-stu-id="07d53-165">The following `Add` activity is used in a <xref:System.Activities.Statements.Sequence>, but its two required arguments are not bound.</span></span>  
  
```csharp  
Variable<int> Operand1 = new Variable<int> { Default = 10 };  
Variable<int> Operand2 = new Variable<int> { Default = 15 };  
Variable<int> Result = new Variable<int>();  
  
Activity wf = new Sequence  
{  
    Variables = { Operand1, Operand2, Result },  
    Activities =
    {  
        new Add(),  
        new WriteLine  
        {  
            Text = new InArgument<string>(env => "The result is " + Result.Get(env))  
        }  
    }  
};  
```  
  
 <span data-ttu-id="07d53-166">Pour l’exemple suivant, la validation est effectuée avec la propriété <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> définie sur `true`. Aussi seule l’activité <xref:System.Activities.Statements.Sequence> racine est-elle validée.</span><span class="sxs-lookup"><span data-stu-id="07d53-166">For the following example, validation is performed with <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> set to `true`, so only the root <xref:System.Activities.Statements.Sequence> activity is validated.</span></span>  
  
```csharp  
ValidationSettings settings = new ValidationSettings  
{  
    SingleLevel = true  
};  
  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error: {0}", error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning: {0}", warning.Message);  
    }  
}  
```  
  
 <span data-ttu-id="07d53-167">Ce code affiche la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="07d53-167">This code displays the following output:</span></span>  
  
 <span data-ttu-id="07d53-168">**Pas d’avertissements ou d’erreurs** Même si `Add` l’activité a exigé des arguments qui ne sont pas liés, la validation est réussie parce que seule l’activité racine est évaluée.</span><span class="sxs-lookup"><span data-stu-id="07d53-168">**No warnings or errors** Even though the `Add` activity has required arguments that are not bound, validation is successful because only the root activity is evaluated.</span></span> <span data-ttu-id="07d53-169">Ce type de validation est utile pour valider uniquement des éléments particuliers d’une arborescence d’activité, par exemple pour valider, dans un concepteur, une modification de propriété d’une activité unique.</span><span class="sxs-lookup"><span data-stu-id="07d53-169">This type of validation is useful for validating only specific elements in an activity tree, such as validation of a property change of a single activity in a designer.</span></span> <span data-ttu-id="07d53-170">Notez que si ce workflow est appelé, la validation complète configurée dans le workflow est évaluée et <xref:System.Activities.InvalidWorkflowException> est levée.</span><span class="sxs-lookup"><span data-stu-id="07d53-170">Note that if this workflow is invoked, the full validation configured in the workflow is evaluated and an <xref:System.Activities.InvalidWorkflowException> would be thrown.</span></span> <span data-ttu-id="07d53-171"><xref:System.Activities.Validation.ActivityValidationServices> et <xref:System.Activities.Validation.ValidationSettings> configurent uniquement la validation explicitement appelée par l'hôte, et non la validation qui a lieu lors de l'appel d'un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="07d53-171"><xref:System.Activities.Validation.ActivityValidationServices> and <xref:System.Activities.Validation.ValidationSettings> configure only validation explicitly invoked by the host, and not the validation that occurs when a workflow is invoked.</span></span>
