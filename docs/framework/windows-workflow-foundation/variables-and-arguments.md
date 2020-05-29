---
title: Variables et arguments
description: Cet article décrit les variables, qui représentent le stockage des données, et les arguments qui représentent le flux de données vers/à partir d’une activité dans Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 5cce9931e9b0a37d5fafbfb84527ffd543a0a50f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201958"
---
# <a name="variables-and-arguments"></a>Variables et arguments
Dans Windows Workflow Foundation (WF), les variables représentent le stockage de données et les arguments représentent le flux de données à l’intérieur et à l’extérieur d’une activité. Une activité a un ensemble d'arguments et ils composent la signature de l'activité. En outre, une activité peut gérer une liste de variables dans laquelle un développeur peut ajouter ou supprimer des variables pendant la conception d'un workflow. Un argument est lié à l'aide d'une expression qui retourne une valeur.  
  
## <a name="variables"></a>Variables  
 Les variables sont des emplacements de stockage pour les données. Les variables sont déclarées dans le cadre de la définition d'un workflow. Les variables prennent des valeurs au moment de l'exécution et ces valeurs sont stockées dans le cadre de l'état d'une instance de workflow. Une définition de variable spécifie le type de la variable et éventuellement le nom. Le code suivant indique comment déclarer une variable, lui affecter une valeur à l'aide d'une activité <xref:System.Activities.Statements.Assign%601>, puis afficher sa valeur dans la console à l'aide d'une activité <xref:System.Activities.Statements.WriteLine>.  
  
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
  
 Une expression de valeur par défaut peut être spécifiée éventuellement dans le cadre d'une déclaration de variable. Les variables peuvent également avoir des modificateurs. Par exemple, si une variable est en lecture seule, le modificateur <xref:System.Activities.VariableModifiers> en lecture seule peut être appliqué. Dans l'exemple suivant, une variable en lecture seule à laquelle une valeur par défaut est affectée est créée.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Portée des variables  
 La durée de vie d'une variable au moment de l'exécution est égale à la durée de vie de l'activité qui la déclare. Lorsqu'une activité est terminée, ses variables sont nettoyées et ne peuvent plus être référencées.  
  
## <a name="arguments"></a>Arguments  
 Les auteurs d'activités utilisent des arguments pour définir la façon dont les données passent à l'intérieur et à l'extérieur d'une activité. Chaque argument a une direction spécifiée : <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out> ou <xref:System.Activities.ArgumentDirection.InOut>.  
  
 L'exécution du workflow apporte les garanties suivantes sur le minutage des déplacements de données à l'intérieur et à l'extérieur des activités :  
  
1. Lorsque l'exécution d'une activité commence, les valeurs de tous ses arguments d'entrée et d'entrée/de sortie sont calculées. Par exemple, la valeur retournée est celle calculée par l'exécution avant son appel à <xref:System.Activities.Argument.Get%2A>, indépendamment du moment où `Execute` est appelé.  
  
2. Lorsque <xref:System.Activities.InOutArgument%601.Set%2A> est appelé, l'exécution définit immédiatement la valeur.  
  
3. Les arguments peuvent éventuellement avoir leur <xref:System.Activities.Argument.EvaluationOrder%2A> spécifié. <xref:System.Activities.Argument.EvaluationOrder%2A> est une valeur de base zéro qui spécifie l'ordre dans lequel l'argument est évalué. Par défaut, l'ordre d'évaluation de l'argument n'est pas spécifié et est égal à la valeur <xref:System.Activities.Argument.UnspecifiedEvaluationOrder>. Affectez à <xref:System.Activities.Argument.EvaluationOrder%2A> une valeur supérieure ou égale à zéro pour spécifier un ordre d’évaluation pour cet argument. Windows Workflow Foundation évalue les arguments avec un ordre d’évaluation spécifié dans l’ordre croissant. Notez que les arguments avec un ordre d'évaluation non spécifié sont évalués avant ceux avec un ordre d'évaluation spécifié.  
  
 Un auteur d’activité peut utiliser un mécanisme fortement typé pour exposer ses arguments. Pour ce faire, déclarez des propriétés de type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> et <xref:System.Activities.InOutArgument%601>. Cela permet à un auteur d'activité d'établir un contrat spécifique sur les données qui entrent dans une activité et en sortent.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Définition des arguments sur une activité  
 Des arguments peuvent être définis sur une activité en spécifiant des propriétés de type <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601> et <xref:System.Activities.InOutArgument%601>. Le code suivant indique comment définir les arguments pour une activité `Prompt` qui accepte une chaîne à afficher à l’intention de l’utilisateur et retourne une chaîne qui contient la réponse de l’utilisateur.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> Les activités qui retournent une valeur unique peuvent dériver de <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601> ou <xref:System.Activities.CodeActivity%601>. Ces activités ont un <xref:System.Activities.OutArgument%601> précis nommé <xref:System.Activities.Activity%601.Result%2A> qui contient la valeur de retour de l'activité.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Utilisation de variables et d’arguments dans les workflows  
 L’exemple suivant illustre comment les variables et arguments sont utilisés dans un workflow. Le workflow est une séquence qui déclare trois variables : `var1`, `var2` et `var3`. La première activité dans le workflow est une activité `Assign` qui affecte la valeur de la variable `var1` à la variable `var2`. Elle est suivie par une activité `WriteLine` qui imprime la valeur de la variable `var2`. Ensuite, une autre activité `Assign` affecte la valeur de la variable `var2` à la variable `var3`. Enfin, une autre activité `WriteLine` imprime la valeur de la variable `var3`. La première activité `Assign` utilise les objets `InArgument<string>` et `OutArgument<string>` qui représentent explicitement les liaisons pour les arguments de l’activité. `InArgument<string>` est utilisé pour <xref:System.Activities.Statements.Assign.Value%2A>, car la valeur est transférée dans l'activité <xref:System.Activities.Statements.Assign%601> via son argument <xref:System.Activities.Statements.Assign.Value%2A>, et `OutArgument<string>` est utilisé pour <xref:System.Activities.Statements.Assign.To%2A>, car la valeur est transférée de l'argument <xref:System.Activities.Statements.Assign.To%2A> à la variable. La deuxième activité `Assign` effectue la même opération avec une syntaxe plus compacte mais équivalente qui utilise des casts implicites. Les activités `WriteLine` utilisent également la syntaxe compacte.  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Utilisation de variables et d’arguments dans les activités basées sur le code  
 Les exemples précédents indiquent comment utiliser des arguments et des variables dans les workflows et les activités déclaratives. Les arguments et variables sont également utilisés dans les activités basées sur le code. Conceptuellement, l'utilisation est très semblable. Les variables représentent le stockage de données dans l’activité, et les arguments représentent le flux de données à l’intérieur ou à l’extérieur de l’activité et sont liés par l’auteur de workflow aux autres variables ou arguments dans le workflow qui représentent l’emplacement depuis ou vers lequel les données transitent. Pour obtenir ou définir la valeur d'une variable ou d'un argument dans une activité, un contexte d'activité qui représente l'environnement d'exécution actuel de l'activité doit être utilisé. Il est transmis à la méthode <xref:System.Activities.CodeActivity%601.Execute%2A> de l'activité par l'exécution du workflow. Dans cet exemple, une activité `Add` personnalisée qui a deux arguments <xref:System.Activities.ArgumentDirection.In> est définie. Pour accéder à la valeur des arguments, la méthode <xref:System.Activities.Argument.Get%2A> est utilisée et le contexte passé par l’exécution du workflow est utilisé.  
  
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
  
 Pour plus d’informations sur l’utilisation des arguments, des variables et des expressions dans le code, consultez [création de flux de travail, d’activités et d’expressions à l’aide du code impératif](authoring-workflows-activities-and-expressions-using-imperative-code.md) et des [arguments requis et des groupes surchargés](required-arguments-and-overload-groups.md).
