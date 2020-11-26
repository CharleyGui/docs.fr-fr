---
title: Contraintes déclaratives
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 9098a3d79337689fef6d37e4cccf3633d8128a10
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236453"
---
# <a name="declarative-constraints"></a>Contraintes déclaratives

Les contraintes déclaratives fournissent une méthode puissante de validation d’une activité et de ses relations avec d’autres activités. Les contraintes sont configurées pour une activité pendant le processus de création, mais les contraintes supplémentaires peuvent également être spécifiées par l'hôte du workflow. Cette rubrique fournit une vue d’ensemble de l’utilisation de contraintes déclaratives afin de fournir la validation d’activité.  
  
## <a name="using-declarative-constraints"></a>Utilisation des contraintes déclaratives  

 Une contrainte est une activité qui contient la logique de validation. Cette activité de contrainte peut être créée dans le code ou en XAML. Une fois une activité de contrainte créée, les auteurs d’activités ajoutent cette contrainte à la propriété <xref:System.Activities.Activity.Constraints%2A> de l’activité à valider, ou ils utilisent la contrainte pour fournir la validation supplémentaire à l’aide de la propriété <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> d’une instance <xref:System.Activities.Validation.ValidationSettings>. La logique de validation peut consister en validations simples telles que la validation des métadonnées d'une activité, mais il peut également effectuer une validation qui tient compte de la relation de l'activité actuelle à son parent, enfants et activités de mêmes parents. Les contraintes sont créées à l’aide de l’activité <xref:System.Activities.Validation.Constraint%601>, et plusieurs activités de validation supplémentaires sont fournies pour aider à la création d’erreurs de validation et avertissements et fournir des informations à propos des activités connexes dans le workflow.  
  
### <a name="assertvalidation-and-addvalidationerror"></a>AssertValidation et AddValidationError  

 L’activité <xref:System.Activities.Validation.AssertValidation> évalue l’expression référencée par sa propriété <xref:System.Activities.Validation.AssertValidation.Assertion%2A>, et si l’expression donne la valeur `false`, une erreur de validation ou un avertissement est ajoutée à <xref:System.Activities.Validation.ValidationResults>. La propriété <xref:System.Activities.Validation.AssertValidation.Message%2A> décrit l’erreur de validation et la propriété <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> indique si l’échec de la validation est une erreur ou un avertissement. La valeur par défaut pour <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> est `false`.  
  
 Dans l'exemple suivant, une contrainte est déclarée et renvoie un avertissement de validation si le <xref:System.Activities.Activity.DisplayName%2A> de l'activité qui est validée comprend deux caractères ou moins. Le paramètre de type générique utilisé pour <xref:System.Activities.Validation.Constraint%601> spécifie le type d’activité validé par la contrainte. Cette contrainte utilise <xref:System.Activities.Activity> comme type générique et peut être utilisée pour valider tous les types d'activités.  
  
```csharp  
public static Constraint ActivityDisplayNameIsNotSetWarning()  
{  
    DelegateInArgument<Activity> element = new DelegateInArgument<Activity>();  
  
    return new Constraint<Activity>  
    {  
        Body = new ActivityAction<Activity, ValidationContext>  
        {  
            Argument1 = element,  
            Handler = new AssertValidation  
            {  
                IsWarning = true,  
                Assertion = new InArgument<bool>(env => (element.Get(env).DisplayName.Length > 2)),  
                Message = new InArgument<string>("It is a best practice to have a DisplayName of more than 2 characters."),  
            }  
        }  
    };  
}  
```  
  
 Pour spécifier cette contrainte pour une activité, elle est ajoutée au <xref:System.Activities.Activity.Constraints%2A> de l'activité, comme indiqué dans l'exemple de code suivant.  
  
```csharp  
public sealed class SampleActivity : CodeActivity  
{  
    public SampleActivity()  
    {  
        base.Constraints.Add(ActivityDisplayNameIsNotSetWarning());  
    }  
  
    // Activity implementation omitted.  
}  
```  
  
 Cette contrainte pourrait également être spécifiée pour les activités d'un workflow par l'hôte à l'aide de <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. La section suivante explique la démarche à suivre.  
  
 L’activité <xref:System.Activities.Validation.AddValidationError> est utilisée pour générer une erreur de validation ou un avertissement sans recourir à l’évaluation d’une expression. Ses propriétés sont semblables à <xref:System.Activities.Validation.AssertValidation> et elle peut être utilisée avec des activités de contrôle de flux d'une contrainte telles que l'activité <xref:System.Activities.Statements.If>.
  
### <a name="workflow-relationship-activities"></a>Activités de la relation du workflow

Plusieurs activités de validation sont disponibles, qui fournissent des informations sur les autres activités dans le flux de travail par rapport à l’activité en cours de validation. <xref:System.Activities.Validation.GetParentChain> retourne une collection d'activités qui contient toutes les activités entre l'activité actuelle et l'activité racine. <xref:System.Activities.Validation.GetChildSubtree> fournit une collection d'activités qui contient les activités enfants dans un modèle récurrent, et <xref:System.Activities.Validation.GetWorkflowTree> obtient toutes les activités dans le workflow.  
  
Dans l'exemple suivant, une activité `CreateState` est définie. L'activité `CreateState` doit être contenue dans une activité `CreateCountry`, et la méthode `GetParent` retourne une contrainte qui applique cette spécification. `GetParent` utilise l'activité <xref:System.Activities.Validation.GetParentChain> conjointement avec une activité <xref:System.Activities.Statements.ForEach%601> pour examiner les activités parentes de l'activité `CreateState` et déterminer si la spécification est satisfaite.  
  
```csharp  
public sealed class CreateState : CodeActivity  
{  
    public CreateState()  
    {  
        base.Constraints.Add(CheckParent());  
        this.Cities = new List<Activity>();
    }  
  
    public List<Activity> Cities { get; set; }  
  
    public string Name { get; set; }
  
    static Constraint CheckParent()  
    {  
        DelegateInArgument<CreateState> element = new DelegateInArgument<CreateState>();  
        DelegateInArgument<ValidationContext> context = new DelegateInArgument<ValidationContext>();
        Variable<bool> result = new Variable<bool>();  
        DelegateInArgument<Activity> parent = new DelegateInArgument<Activity>();  
  
        return new Constraint<CreateState>  
        {
            Body = new ActivityAction<CreateState,ValidationContext>  
            {
                Argument1 = element,  
                Argument2 = context,  
                Handler = new Sequence  
                {  
                    Variables =  
                    {  
                        result
                    },  
                    Activities =  
                    {  
                        new ForEach<Activity>  
                        {
                            Values = new GetParentChain  
                            {  
                                ValidationContext = context
                            },  
                            Body = new ActivityAction<Activity>  
                            {
                                Argument = parent,
                                Handler = new If()  
                                {
                                    Condition = new InArgument<bool>((env) => object.Equals(parent.Get(env).GetType(),typeof(CreateCountry))),
                                    Then = new Assign<bool>  
                                    {  
                                        Value = true,  
                                        To = result  
                                    }  
                                }  
                            }
                        },  
                        new AssertValidation  
                        {  
                            Assertion = new InArgument<bool>(result),  
                            Message = new InArgument<string> ("CreateState has to be inside a CreateCountry activity"),
                        }  
                    }  
                }  
            }  
        };  
    }  
  
    protected override void Execute(CodeActivityContext context)  
    {  
        // not needed for the sample  
    }  
}  
```
  
## <a name="additional-constraints"></a>Contraintes supplémentaires  

 Les auteurs hôte du workflow peuvent spécifier des contraintes de validation supplémentaires pour les activités d'un workflow en créant des contraintes et en les ajoutant au dictionnaire <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> d'une instance <xref:System.Activities.Validation.ValidationSettings>. Chaque élément dans <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contient le type d'activité pour laquelle les contraintes s'appliquent et une liste des contraintes supplémentaires pour ce type d'activité. Lorsque la validation est appelée pour le workflow, chaque activité du type spécifié, notamment les classes dérivées, évalue les contraintes. Dans cet exemple, la contrainte `ActivityDisplayNameIsNotSetWarning` de la section précédente est appliquée à toutes les activités dans un workflow.  
  
```csharp  
Activity wf = new Sequence  
{  
    // Workflow Details Omitted.  
};  
  
ValidationSettings settings = new ValidationSettings()  
{  
  
    AdditionalConstraints =  
    {  
        {typeof(Activity), new List<Constraint> {ActivityDisplayNameIsNotSetWarning()}},
    }  
};  
  
// Validate the workflow.  
ValidationResults results = ActivityValidationServices.Validate(wf, settings);  
  
// Evaluate the results.  
if (results.Errors.Count == 0 && results.Warnings.Count == 0)  
{  
    Console.WriteLine("No warnings or errors");  
}  
else  
{  
    foreach (ValidationError error in results.Errors)  
    {  
        Console.WriteLine("Error in " + error.Source.DisplayName + ": " + error.Message);  
    }  
    foreach (ValidationError warning in results.Warnings)  
    {  
        Console.WriteLine("Warning in " + warning.Source.DisplayName + ": " + warning.Message);  
    }  
}  
```  
  
 Si la propriété <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> de <xref:System.Activities.Validation.ValidationSettings> est définie sur `true`, seules les contraintes supplémentaires spécifiées sont évaluées lorsque la validation est appelée en invoquant <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>. Cela peut être utile pour inspecter les workflows et rechercher des configurations de validation spécifiques. Notez toutefois que lorsque le workflow est appelé, la logique de validation configurée dans le workflow est évaluée et doit aboutir pour que le workflow démarre avec succès. Pour plus d’informations sur l’appel de validation, consultez [appel de validation d’activité](invoking-activity-validation.md).
