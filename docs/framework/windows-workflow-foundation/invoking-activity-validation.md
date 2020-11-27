---
title: Appel de la validation d'activité
ms.date: 03/30/2017
ms.assetid: 22bef766-c505-4fd4-ac0f-7b363b238969
ms.openlocfilehash: 95e6b22fe9814133df080b1faadcc4be32b60bf9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279803"
---
# <a name="invoking-activity-validation"></a>Appel de la validation d'activité

La validation d’activité offre une méthode d’identification et de signalisation des erreurs dans la configuration de toute activité, avant son exécution. La validation a lieu lorsque, dans le Concepteur de Workflow, un workflow est modifié et que l'ensemble des erreurs ou avertissements de validation sont affichés. La validation se produit également au moment de l’exécution lorsqu’un workflow est appelé et si des erreurs de validation se produisent, <xref:System.Activities.InvalidWorkflowException> est levée par la logique de validation par défaut. Windows Workflow Foundation (WF) fournit la <xref:System.Activities.Validation.ActivityValidationServices> classe qui peut être utilisée par l’application de workflow et les développeurs d’outils pour valider explicitement une activité. Cette rubrique décrit comment utiliser la classe <xref:System.Activities.Validation.ActivityValidationServices> pour valider une activité.  
  
## <a name="using-activityvalidationservices"></a>Utilisation de la classe ActivityValidationServices  

 La classe <xref:System.Activities.Validation.ActivityValidationServices> compte deux surcharges <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>, utilisées pour appeler la logique de validation d'une activité. La première surcharge prend l’activité racine à valider et retourne une collection d’erreurs et avertissements de validation. Dans l’exemple suivant, une activité `Add` personnalisée qui compte deux arguments requis est utilisée.  
  
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
  
 L'activité `Add` est utilisée dans un objet <xref:System.Activities.Statements.Sequence>, mais ses deux arguments requis ne sont pas liés, comme indiqué dans l'exemple suivant :  
  
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
  
 Ce flux de travail peut être validé en appelant <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. La méthode <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> retourne une collection de l'ensemble des erreurs ou avertissements de validation contenus dans l'activité et tout enfant, comme indiqué dans l'exemple suivant :  
  
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
  
 Lorsque la méthode <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> est appelée sur cet exemple de flux de travail, deux erreurs de validation sont retournées.  
  
 **Erreur : La valeur pour un argument d'activité 'Operand2' requis n'a pas été fournie.**  
**Erreur : La valeur pour un argument d'activité 'Operand1' requis n'a pas été fournie.**  Si ce workflow était appelé, un <xref:System.Activities.InvalidWorkflowException> serait levé, comme indiqué dans l'exemple suivant :  
  
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
  
 **System.Activities.InvalidWorkflowException :**  
**Les erreurs suivantes se sont produites lors du traitement de l’arborescence du flux de travail :** 
 **'Add' : la valeur d’un argument d’activité’Operand2 'requis n’a pas été fournie.** 
 **'Add' : la valeur d’un argument d’activité’Operand1 'requis n’a pas été fournie.**  Pour que cet exemple de workflow soit valide, les deux arguments requis de l’activité `Add` doivent être liés. Dans l’exemple suivant, les deux arguments requis sont liés aux variables de flux de travail, tout comme la valeur de résultat. Dans cet exemple, l'argument <xref:System.Activities.Activity%601.Result%2A> est lié, ainsi que les deux arguments requis. L'argument <xref:System.Activities.Activity%601.Result%2A> ne doit pas forcément être lié et ne provoque pas d'erreur de validation s'il ne l'est pas. Il incombe à l'auteur du workflow de lier l'objet <xref:System.Activities.Activity%601.Result%2A>, si sa valeur est utilisée ailleurs dans le flux de travail.  
  
```csharp  
new Add  
{  
    Operand1 = Operand1,  
    Operand2 = Operand2,  
    Result = Result  
}  
```  
  
### <a name="validating-required-arguments-on-the-root-activity"></a>Validation des arguments requis à l’activité racine  

 Si l'activité racine d'un workflow possède des arguments, ils ne sont pas liés jusqu'à ce que le workflow soit appelé et les paramètres passés au workflow. Le workflow suivant passe la validation, mais une exception est levée si le workflow est appelé sans passer les arguments requis, comme indiqué dans l’exemple suivant.  
  
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
  
 **System.ArgumentException : les paramètres de l'argument de l'activité racine sont incorrects.**  
**Corrigez la définition du flux de travail ou fournissez des valeurs d’entrée pour corriger ces erreurs :** 
 **'Add' : la valeur d’un argument d’activité’Operand2 'requis n’a pas été fournie.** 
 **'Add' : la valeur d’un argument d’activité’Operand1 'requis n’a pas été fournie.**  Une fois les arguments appropriés passés, le flux de travail se termine correctement, comme indiqué dans l’exemple suivant :  
  
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
> Dans cet exemple, l'activité racine a été déclarée comme activité `Add` plutôt qu'`Activity` comme dans l'exemple précédent. La méthode `WorkflowInvoker.Invoke` peut ainsi retourner un entier unique qui représente les résultats de l’activité `Add`, au lieu d’un dictionnaire d’arguments `out`. La variable `wf` aurait également pu être déclarée comme `Activity<int>`.  
  
 Lors de la validation d’arguments racines, il incombe à l’application hôte de vérifier que tous les arguments requis sont passés pendant l’appel du flux de travail.  
  
### <a name="invoking-imperative-code-based-validation"></a>Appel de validation basée sur le code impératif

La validation basée sur le code impératif offre un moyen simple de valider une activité ainsi que les activités dérivées de <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity> et <xref:System.Activities.NativeActivity>. Le code de validation est ajouté à l’activité qui détermine les erreurs ou avertissements de validation ajoutés à l’activité. Lorsque la validation est appelée sur l’activité, ces avertissements ou erreurs sont contenus dans la collection retournée par l’appel à <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Dans l'exemple suivant, une activité `CreateProduct` est définie. Si la valeur `Cost` est supérieure à la valeur `Price`, une erreur de validation est ajoutée aux métadonnées dans la substitution <xref:System.Activities.CodeActivity.CacheMetadata%2A>.  
  
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
  
 Dans cet exemple, un workflow est configuré à l'aide de l'activité `CreateProduct`. Dans ce workflow, la valeur `Cost` est supérieure à la valeur `Price`, et l’argument `Description` requis n’est pas défini. Lorsque la validation est appelée, les erreurs suivantes sont retournées.  
  
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
  
 **Erreur : le coût doit être inférieur ou égal au prix.**  
**Erreur : la valeur pour un argument d'activité 'Description' requis n'a pas été fournie.**
> [!NOTE]
> Les auteurs d’activités personnalisées peuvent fournir la logique de validation dans la substitution de la méthode <xref:System.Activities.CodeActivity.CacheMetadata%2A> d’une activité. Toutes les exceptions levées à partir de <xref:System.Activities.CodeActivity.CacheMetadata%2A> ne sont pas traitées comme des erreurs de validation. Ces exceptions ne seront pas détectées par l'appel à <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A> et doivent être gérées par l'appelant.  
  
## <a name="using-validationsettings"></a>Utilisation de ValidationSettings  

 Par défaut, toutes les activités dans l'arborescence d'activité sont évaluées lorsque la validation est appelée par <xref:System.Activities.Validation.ActivityValidationServices>. <xref:System.Activities.Validation.ValidationSettings> vous permet de personnaliser la validation de plusieurs façons différentes en configurant ses trois propriétés. <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> spécifie si le validateur doit parcourir l'arborescence d'activité entière ou uniquement appliquer la logique de validation à l'activité fournie. La valeur par défaut pour ce paramètre est `false`. <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> spécifie un mappage de contraintes supplémentaires, d'un type vers une liste de contraintes. Pour le type de base de chaque activité de l'arborescence en cours de validation, il existe une recherche dans la propriété <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. Si une liste de contraintes correspondante est trouvée, toutes les contraintes de la liste sont évaluées pour l'activité. <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> spécifie si le validateur doit évaluer toutes les contraintes ou seulement celles spécifiées dans la propriété <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. La valeur par défaut est `false`. Grâce aux propriétés <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> et <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A>, les auteurs hôtes de flux de travail peuvent ajouter une validation supplémentaire pour les flux de travail comme les contraintes de stratégie pour les outils tels que FxCop. Pour plus d’informations sur les contraintes, consultez [contraintes déclaratives](declarative-constraints.md).  
  
 Pour utiliser l'objet <xref:System.Activities.Validation.ValidationSettings>, configurez les propriétés de votre choix, puis passez-le dans l'appel à la méthode <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Dans cet exemple, un flux de travail, qui consiste en un objet <xref:System.Activities.Statements.Sequence> avec une activité `Add` personnalisée, est validé. L’activité `Add` compte deux arguments requis.  
  
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
  
 L’activité `Add` suivante est utilisée dans un objet <xref:System.Activities.Statements.Sequence>, mais ses deux arguments requis ne sont pas liés.  
  
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
  
 Pour l’exemple suivant, la validation est effectuée avec la propriété <xref:System.Activities.Validation.ValidationSettings.SingleLevel%2A> définie sur `true`. Aussi seule l’activité <xref:System.Activities.Statements.Sequence> racine est-elle validée.  
  
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
  
 Ce code affiche la sortie suivante :  
  
 **Aucun avertissement ni aucune erreur** Même si l' `Add` activité comporte des arguments requis qui ne sont pas liés, la validation est réussie, car seule l’activité racine est évaluée. Ce type de validation est utile pour valider uniquement des éléments particuliers d’une arborescence d’activité, par exemple pour valider, dans un concepteur, une modification de propriété d’une activité unique. Notez que si ce workflow est appelé, la validation complète configurée dans le workflow est évaluée et <xref:System.Activities.InvalidWorkflowException> est levée. <xref:System.Activities.Validation.ActivityValidationServices> et <xref:System.Activities.Validation.ValidationSettings> configurent uniquement la validation explicitement appelée par l'hôte, et non la validation qui a lieu lors de l'appel d'un flux de travail.
