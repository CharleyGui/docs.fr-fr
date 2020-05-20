---
title: Variables et arguments
description: Cet article décrit les variables, qui représentent le stockage des données, et les arguments qui représentent le flux de données vers/à partir d’une activité dans Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 47b8a7bddc8c3a9a8427bcb3e93760a63e5fa976
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421304"
---
# <a name="variables-and-arguments"></a><span data-ttu-id="655db-103">Variables et arguments</span><span class="sxs-lookup"><span data-stu-id="655db-103">Variables and Arguments</span></span>
<span data-ttu-id="655db-104">Dans Windows Workflow Foundation (WF), les variables représentent le stockage de données et les arguments représentent le flux de données à l’intérieur et à l’extérieur d’une activité.</span><span class="sxs-lookup"><span data-stu-id="655db-104">In Windows Workflow Foundation (WF), variables represent the storage of data and arguments represent the flow of data into and out of an activity.</span></span> <span data-ttu-id="655db-105">Une activité a un ensemble d'arguments et ils composent la signature de l'activité.</span><span class="sxs-lookup"><span data-stu-id="655db-105">An activity has a set of arguments and they make up the signature of the activity.</span></span> <span data-ttu-id="655db-106">En outre, une activité peut gérer une liste de variables dans laquelle un développeur peut ajouter ou supprimer des variables pendant la conception d'un workflow.</span><span class="sxs-lookup"><span data-stu-id="655db-106">Additionally, an activity can maintain a list of variables to which a developer can add or remove variables during the design of a workflow.</span></span> <span data-ttu-id="655db-107">Un argument est lié à l'aide d'une expression qui retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="655db-107">An argument is bound using an expression that returns a value.</span></span>  
  
## <a name="variables"></a><span data-ttu-id="655db-108">Variables</span><span class="sxs-lookup"><span data-stu-id="655db-108">Variables</span></span>  
 <span data-ttu-id="655db-109">Les variables sont des emplacements de stockage pour les données.</span><span class="sxs-lookup"><span data-stu-id="655db-109">Variables are storage locations for data.</span></span> <span data-ttu-id="655db-110">Les variables sont déclarées dans le cadre de la définition d'un workflow.</span><span class="sxs-lookup"><span data-stu-id="655db-110">Variables are declared as part of the definition of a workflow.</span></span> <span data-ttu-id="655db-111">Les variables prennent des valeurs au moment de l'exécution et ces valeurs sont stockées dans le cadre de l'état d'une instance de workflow.</span><span class="sxs-lookup"><span data-stu-id="655db-111">Variables take on values at runtime and these values are stored as part of the state of a workflow instance.</span></span> <span data-ttu-id="655db-112">Une définition de variable spécifie le type de la variable et éventuellement le nom.</span><span class="sxs-lookup"><span data-stu-id="655db-112">A variable definition specifies the type of the variable and optionally, the name.</span></span> <span data-ttu-id="655db-113">Le code suivant indique comment déclarer une variable, lui affecter une valeur à l'aide d'une activité <xref:System.Activities.Statements.Assign%601>, puis afficher sa valeur dans la console à l'aide d'une activité <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="655db-113">The following code shows how to declare a variable, assign a value to it using an <xref:System.Activities.Statements.Assign%601> activity, and then display its value to the console using a <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="655db-114">Une expression de valeur par défaut peut être spécifiée éventuellement dans le cadre d'une déclaration de variable.</span><span class="sxs-lookup"><span data-stu-id="655db-114">A default value expression can optionally be specified as part of a variable declaration.</span></span> <span data-ttu-id="655db-115">Les variables peuvent également avoir des modificateurs.</span><span class="sxs-lookup"><span data-stu-id="655db-115">Variables also can have modifiers.</span></span> <span data-ttu-id="655db-116">Par exemple, si une variable est en lecture seule, le modificateur <xref:System.Activities.VariableModifiers> en lecture seule peut être appliqué.</span><span class="sxs-lookup"><span data-stu-id="655db-116">For example, if a variable is read-only then the read-only <xref:System.Activities.VariableModifiers> modifier can be applied.</span></span> <span data-ttu-id="655db-117">Dans l'exemple suivant, une variable en lecture seule à laquelle une valeur par défaut est affectée est créée.</span><span class="sxs-lookup"><span data-stu-id="655db-117">In the following example, a read-only variable is created that has a default value assigned.</span></span>  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a><span data-ttu-id="655db-118">Portée des variables</span><span class="sxs-lookup"><span data-stu-id="655db-118">Variable Scoping</span></span>  
 <span data-ttu-id="655db-119">La durée de vie d'une variable au moment de l'exécution est égale à la durée de vie de l'activité qui la déclare.</span><span class="sxs-lookup"><span data-stu-id="655db-119">The lifetime of a variable at runtime is equal to the lifetime of the activity that declares it.</span></span> <span data-ttu-id="655db-120">Lorsqu'une activité est terminée, ses variables sont nettoyées et ne peuvent plus être référencées.</span><span class="sxs-lookup"><span data-stu-id="655db-120">When an activity completes, its variables are cleaned up and can no longer be referenced.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="655db-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="655db-121">Arguments</span></span>  
 <span data-ttu-id="655db-122">Les auteurs d'activités utilisent des arguments pour définir la façon dont les données passent à l'intérieur et à l'extérieur d'une activité.</span><span class="sxs-lookup"><span data-stu-id="655db-122">Activity authors use arguments to define the way data flows into and out of an activity.</span></span> <span data-ttu-id="655db-123">Chaque argument a une direction spécifiée : <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out> ou <xref:System.Activities.ArgumentDirection.InOut>.</span><span class="sxs-lookup"><span data-stu-id="655db-123">Each argument has a specified direction: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, or <xref:System.Activities.ArgumentDirection.InOut>.</span></span>  
  
 <span data-ttu-id="655db-124">L'exécution du workflow apporte les garanties suivantes sur le minutage des déplacements de données à l'intérieur et à l'extérieur des activités :</span><span class="sxs-lookup"><span data-stu-id="655db-124">The workflow runtime makes the following guarantees about the timing of data movement into and out of activities:</span></span>  
  
1. <span data-ttu-id="655db-125">Lorsque l'exécution d'une activité commence, les valeurs de tous ses arguments d'entrée et d'entrée/de sortie sont calculées.</span><span class="sxs-lookup"><span data-stu-id="655db-125">When an activity starts executing, the values of all of its input and input/output arguments are calculated.</span></span> <span data-ttu-id="655db-126">Par exemple, la valeur retournée est celle calculée par l'exécution avant son appel à <xref:System.Activities.Argument.Get%2A>, indépendamment du moment où `Execute` est appelé.</span><span class="sxs-lookup"><span data-stu-id="655db-126">For example, regardless of when <xref:System.Activities.Argument.Get%2A> is called, the value returned is the one calculated by the runtime prior to its invocation of `Execute`.</span></span>  
  
2. <span data-ttu-id="655db-127">Lorsque <xref:System.Activities.InOutArgument%601.Set%2A> est appelé, l'exécution définit immédiatement la valeur.</span><span class="sxs-lookup"><span data-stu-id="655db-127">When <xref:System.Activities.InOutArgument%601.Set%2A> is called, the runtime sets the value immediately.</span></span>  
  
3. <span data-ttu-id="655db-128">Les arguments peuvent éventuellement avoir leur <xref:System.Activities.Argument.EvaluationOrder%2A> spécifié.</span><span class="sxs-lookup"><span data-stu-id="655db-128">Arguments can optionally have their <xref:System.Activities.Argument.EvaluationOrder%2A> specified.</span></span> <span data-ttu-id="655db-129"><xref:System.Activities.Argument.EvaluationOrder%2A> est une valeur de base zéro qui spécifie l'ordre dans lequel l'argument est évalué.</span><span class="sxs-lookup"><span data-stu-id="655db-129"><xref:System.Activities.Argument.EvaluationOrder%2A> is a zero-based value that specifies the order in which the argument is evaluated.</span></span> <span data-ttu-id="655db-130">Par défaut, l'ordre d'évaluation de l'argument n'est pas spécifié et est égal à la valeur <xref:System.Activities.Argument.UnspecifiedEvaluationOrder>.</span><span class="sxs-lookup"><span data-stu-id="655db-130">By default, the evaluation order of the argument is unspecified and is equal to the <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> value.</span></span> <span data-ttu-id="655db-131">Affectez à <xref:System.Activities.Argument.EvaluationOrder%2A> une valeur supérieure ou égale à zéro pour spécifier un ordre d’évaluation pour cet argument.</span><span class="sxs-lookup"><span data-stu-id="655db-131">Set <xref:System.Activities.Argument.EvaluationOrder%2A> to a value greater or equal to zero to specify an evaluation order for this argument.</span></span> <span data-ttu-id="655db-132">Windows Workflow Foundation évalue les arguments avec un ordre d’évaluation spécifié dans l’ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="655db-132">Windows Workflow Foundation evaluates arguments with a specified evaluation order in ascending order.</span></span> <span data-ttu-id="655db-133">Notez que les arguments avec un ordre d'évaluation non spécifié sont évalués avant ceux avec un ordre d'évaluation spécifié.</span><span class="sxs-lookup"><span data-stu-id="655db-133">Note that arguments with an unspecified evaluation order are evaluated before those with a specified evaluation order.</span></span>  
  
 <span data-ttu-id="655db-134">Un auteur d'activité peut utiliser un mécanisme fortement typé pour l'exposition de ses arguments.</span><span class="sxs-lookup"><span data-stu-id="655db-134">An activity author can use a strongly-typed mechanism for exposing its arguments.</span></span> <span data-ttu-id="655db-135">Pour ce faire, déclarez des propriétés de type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> et <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="655db-135">This is accomplished by declaring properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="655db-136">Cela permet à un auteur d'activité d'établir un contrat spécifique sur les données qui entrent dans une activité et en sortent.</span><span class="sxs-lookup"><span data-stu-id="655db-136">This allows an activity author to establish a specific contract about the data going into and out of an activity.</span></span>  
  
### <a name="defining-the-arguments-on-an-activity"></a><span data-ttu-id="655db-137">Définition des arguments sur une activité</span><span class="sxs-lookup"><span data-stu-id="655db-137">Defining the Arguments on an Activity</span></span>  
 <span data-ttu-id="655db-138">Des arguments peuvent être définis sur une activité en spécifiant des propriétés de type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> et <xref:System.Activities.InOutArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="655db-138">Arguments can be defined on an activity by specifying properties of type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, and <xref:System.Activities.InOutArgument%601>.</span></span> <span data-ttu-id="655db-139">Le code suivant indique comment définir les arguments pour une activité `Prompt` qui accepte une chaîne à afficher à l’intention de l’utilisateur et retourne une chaîne qui contient la réponse de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="655db-139">The following code shows how to define the arguments for a `Prompt` activity that takes in a string to display to the user and returns a string that contains the user's response.</span></span>  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="655db-140">Les activités qui retournent une valeur unique peuvent dériver de <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601> ou <xref:System.Activities.CodeActivity%601>.</span><span class="sxs-lookup"><span data-stu-id="655db-140">Activities that return a single value can derive from <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, or <xref:System.Activities.CodeActivity%601>.</span></span> <span data-ttu-id="655db-141">Ces activités ont un <xref:System.Activities.OutArgument%601> précis nommé <xref:System.Activities.Activity%601.Result%2A> qui contient la valeur de retour de l'activité.</span><span class="sxs-lookup"><span data-stu-id="655db-141">These activities have a well-defined <xref:System.Activities.OutArgument%601> named <xref:System.Activities.Activity%601.Result%2A> that contains the return value of the activity.</span></span>  
  
### <a name="using-variables-and-arguments-in-workflows"></a><span data-ttu-id="655db-142">Utilisation de variables et d’arguments dans les workflows</span><span class="sxs-lookup"><span data-stu-id="655db-142">Using Variables and Arguments in Workflows</span></span>  
 <span data-ttu-id="655db-143">L’exemple suivant illustre comment les variables et arguments sont utilisés dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="655db-143">The following example shows how variables and arguments are used in a workflow.</span></span> <span data-ttu-id="655db-144">Le workflow est une séquence qui déclare trois variables : `var1`, `var2` et `var3`.</span><span class="sxs-lookup"><span data-stu-id="655db-144">The workflow is a sequence that declares three variables: `var1`, `var2`, and `var3`.</span></span> <span data-ttu-id="655db-145">La première activité dans le workflow est une activité `Assign` qui affecte la valeur de la variable `var1` à la variable `var2`.</span><span class="sxs-lookup"><span data-stu-id="655db-145">The first activity in the workflow is an `Assign` activity that assigns the value of variable `var1` to the variable `var2`.</span></span> <span data-ttu-id="655db-146">Elle est suivie par une activité `WriteLine` qui imprime la valeur de la variable `var2`.</span><span class="sxs-lookup"><span data-stu-id="655db-146">This is followed by a `WriteLine` activity that prints the value of the `var2` variable.</span></span> <span data-ttu-id="655db-147">Ensuite, une autre activité `Assign` affecte la valeur de la variable `var2` à la variable `var3`.</span><span class="sxs-lookup"><span data-stu-id="655db-147">Next is another `Assign` activity that assigns the value of variable `var2` to the variable `var3`.</span></span> <span data-ttu-id="655db-148">Enfin, une autre activité `WriteLine` imprime la valeur de la variable `var3`.</span><span class="sxs-lookup"><span data-stu-id="655db-148">Finally there is another `WriteLine` activity that prints the value of the `var3` variable.</span></span> <span data-ttu-id="655db-149">La première activité `Assign` utilise les objets `InArgument<string>` et `OutArgument<string>` qui représentent explicitement les liaisons pour les arguments de l’activité.</span><span class="sxs-lookup"><span data-stu-id="655db-149">The first `Assign` activity uses `InArgument<string>` and `OutArgument<string>` objects that explicitly represent the bindings for the activity's arguments.</span></span> <span data-ttu-id="655db-150">`InArgument<string>` est utilisé pour <xref:System.Activities.Statements.Assign.Value%2A>, car la valeur est transférée dans l'activité <xref:System.Activities.Statements.Assign%601> via son argument <xref:System.Activities.Statements.Assign.Value%2A>, et `OutArgument<string>` est utilisé pour <xref:System.Activities.Statements.Assign.To%2A>, car la valeur est transférée de l'argument <xref:System.Activities.Statements.Assign.To%2A> à la variable.</span><span class="sxs-lookup"><span data-stu-id="655db-150">`InArgument<string>` is used for <xref:System.Activities.Statements.Assign.Value%2A> because the value is flowing into the <xref:System.Activities.Statements.Assign%601> activity through its <xref:System.Activities.Statements.Assign.Value%2A> argument, and `OutArgument<string>` is used for <xref:System.Activities.Statements.Assign.To%2A> because the value is flowing out of the <xref:System.Activities.Statements.Assign.To%2A> argument into the variable.</span></span> <span data-ttu-id="655db-151">La deuxième activité `Assign` effectue la même opération avec une syntaxe plus compacte mais équivalente qui utilise des casts implicites.</span><span class="sxs-lookup"><span data-stu-id="655db-151">The second `Assign` activity accomplishes the same thing with more compact but equivalent syntax that uses implicit casts.</span></span> <span data-ttu-id="655db-152">Les activités `WriteLine` utilisent également la syntaxe compacte.</span><span class="sxs-lookup"><span data-stu-id="655db-152">The `WriteLine` activities also use the compact syntax.</span></span>  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a><span data-ttu-id="655db-153">Utilisation de variables et d’arguments dans les activités basées sur le code</span><span class="sxs-lookup"><span data-stu-id="655db-153">Using Variables and Arguments in Code-Based Activities</span></span>  
 <span data-ttu-id="655db-154">Les exemples précédents indiquent comment utiliser des arguments et des variables dans les workflows et les activités déclaratives.</span><span class="sxs-lookup"><span data-stu-id="655db-154">The previous examples show how to use arguments and variables in workflows and declarative activities.</span></span> <span data-ttu-id="655db-155">Les arguments et variables sont également utilisés dans les activités basées sur le code.</span><span class="sxs-lookup"><span data-stu-id="655db-155">Arguments and variables are also used in code-based activities.</span></span> <span data-ttu-id="655db-156">Conceptuellement, l'utilisation est très semblable.</span><span class="sxs-lookup"><span data-stu-id="655db-156">Conceptually the usage is very similar.</span></span> <span data-ttu-id="655db-157">Les variables représentent le stockage de données dans l’activité, et les arguments représentent le flux de données à l’intérieur ou à l’extérieur de l’activité et sont liés par l’auteur de workflow aux autres variables ou arguments dans le workflow qui représentent l’emplacement depuis ou vers lequel les données transitent.</span><span class="sxs-lookup"><span data-stu-id="655db-157">Variables represent data storage within the activity, and arguments represent the flow of data into or out of the activity, and are bound by the workflow author to other variables or arguments in the workflow that represent where the data flows to or from.</span></span> <span data-ttu-id="655db-158">Pour obtenir ou définir la valeur d'une variable ou d'un argument dans une activité, un contexte d'activité qui représente l'environnement d'exécution actuel de l'activité doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="655db-158">To get or set the value of a variable or argument in an activity, an activity context must be used that represents the current execution environment of the activity.</span></span> <span data-ttu-id="655db-159">Il est transmis à la méthode <xref:System.Activities.CodeActivity%601.Execute%2A> de l'activité par l'exécution du workflow.</span><span class="sxs-lookup"><span data-stu-id="655db-159">This is passed into the <xref:System.Activities.CodeActivity%601.Execute%2A> method of the activity by the workflow runtime.</span></span> <span data-ttu-id="655db-160">Dans cet exemple, une activité `Add` personnalisée qui a deux arguments <xref:System.Activities.ArgumentDirection.In> est définie.</span><span class="sxs-lookup"><span data-stu-id="655db-160">In this example, a custom `Add` activity is defined that has two <xref:System.Activities.ArgumentDirection.In> arguments.</span></span> <span data-ttu-id="655db-161">Pour accéder à la valeur des arguments, la méthode <xref:System.Activities.Argument.Get%2A> est utilisée et le contexte passé par l’exécution du workflow est utilisé.</span><span class="sxs-lookup"><span data-stu-id="655db-161">To access the value of the arguments, the <xref:System.Activities.Argument.Get%2A> method is used and the context that was passed in by the workflow runtime is used.</span></span>  
  
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
  
 <span data-ttu-id="655db-162">Pour plus d’informations sur l’utilisation des arguments, des variables et des expressions dans le code, consultez [création de flux de travail, d’activités et d’expressions à l’aide du code impératif](authoring-workflows-activities-and-expressions-using-imperative-code.md) et des [arguments requis et des groupes surchargés](required-arguments-and-overload-groups.md).</span><span class="sxs-lookup"><span data-stu-id="655db-162">For more information about working with arguments, variables, and expressions in code, see [Authoring Workflows, Activities, and Expressions Using Imperative Code](authoring-workflows-activities-and-expressions-using-imperative-code.md) and [Required Arguments and Overload Groups](required-arguments-and-overload-groups.md).</span></span>
