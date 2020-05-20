---
title: Création de workflows, d'activités et d'expressions à l'aide du code impératif
description: Une définition de flux de travail Workflow Foundation est une arborescence d’objets d’activité configurés. Utilisez du code pour créer des définitions de flux de travail, des activités et des expressions.
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: d8b4cb8b85d3ea3759d58e15df823a72146772e8
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421551"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Création de workflows, d'activités et d'expressions à l'aide du code impératif
Une définition de workflow est une arborescence d’objets d’activité configurés. Cette arborescence d'activités peut être définie de nombreuses façons, notamment en modifiant manuellement des données XAML ou en utilisant le Workflow Designer pour produire  des données XAML. L'utilisation de XAML n'est toutefois pas impérative. Les définitions de workflow peuvent également être créées par programmation. Cette rubrique fournit une vue d'ensemble de la création des définitions, des activités et des expressions de workflow à l'aide du code. Pour obtenir des exemples d’utilisation de workflows XAML à l’aide de code, consultez [sérialisation de workflows et d’activités vers et à partir de XAML](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Création de définitions de workflow  
 Une définition de workflow peut être créée en instanciant une instance d'un type d'activité et configurant les propriétés de l'objet d'activité. Pour les activités qui ne contiennent pas d'activités enfants, cette opération peut être effectuée à l'aide de quelques lignes de code.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
> Les exemples de cette rubrique utilisent <xref:System.Activities.WorkflowInvoker> pour exécuter les exemples de workflow. Pour plus d’informations sur l’appel de workflows, le passage d’arguments et les différents choix d’hébergement disponibles, consultez [utilisation de WorkflowInvoker et WorkflowApplication](using-workflowinvoker-and-workflowapplication.md).  
  
 Dans cet exemple, un workflow qui consiste en une activité <xref:System.Activities.Statements.WriteLine> unique est créé. L'argument <xref:System.Activities.Statements.WriteLine> de l'activité <xref:System.Activities.Statements.WriteLine.Text%2A> est défini et le workflow est appelé. Si une activité contient des activités enfants, la méthode de construction est semblable. L'exemple suivant utilise une activité <xref:System.Activities.Statements.Sequence> qui contient deux activités <xref:System.Activities.Statements.WriteLine>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Utilisation d'initialiseurs d'objets  
 Les exemples de cette rubrique utilisent la syntaxe d'initialisation d'objet. La syntaxe d'initialisation d'objet peut être une méthode utile pour créer des définitions de workflow dans le code, car elle fournit une vue hiérarchique des activités dans le workflow et affiche la relation entre les activités. Il n'est pas impératif d'utiliser la syntaxe d'initialisation d'objet lorsque vous créez des workflows par programmation. L'exemple suivant est d'un point de vue fonctionnel équivalent à l'exemple précédent :  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Pour plus d’informations sur les initialiseurs d’objets, consultez [Comment : initialiser des objets sans appeler de constructeur (Guide de programmation C#)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) et [Comment : déclarer un objet à l’aide d’un initialiseur d’objet](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Utilisation de variables, de valeurs littérales et d'expressions  
 Lorsque vous créez une définition de workflow à l'aide de code, tenez compte de ce que le code exécute dans le cadre de la création de la définition de workflow et de ce qu'il exécute dans le cadre de l'exécution d'une instance de ce workflow. Par exemple, le workflow suivant est conçu pour générer un nombre aléatoire et l'écrire dans la console.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Lorsque ce code de définition de workflow est exécuté, l'appel à `Random.Next` est passé et le résultat est stocké dans la définition de workflow comme valeur littérale. De nombreuses instances de ce workflow peuvent être appelées et toutes afficheraient le même nombre. Pour que la génération du nombre aléatoire ait lieu pendant l'exécution du workflow, une expression qui est évaluée à chaque exécution du workflow doit être utilisée. Dans l'exemple suivant, une expression Visual Basic est utilisée avec <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 L'expression dans l'exemple précédent pourrait également être implémentée à l'aide de <xref:Microsoft.CSharp.Activities.CSharpValue%601> et d'une expression C#.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 Les expressions C# doivent être compilées avant que le workflow qui les contient ne soit appelé. Si les expressions C# ne sont pas compilées, une <xref:System.NotSupportedException> exception est levée lorsque le workflow est appelé avec un message similaire à ce qui suit : ``Expression Activity type 'CSharpValue`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.`` dans la plupart des scénarios impliquant des flux de travail créés dans Visual Studio, les expressions c# sont compilées automatiquement, mais dans certains scénarios, tels que les flux de travail de code, les expressions c# doivent être compilées manuellement. Pour obtenir un exemple de compilation d’expressions C#, consultez la section [utilisation d’expressions c# dans les flux de travail de code](csharp-expressions.md#CodeWorkflows) de la rubrique [expressions c#](csharp-expressions.md) .  
  
 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> représente une expression dans la syntaxe Visual Basic qui peut être utilisée comme r-value dans une expression et <xref:Microsoft.CSharp.Activities.CSharpValue%601> représente une expression dans la syntaxe C# qui peut être utilisée comme r-value dans une expression. Ces expressions sont évaluées chaque fois que l'activité conteneur est exécutée. Le résultat de l'expression est affecté à la variable de workflow `n` et ces résultats sont utilisés par l'activité suivante dans le workflow. Pour accéder à la valeur de la variable de workflow `n` au moment de l'exécution, le <xref:System.Activities.ActivityContext> est requis. Elle est accessible à l’aide de l’expression lambda suivante.  
  
> [!NOTE]
> Notez que ces deux exemples de code utilisent C# comme langage de programmation, mais l'un d'eux utilise <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> et l'autre utilise <xref:Microsoft.CSharp.Activities.CSharpValue%601>. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> et <xref:Microsoft.CSharp.Activities.CSharpValue%601> peuvent être utilisés dans les projets Visual Basic et C#. Par défaut, les expressions créées dans le concepteur de workflow correspondent au langage du projet d'hébergement. Lors de la création des workflows dans le code, le langage souhaité est à la discrétion de l'auteur de workflow.  
  
 Dans ces exemples, le résultat de l'expression est affecté à la variable de workflow `n` et ces résultats sont utilisés par l'activité suivante dans le workflow. Pour accéder à la valeur de la variable de workflow `n` au moment de l'exécution, le <xref:System.Activities.ActivityContext> est requis. Elle est accessible à l’aide de l’expression lambda suivante.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Pour plus d’informations sur les expressions lambda, consultez [expressions lambda (Guide de programmation C#)](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ou [expressions lambda (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Les expressions lambda ne sont pas sérialisables au format XAML. Si une tentative de sérialiser un workflow avec les expressions lambda est faite, <xref:System.Activities.Expressions.LambdaSerializationException> est levée avec le message suivant : « Ce workflow contient des expressions lambda spécifiées dans le code. Ces expressions ne peuvent pas être sérialisées en XAML. Pour cela, utilisez VisualBasicValue/VisualBasicReference ou ExpressionServices.Convert(lambda). Cela convertira les expressions lambda en activités d'expressions. » Pour rendre cette expression compatible avec XAML, utilisez <xref:System.Activities.Expressions.ExpressionServices> et <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>, comme illustré dans l'exemple suivant.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 Un <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> pourrait également être utilisé. Notez qu'aucune expression lambda n'est requise lors de l'utilisation d'une expression Visual Basic.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 Au moment de l'exécution, les expressions Visual Basic sont compilées dans des expressions LINQ. Les deux exemples précédents sont sérialisables en XAML, mais si le code XAML sérialisé est conçu pour être affiché et modifié dans le concepteur de workflow, utilisez <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> pour vos expressions. Les workflows sérialisés qui utilisent `ExpressionServices.Convert` peuvent être ouverts dans le concepteur, mais la valeur de l'expression sera vide. Pour plus d’informations sur la sérialisation des flux de travail en XAML, consultez [sérialisation de workflows et d’activités vers et à partir de XAML](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Expressions littérales et types de référence  
 Les expressions littérales sont représentées dans les workflows par l'activité <xref:System.Activities.Expressions.Literal%601>. Les activités <xref:System.Activities.Statements.WriteLine> suivantes sont équivalentes du point de vue fonctionnel.  
  
```csharp  
new WriteLine  
{  
    Text = "Hello World."  
},  
new WriteLine  
{  
    Text = new Literal<string>("Hello World.")  
}  
```  
  
 Elle n'est pas valide pour initialiser une expression littérale avec un type de référence, sauf <xref:System.String>. Dans l'exemple suivant, la propriété <xref:System.Activities.Statements.Assign> d'une activité <xref:System.Activities.Statements.Assign.Value%2A> est initialisée avec une expression littérale à l'aide de `List<string>`.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Lorsque le workflow contenant cette activité est validé, l'erreur de validation suivante est retournée : « Un littéral prend uniquement en charge les types valeur et le type immuable System.String. Le type System.Collections.Generic.List`1[System.String] ne peut pas être utilisé comme littéral. » Si le workflow est appelé, il lève une <xref:System.Activities.InvalidWorkflowException> qui contient le texte de l'erreur de validation. Il s’agit d’une erreur de validation, car la création d’une expression littérale avec un type de référence ne crée pas de nouvelle instance du type de référence pour chaque instance du workflow. Pour résoudre ce problème, remplacez l'expression littérale par une expression qui crée et retourne une nouvelle instance du type de référence.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 Pour plus d’informations sur les expressions, consultez [expressions](expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Appeler des méthodes sur des objets à l'aide d'expressions et de l'activité InvokeMethod  
 L'activité <xref:System.Activities.Expressions.InvokeMethod%601> peut être utilisée pour appeler les méthodes statiques et d'instance des classes dans le .NET Framework. Dans un exemple précédent de cette rubrique, un nombre aléatoire a été généré à l'aide de la classe <xref:System.Random>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 L'activité <xref:System.Activities.Expressions.InvokeMethod%601> peut avoir été utilisée pour appeler la méthode <xref:System.Random.Next%2A> de classe <xref:System.Random>.  
  
```csharp  
new InvokeMethod<int>  
{  
    TargetObject = new InArgument<Random>(new VisualBasicValue<Random>("New Random()")),  
    MethodName = "Next",  
    Parameters =
    {  
        new InArgument<int>(1),  
        new InArgument<int>(101)  
    },  
    Result = n  
}  
```  
  
 Étant donné que <xref:System.Random.Next%2A> n'est pas une méthode statique, une instance de la classe <xref:System.Random> est fournie pour la propriété <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>. Dans cet exemple une nouvelle instance est créée à l'aide d'une expression Visual Basic, mais elle peut également avoir été créée précédemment et stockée dans une variable de workflow. Dans cet exemple, il serait plus simple d'utiliser l'activité <xref:System.Activities.Statements.Assign%601> plutôt que l'activité <xref:System.Activities.Expressions.InvokeMethod%601>. Si l'appel de la méthode appelée en dernier lieu par l'activité <xref:System.Activities.Statements.Assign%601> ou <xref:System.Activities.Expressions.InvokeMethod%601> est long, <xref:System.Activities.Expressions.InvokeMethod%601> présente un avantage, car il a une propriété <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A>. Lorsque cette propriété a la valeur `true`, la méthode appelée s'exécute de façon asynchrone par rapport au workflow. Si d'autres activités existent en parallèle, elles ne seront pas bloquées pendant que la méthode s'exécute de façon asynchrone. En outre, si la méthode à appeler n'a aucune valeur de retour, <xref:System.Activities.Expressions.InvokeMethod%601> est la méthode appropriée pour appeler la méthode.  
  
## <a name="arguments-and-dynamic-activities"></a>Arguments et activités dynamiques  
 Une définition de workflow est créée dans le code en assemblant des activités dans une arborescence d’activité et en configurant l’ensemble des propriétés et arguments. Les arguments existants peuvent être liés, mais les nouveaux arguments ne peuvent pas être ajoutés aux activités. Cela inclut les arguments de workflow passés à l’activité racine. Dans le code impératif, les arguments de workflow sont spécifiés comme propriétés sur un nouveau type CLR et, en XAML, ils sont déclarés à l'aide de `x:Class` et `x:Member`. Étant donné qu'il n'existe aucun nouveau type CLR créé lorsqu'une définition de workflow est créée comme une arborescence d'objets en mémoire, les arguments ne peuvent pas être ajoutés. Toutefois, les arguments peuvent être ajoutés à une <xref:System.Activities.DynamicActivity>. Dans cet exemple, un <xref:System.Activities.DynamicActivity%601> qui accepte deux arguments entiers, les additionne et retourne le résultat est créé. Une <xref:System.Activities.DynamicActivityProperty> est créée pour chaque argument et le résultat de l’opération est affecté à l’argument <xref:System.Activities.Activity%601.Result%2A> de <xref:System.Activities.DynamicActivity%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Pour plus d’informations sur les activités dynamiques, consultez [création d’une activité au moment de l’exécution](creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Activités compilées  
 Les activités dynamiques sont un moyen de définir une activité qui contient des arguments à l’aide du code, mais les activités peuvent également être créées dans le code et être compilées en types. Il est possible de créer des activités simples qui dérivent de <xref:System.Activities.CodeActivity>, et des activités asynchrones qui dérivent de <xref:System.Activities.AsyncCodeActivity>. Ces activités peuvent avoir des arguments, des valeurs de retour, et définir leur logique en utilisant du code impératif. Pour obtenir des exemples de création de ces types d’activités, consultez [classe de base CodeActivity](workflow-activity-authoring-using-the-codeactivity-class.md) et [création d’activités asynchrones](creating-asynchronous-activities-in-wf.md).  
  
 Les activités qui dérivent de <xref:System.Activities.NativeActivity> peuvent définir leur logique à l'aide du code impératif et elles peuvent également contenir des activités enfants qui définissent la logique. Ils ont également un accès complet aux fonctionnalités du runtime telles que la création de signets. Pour obtenir des exemples de création d’une <xref:System.Activities.NativeActivity> activité basée sur, consultez [classe de base NativeActivity](nativeactivity-base-class.md), [Comment : créer une activité](how-to-create-an-activity.md)et l’exemple [composite personnalisé à l’aide d’une activité Native](./samples/custom-composite-using-native-activity.md) .  
  
 Les activités qui dérivent de <xref:System.Activities.Activity> définissent leur logique uniquement via l'utilisation d'activités enfants. Ces activités sont généralement créées à l'aide du concepteur de workflow Designer, mais peuvent également être définies à l'aide du code. Dans l'exemple suivant, une activité `Square` qui dérive d'`Activity<int>` est définie. L'activité `Square` a un seul <xref:System.Activities.InArgument%601> nommé `Value`, et définit sa logique en spécifiant une activité <xref:System.Activities.Statements.Sequence> à l'aide de la propriété <xref:System.Activities.Activity.Implementation%2A>. L'activité <xref:System.Activities.Statements.Sequence> contient une activité <xref:System.Activities.Statements.WriteLine> et une activité <xref:System.Activities.Statements.Assign%601>. Ensemble, ces trois activités implémentent la logique de l'activité `Square`.  
  
```csharp  
class Square : Activity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Value { get; set; }  
  
    public Square()  
    {  
        this.Implementation = () => new Sequence  
        {  
            Activities =  
            {  
                new WriteLine  
                {  
                    Text = new InArgument<string>((env) => "Squaring the value: " + this.Value.Get(env))  
                },  
                new Assign<int>  
                {  
                    To = new OutArgument<int>((env) => this.Result.Get(env)),  
                    Value = new InArgument<int>((env) => this.Value.Get(env) * this.Value.Get(env))  
                }  
            }  
        };  
    }  
}  
```  
  
 L'exemple suivant appelle une définition de workflow composée d'une activité `Square` unique à l'aide de <xref:System.Activities.WorkflowInvoker>.  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 Lorsque le workflow est appelé, la sortie suivante s'affiche sur la console :  
  
 **Mise au carré de la valeur : 5**  
**Résultat : 25**
