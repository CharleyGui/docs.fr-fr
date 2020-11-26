---
title: Expressions C#
ms.date: 03/30/2017
ms.assetid: 29110be7-f4e3-407e-8dbe-78102eb21115
ms.openlocfilehash: b0e5d7f2fbb1f7b84c6d8f0110bd111165f0ea52
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239612"
---
# <a name="c-expressions"></a>Expressions C#

À compter de .NET Framework 4,5, les expressions C# sont prises en charge dans Windows Workflow Foundation (WF). Les nouveaux projets de workflow C# créés dans Visual Studio 2012 qui ciblent .NET Framework 4,5 utilisent des expressions C#, et les projets de flux de travail Visual Basic utilisent des expressions Visual Basic. Les projets de flux de travail .NET Framework 4 existants qui utilisent des expressions Visual Basic peuvent être migrés vers [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] quel que soit le langage du projet et sont pris en charge. Cette rubrique fournit une vue d'ensemble des expressions C# dans [!INCLUDE[wf1](../../../includes/wf1-md.md)].

## <a name="using-c-expressions-in-workflows"></a>Utilisation des expressions C# dans les workflows

- [Utilisation des expressions C# dans Workflow Designer](csharp-expressions.md#WFDesigner)

  - [Compatibilité descendante](csharp-expressions.md#BackwardCompat)

- [Utilisation des expressions C# dans les workflows avec code](csharp-expressions.md#CodeWorkflows)

- [Utilisation des expressions C# dans les workflows XAML](csharp-expressions.md#XamlWorkflows)

  - [XAML compilé](csharp-expressions.md#CompiledXaml)

  - [XAML libre](csharp-expressions.md#LooseXaml)

- [Utilisation des expressions C# dans les services de workflow XAMLX](csharp-expressions.md#WFServices)

### <a name="using-c-expressions-in-the-workflow-designer"></a><a name="WFDesigner"></a> Utilisation d’expressions C# dans le Concepteur de flux de travail

À compter de .NET Framework 4,5, les expressions C# sont prises en charge dans Windows Workflow Foundation (WF). Les projets de workflow c# créés dans Visual Studio 2012 qui ciblent .NET Framework 4,5 utilisent des expressions C#, tandis que les Visual Basic projets de workflow utilisent des expressions Visual Basic. Pour spécifier l’expression C# souhaitée, tapez-la dans la zone intitulée **entrer une expression c#**. Cette étiquette s'affiche dans la fenêtre de propriétés lorsque l'activité est sélectionnée dans le concepteur, ou sur l'activité dans Workflow Designer. Dans l'exemple suivant, deux activités `WriteLine` sont contenues dans `Sequence` à l'intérieur de `NoPersistScope`.

![Capture d’écran montrant une activité de séquence créée automatiquement.](./media/csharp-expressions/auto-surround-sequence-activity.png)

> [!NOTE]
> Les expressions C# sont prises en charge uniquement dans Visual Studio et ne sont pas prises en charge dans le concepteur de flux de travail réhébergé. Pour plus d’informations sur les nouvelles fonctionnalités WF45 prises en charge dans le concepteur réhébergé, consultez [prise en charge des nouvelles fonctionnalités de Workflow Foundation 4,5 dans le concepteur de flux de travail](wf-features-in-the-rehosted-workflow-designer.md)réhébergé.

#### <a name="backwards-compatibility"></a><a name="BackwardCompat"></a> Compatibilité descendante

Visual Basic expressions dans des projets de flux de travail .NET Framework 4 C# existants qui ont été migrés vers [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] sont prises en charge. Lorsque les expressions Visual Basic sont affichées dans le concepteur de workflow, le texte de l’expression Visual Basic existante est remplacé par la **valeur définie en XAML**, à moins que l’expression Visual Basic soit une syntaxe C# valide. Si l'expression Visual Basic correspond à une syntaxe C# valide, elle s'affiche. Pour mettre à jour les expressions Visual Basic en C#, modifiez-les dans le concepteur de workflow et spécifiez l'expression C# équivalente. Il n'est pas nécessaire de mettre à jour les expressions Visual Basic vers C#, mais une fois les expressions mises à jour dans le concepteur de workflow, elles sont converties en C# et ne peuvent pas être rétablies en Visual Basic.

### <a name="using-c-expressions-in-code-workflows"></a><a name="CodeWorkflows"></a> Utilisation d’expressions C# dans les flux de travail de code

Les expressions C# sont prises en charge dans les workflows basés sur du code [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], mais vous devez compiler les expressions C# à l'aide de <xref:System.Activities.XamlIntegration.TextExpressionCompiler.Compile%2A?displayProperty=nameWithType> pour pouvoir appeler le workflow. Les auteurs de workflow peuvent utiliser `CSharpValue` comme r-value dans une expression, et `CSharpReference` comme l-value dans une expression. Dans l'exemple suivant, un workflow qui contient une activité `Assign` est créé et une activité consistant en une activité `WriteLine` est contenue dans une activité `Sequence`. `CSharpReference` est spécifié pour l’argument `To` de l’activité `Assign`, et est utilisé comme l-value de l’expression. `CSharpValue` est spécifié pour l’argument `Value` d’`Assign`, et pour l’argument `Text` de `WriteLine`, et est utilisé comme r-value de ces deux expressions.

```csharp
Variable<int> n = new Variable<int>
{
    Name = "n"
};

Activity wf = new Sequence
{
    Variables = { n },
    Activities =
    {
        new Assign<int>
        {
            To = new CSharpReference<int>("n"),
            Value = new CSharpValue<int>("new Random().Next(1, 101)")
        },
        new WriteLine
        {
            Text = new CSharpValue<string>("\"The number is \" + n")
        }
    }
};

CompileExpressions(wf);

WorkflowInvoker.Invoke(wf);
```

Une fois que le workflow soit construit, les expressions C# sont compilées en appelant la méthode d'assistance `CompileExpressions`, puis le workflow. L'exemple suivant utilise la méthode `CompileExpressions`.

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```

> [!NOTE]
> Si les expressions C# ne sont pas compilées, une <xref:System.NotSupportedException> exception est levée lorsque le workflow est appelé avec un message similaire à ce qui suit : `Expression Activity type 'CSharpValue` 1 'nécessite une compilation pour pouvoir s’exécuter.  Vérifiez que le flux de travail a été compilé.»

Si votre workflow basé sur du code personnalisé utilise `DynamicActivity`, vous devez apporter des modifications à la méthode `CompileExpressions`, tel que l'indique l'exemple de code suivant.

```csharp
static void CompileExpressions(DynamicActivity dynamicActivity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions. For Dynamic Activities this can be retrieved using the
    // name property , which must be in the form Namespace.Type.
    string activityName = dynamicActivity.Name;

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = dynamicActivity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = true
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { dynamicActivity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation(
        dynamicActivity, compiledExpressionRoot);
}
```

Il existe plusieurs différences dans la surcharge de `CompileExpressions` qui compile les expressions C# dans une activité dynamique.

- Le paramètre `CompileExpressions` a la valeur `DynamicActivity`.

- Le nom de type et l'espace de noms sont récupérés à l'aide de la propriété `DynamicActivity.Name`.

- `TextExpressionCompilerSettings.ForImplementation` a la valeur `true`.

- `CompiledExpressionInvoker.SetCompiledExpressionRootForImplementation` est appelé au lieu de `CompiledExpressionInvoker.SetCompiledExpressionRoot`.

Pour plus d’informations sur l’utilisation des expressions dans le code, consultez [création de flux de travail, d’activités et d’expressions à l’aide du code impératif](authoring-workflows-activities-and-expressions-using-imperative-code.md).

### <a name="using-c-expressions-in-xaml-workflows"></a><a name="XamlWorkflows"></a> Utilisation d’expressions C# dans les workflows XAML

Les expressions C# sont prises en charge dans les workflows XAML. Les workflows XAML compilés sont compilés en un type, et workflows XAML libre sont chargés par le runtime et compilés dans une arborescence d’activité lorsque le workflow est exécuté.

- [XAML compilé](csharp-expressions.md#CompiledXaml)

- [XAML libre](csharp-expressions.md#LooseXaml)

#### <a name="compiled-xaml"></a><a name="CompiledXaml"></a> XAML compilé

Les expressions C# sont prises en charge dans les workflows XAML compilés qui sont compilés en un type dans le cadre d'un projet de workflow C# qui cible [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]. Le XAML compilé est le type par défaut de création de flux de travail dans Visual Studio, et les projets de flux de travail C# créés dans Visual Studio qui ciblent [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] utilisent des expressions c#.

#### <a name="loose-xaml"></a><a name="LooseXaml"></a> XAML libre

Les expressions C# sont prises en charge dans les workflows XAML libre. Le programme d'hôte de workflow qui charge et appelle le workflow XAML libre doit cibler [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], et <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> doit avoir la valeur `true` (la valeur par défaut est `false`). Pour affecter la valeur <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> à `true`, créez une instance <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings> dont la propriété <xref:System.Activities.XamlIntegration.ActivityXamlServicesSettings.CompileExpressions%2A> a la valeur `true`, et passez-la comme paramètre à <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A?displayProperty=nameWithType>. Si `CompileExpressions` n’a pas `true` la valeur, une est <xref:System.NotSupportedException> levée avec un message semblable au suivant : `Expression Activity type 'CSharpValue` 1 'nécessite une compilation pour pouvoir s’exécuter.  Vérifiez que le flux de travail a été compilé.»

```csharp
ActivityXamlServicesSettings settings = new ActivityXamlServicesSettings
{
    CompileExpressions = true
};

DynamicActivity<int> wf = ActivityXamlServices.Load(new StringReader(serializedAB), settings) as DynamicActivity<int>;
```

Pour plus d’informations sur l’utilisation des workflows XAML, consultez [sérialisation de workflows et d’activités vers et à partir de XAML](serializing-workflows-and-activities-to-and-from-xaml.md).

### <a name="using-c-expressions-in-xamlx-workflow-services"></a><a name="WFServices"></a> Utilisation d’expressions C# dans les services de flux de travail XAMLX

Les expressions C# sont prises en charge dans les services de workflow XAMLX. Lorsqu'un service de workflow est hébergé dans IIS ou WAS, aucune étape supplémentaire n'est nécessaire, mais si le service de workflow XAML est auto-hébergé, les expressions C# doivent être compilées. Pour compiler les expressions C# dans un service de workflow XAMLX auto-hébergé, commencez par charger le fichier XAMLX dans un `WorkflowService` , puis transmettez le `Body` de `WorkflowService` à la `CompileExpressions` méthode décrite dans la section précédente [utilisation des expressions C# dans les flux de travail de code](csharp-expressions.md#CodeWorkflows) . Dans l'exemple suivant, un service de workflow XAMLX est chargé, les expressions C# sont compilées, puis le service de workflow est ouvert et attend des demandes.

```csharp
// Load the XAMLX workflow service.
WorkflowService workflow1 =
    (WorkflowService)XamlServices.Load(xamlxPath);

// Compile the C# expressions in the workflow by passing the Body to CompileExpressions.
CompileExpressions(workflow1.Body);

// Initialize the WorkflowServiceHost.
var host = new WorkflowServiceHost(workflow1, new Uri("http://localhost:8293/Service1.xamlx"));

// Enable Metadata publishing/
ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
smb.HttpGetEnabled = true;
smb.MetadataExporter.PolicyVersion = PolicyVersion.Policy15;
host.Description.Behaviors.Add(smb);

// Open the WorkflowServiceHost and wait for requests.
host.Open();
Console.WriteLine("Press enter to quit");
Console.ReadLine();
```

Si les expressions C# ne sont pas compilées, l'opération `Open` réussit, mais le workflow échoue lorsqu'il est appelé. La `CompileExpressions` méthode suivante est la même que la méthode de la section précédente [utilisation des expressions C# dans les flux de travail de code](csharp-expressions.md#CodeWorkflows) .

```csharp
static void CompileExpressions(Activity activity)
{
    // activityName is the Namespace.Type of the activity that contains the
    // C# expressions.
    string activityName = activity.GetType().ToString();

    // Split activityName into Namespace and Type.Append _CompiledExpressionRoot to the type name
    // to represent the new type that represents the compiled expressions.
    // Take everything after the last . for the type name.
    string activityType = activityName.Split('.').Last() + "_CompiledExpressionRoot";
    // Take everything before the last . for the namespace.
    string activityNamespace = string.Join(".", activityName.Split('.').Reverse().Skip(1).Reverse());

    // Create a TextExpressionCompilerSettings.
    TextExpressionCompilerSettings settings = new TextExpressionCompilerSettings
    {
        Activity = activity,
        Language = "C#",
        ActivityName = activityType,
        ActivityNamespace = activityNamespace,
        RootNamespace = null,
        GenerateAsPartialClass = false,
        AlwaysGenerateSource = true,
        ForImplementation = false
    };

    // Compile the C# expression.
    TextExpressionCompilerResults results =
        new TextExpressionCompiler(settings).Compile();

    // Any compilation errors are contained in the CompilerMessages.
    if (results.HasErrors)
    {
        throw new Exception("Compilation failed.");
    }

    // Create an instance of the new compiled expression type.
    ICompiledExpressionRoot compiledExpressionRoot =
        Activator.CreateInstance(results.ResultType,
            new object[] { activity }) as ICompiledExpressionRoot;

    // Attach it to the activity.
    CompiledExpressionInvoker.SetCompiledExpressionRoot(
        activity, compiledExpressionRoot);
}
```
