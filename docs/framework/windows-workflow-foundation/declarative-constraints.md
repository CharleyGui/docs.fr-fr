---
title: Contraintes déclaratives
ms.date: 03/30/2017
ms.assetid: 67001ed1-7f4d-4ada-ae57-a31176901a53
ms.openlocfilehash: 321021e3d73daecae07268f33807c992414a7b4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182962"
---
# <a name="declarative-constraints"></a><span data-ttu-id="5787e-102">Contraintes déclaratives</span><span class="sxs-lookup"><span data-stu-id="5787e-102">Declarative Constraints</span></span>
<span data-ttu-id="5787e-103">Les contraintes déclaratives fournissent une méthode puissante de validation d’une activité et de ses relations avec d’autres activités.</span><span class="sxs-lookup"><span data-stu-id="5787e-103">Declarative constraints provide a powerful method of validation for an activity and its relationships with other activities.</span></span> <span data-ttu-id="5787e-104">Les contraintes sont configurées pour une activité pendant le processus de création, mais les contraintes supplémentaires peuvent également être spécifiées par l'hôte du workflow.</span><span class="sxs-lookup"><span data-stu-id="5787e-104">Constraints are configured for an activity during the authoring process, but additional constraints can also be specified by the workflow host.</span></span> <span data-ttu-id="5787e-105">Cette rubrique fournit une vue d’ensemble de l’utilisation de contraintes déclaratives afin de fournir la validation d’activité.</span><span class="sxs-lookup"><span data-stu-id="5787e-105">This topic provides an overview of using declarative constraints to provide activity validation.</span></span>  
  
## <a name="using-declarative-constraints"></a><span data-ttu-id="5787e-106">Utilisation des contraintes déclaratives</span><span class="sxs-lookup"><span data-stu-id="5787e-106">Using Declarative Constraints</span></span>  
 <span data-ttu-id="5787e-107">Une contrainte est une activité qui contient la logique de validation.</span><span class="sxs-lookup"><span data-stu-id="5787e-107">A constraint is an activity that contains validation logic.</span></span> <span data-ttu-id="5787e-108">Cette activité de contrainte peut être créée dans le code ou en XAML.</span><span class="sxs-lookup"><span data-stu-id="5787e-108">This constraint activity can be authored in code or in XAML.</span></span> <span data-ttu-id="5787e-109">Une fois une activité de contrainte créée, les auteurs d’activités ajoutent cette contrainte à la propriété <xref:System.Activities.Activity.Constraints%2A> de l’activité à valider, ou ils utilisent la contrainte pour fournir la validation supplémentaire à l’aide de la propriété <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> d’une instance <xref:System.Activities.Validation.ValidationSettings>.</span><span class="sxs-lookup"><span data-stu-id="5787e-109">After a constraint activity is created, activity authors add this constraint to the <xref:System.Activities.Activity.Constraints%2A> property of the activity to validate, or they use the constraint to provide additional validation by using the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> property of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="5787e-110">La logique de validation peut consister en validations simples telles que la validation des métadonnées d'une activité, mais il peut également effectuer une validation qui tient compte de la relation de l'activité actuelle à son parent, enfants et activités de mêmes parents.</span><span class="sxs-lookup"><span data-stu-id="5787e-110">The validation logic can consist of simple validations such as validating an activity’s metadata, but it can also perform validation that takes into account the relationship of the current activity to its parent, children, and sibling activities.</span></span> <span data-ttu-id="5787e-111">Les contraintes sont créées à l’aide de l’activité <xref:System.Activities.Validation.Constraint%601>, et plusieurs activités de validation supplémentaires sont fournies pour aider à la création d’erreurs de validation et avertissements et fournir des informations à propos des activités connexes dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="5787e-111">Constraints are authored by using the <xref:System.Activities.Validation.Constraint%601> activity, and several additional validation activities are provided to assist with the creation of validation errors and warnings and to provide information about related activities in the workflow.</span></span>  
  
### <a name="assertvalidation-and-addvalidationerror"></a><span data-ttu-id="5787e-112">AssertValidation et AddValidationError</span><span class="sxs-lookup"><span data-stu-id="5787e-112">AssertValidation and AddValidationError</span></span>  
 <span data-ttu-id="5787e-113">L’activité <xref:System.Activities.Validation.AssertValidation> évalue l’expression référencée par sa propriété <xref:System.Activities.Validation.AssertValidation.Assertion%2A>, et si l’expression donne la valeur `false`, une erreur de validation ou un avertissement est ajoutée à <xref:System.Activities.Validation.ValidationResults>.</span><span class="sxs-lookup"><span data-stu-id="5787e-113">The <xref:System.Activities.Validation.AssertValidation> activity evaluates the expression referenced by its <xref:System.Activities.Validation.AssertValidation.Assertion%2A> property, and if the expression evaluates to `false`, a validation error or warning is added to the <xref:System.Activities.Validation.ValidationResults>.</span></span> <span data-ttu-id="5787e-114">La propriété <xref:System.Activities.Validation.AssertValidation.Message%2A> décrit l’erreur de validation et la propriété <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> indique si l’échec de la validation est une erreur ou un avertissement.</span><span class="sxs-lookup"><span data-stu-id="5787e-114">The <xref:System.Activities.Validation.AssertValidation.Message%2A> property describes the validation error and the <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> property indicates whether the validation failure is an error or a warning.</span></span> <span data-ttu-id="5787e-115">La valeur par défaut pour <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> est `false`.</span><span class="sxs-lookup"><span data-stu-id="5787e-115">The default value for <xref:System.Activities.Validation.AssertValidation.IsWarning%2A> is `false`.</span></span>  
  
 <span data-ttu-id="5787e-116">Dans l'exemple suivant, une contrainte est déclarée et renvoie un avertissement de validation si le <xref:System.Activities.Activity.DisplayName%2A> de l'activité qui est validée comprend deux caractères ou moins.</span><span class="sxs-lookup"><span data-stu-id="5787e-116">In the following example, a constraint is declared that returns a validation warning if the <xref:System.Activities.Activity.DisplayName%2A> of the activity being validated is two characters or less in length.</span></span> <span data-ttu-id="5787e-117">Le paramètre de type générique utilisé pour <xref:System.Activities.Validation.Constraint%601> spécifie le type d’activité validé par la contrainte.</span><span class="sxs-lookup"><span data-stu-id="5787e-117">The generic type parameter used for <xref:System.Activities.Validation.Constraint%601> specifies the type of activity that is validated by the constraint.</span></span> <span data-ttu-id="5787e-118">Cette contrainte utilise <xref:System.Activities.Activity> comme type générique et peut être utilisée pour valider tous les types d'activités.</span><span class="sxs-lookup"><span data-stu-id="5787e-118">This constraint uses <xref:System.Activities.Activity> as the generic type and can be used to validate all types of activities.</span></span>  
  
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
  
 <span data-ttu-id="5787e-119">Pour spécifier cette contrainte pour une activité, elle est ajoutée au <xref:System.Activities.Activity.Constraints%2A> de l'activité, comme indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="5787e-119">To specify this constraint for an activity, it is added to the <xref:System.Activities.Activity.Constraints%2A> of the activity, as shown in the following example code.</span></span>  
  
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
  
 <span data-ttu-id="5787e-120">Cette contrainte pourrait également être spécifiée pour les activités d'un workflow par l'hôte à l'aide de <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>. La section suivante explique la démarche à suivre.</span><span class="sxs-lookup"><span data-stu-id="5787e-120">The host could also specify this constraint for activities in a workflow by using <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A>, which is covered in the next section.</span></span>  
  
 <span data-ttu-id="5787e-121">L’activité <xref:System.Activities.Validation.AddValidationError> est utilisée pour générer une erreur de validation ou un avertissement sans recourir à l’évaluation d’une expression.</span><span class="sxs-lookup"><span data-stu-id="5787e-121">The <xref:System.Activities.Validation.AddValidationError> activity is used to generate a validation error or warning without requiring the evaluation of an expression.</span></span> <span data-ttu-id="5787e-122">Ses propriétés sont semblables à <xref:System.Activities.Validation.AssertValidation> et elle peut être utilisée avec des activités de contrôle de flux d'une contrainte telles que l'activité <xref:System.Activities.Statements.If>.</span><span class="sxs-lookup"><span data-stu-id="5787e-122">Its properties are similar to <xref:System.Activities.Validation.AssertValidation> and it can be used in conjunction with flow control activities of a constraint such as the <xref:System.Activities.Statements.If> activity.</span></span>
  
### <a name="workflow-relationship-activities"></a><span data-ttu-id="5787e-123">Activités de la relation du workflow</span><span class="sxs-lookup"><span data-stu-id="5787e-123">Workflow Relationship Activities</span></span>

<span data-ttu-id="5787e-124">Plusieurs activités de validation sont disponibles, qui fournissent des informations sur les autres activités dans le flux de travail par rapport à l’activité en cours de validation.</span><span class="sxs-lookup"><span data-stu-id="5787e-124">Several validation activities are available that provide information about the other activities in the workflow in relation to the activity being validated.</span></span> <span data-ttu-id="5787e-125"><xref:System.Activities.Validation.GetParentChain> retourne une collection d'activités qui contient toutes les activités entre l'activité actuelle et l'activité racine.</span><span class="sxs-lookup"><span data-stu-id="5787e-125"><xref:System.Activities.Validation.GetParentChain> returns a collection of activities that contains all of the activities between the current activity and the root activity.</span></span> <span data-ttu-id="5787e-126"><xref:System.Activities.Validation.GetChildSubtree> fournit une collection d'activités qui contient les activités enfants dans un modèle récurrent, et <xref:System.Activities.Validation.GetWorkflowTree> obtient toutes les activités dans le workflow.</span><span class="sxs-lookup"><span data-stu-id="5787e-126"><xref:System.Activities.Validation.GetChildSubtree> provides a collection of activities that contains the child activities in a recursive pattern, and <xref:System.Activities.Validation.GetWorkflowTree> gets all the activities in the workflow.</span></span>  
  
<span data-ttu-id="5787e-127">Dans l'exemple suivant, une activité `CreateState` est définie.</span><span class="sxs-lookup"><span data-stu-id="5787e-127">In the following example, a `CreateState` activity is defined.</span></span> <span data-ttu-id="5787e-128">L'activité `CreateState` doit être contenue dans une activité `CreateCountry`, et la méthode `GetParent` retourne une contrainte qui applique cette spécification.</span><span class="sxs-lookup"><span data-stu-id="5787e-128">The `CreateState` activity must be contained within a `CreateCountry` activity, and the `GetParent` method returns a constraint that enforces this requirement.</span></span> <span data-ttu-id="5787e-129">`GetParent` utilise l'activité <xref:System.Activities.Validation.GetParentChain> conjointement avec une activité <xref:System.Activities.Statements.ForEach%601> pour examiner les activités parentes de l'activité `CreateState` et déterminer si la spécification est satisfaite.</span><span class="sxs-lookup"><span data-stu-id="5787e-129">`GetParent` uses the <xref:System.Activities.Validation.GetParentChain> activity in conjunction with a <xref:System.Activities.Statements.ForEach%601> activity to inspect the parent activities of the `CreateState` activity to determine if the requirement is met.</span></span>  
  
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
  
## <a name="additional-constraints"></a><span data-ttu-id="5787e-130">Contraintes supplémentaires</span><span class="sxs-lookup"><span data-stu-id="5787e-130">Additional Constraints</span></span>  
 <span data-ttu-id="5787e-131">Les auteurs hôte du workflow peuvent spécifier des contraintes de validation supplémentaires pour les activités d'un workflow en créant des contraintes et en les ajoutant au dictionnaire <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> d'une instance <xref:System.Activities.Validation.ValidationSettings>.</span><span class="sxs-lookup"><span data-stu-id="5787e-131">Workflow host authors can specify additional validation constraints for activities in a workflow by creating constraints and adding them to the <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> dictionary of a <xref:System.Activities.Validation.ValidationSettings> instance.</span></span> <span data-ttu-id="5787e-132">Chaque élément dans <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contient le type d'activité pour laquelle les contraintes s'appliquent et une liste des contraintes supplémentaires pour ce type d'activité.</span><span class="sxs-lookup"><span data-stu-id="5787e-132">Each item in <xref:System.Activities.Validation.ValidationSettings.AdditionalConstraints%2A> contains the type of activity for which the constraints apply and a list of the additional constraints for that type of activity.</span></span> <span data-ttu-id="5787e-133">Lorsque la validation est appelée pour le workflow, chaque activité du type spécifié, notamment les classes dérivées, évalue les contraintes.</span><span class="sxs-lookup"><span data-stu-id="5787e-133">When validation is invoked for the workflow, each activity of the specified type, including derived classes, evaluates the constraints.</span></span> <span data-ttu-id="5787e-134">Dans cet exemple, la contrainte `ActivityDisplayNameIsNotSetWarning` de la section précédente est appliquée à toutes les activités dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="5787e-134">In this example, the `ActivityDisplayNameIsNotSetWarning` constraint from the previous section is applied to all activities in a workflow.</span></span>  
  
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
  
 <span data-ttu-id="5787e-135">Si la propriété <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> de <xref:System.Activities.Validation.ValidationSettings> est définie sur `true`, seules les contraintes supplémentaires spécifiées sont évaluées lorsque la validation est appelée en invoquant <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="5787e-135">If the <xref:System.Activities.Validation.ValidationSettings.OnlyUseAdditionalConstraints%2A> property of <xref:System.Activities.Validation.ValidationSettings> is `true`, then only the specified additional constraints are evaluated when validation is invoked by calling <xref:System.Activities.Validation.ActivityValidationServices.Validate%2A>.</span></span> <span data-ttu-id="5787e-136">Cela peut être utile pour inspecter les workflows et rechercher des configurations de validation spécifiques.</span><span class="sxs-lookup"><span data-stu-id="5787e-136">This can be useful for inspecting workflows for specific validation configurations.</span></span> <span data-ttu-id="5787e-137">Notez toutefois que lorsque le workflow est appelé, la logique de validation configurée dans le workflow est évaluée et doit aboutir pour que le workflow démarre avec succès.</span><span class="sxs-lookup"><span data-stu-id="5787e-137">Note however that when the workflow is invoked, the validation logic configured in the workflow is evaluated and must pass for the workflow to successfully begin.</span></span> <span data-ttu-id="5787e-138">Pour plus d’informations sur l’invocation de la validation, voir [Invoquant la validation de l’activité](invoking-activity-validation.md).</span><span class="sxs-lookup"><span data-stu-id="5787e-138">For more information about invoking validation, see [Invoking Activity Validation](invoking-activity-validation.md).</span></span>
