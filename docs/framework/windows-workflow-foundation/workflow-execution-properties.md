---
title: Propriétés d'exécution de workflow
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: be9ae5924786ea1e23cc649034d927789c64e405
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293791"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="9eac3-102">Propriétés d'exécution de workflow</span><span class="sxs-lookup"><span data-stu-id="9eac3-102">Workflow Execution Properties</span></span>

<span data-ttu-id="9eac3-103">Par le biais du stockage local des threads (TLS), le CLR maintient un contexte d’exécution pour chaque thread.</span><span class="sxs-lookup"><span data-stu-id="9eac3-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="9eac3-104">Ce contexte d’exécution gouverne des propriétés de thread connues, telles que l’identité de thread, la transaction ambiante et le jeu d’autorisations actuel, en plus des propriétés de thread définies par l’utilisateur (comme les emplacements nommés).</span><span class="sxs-lookup"><span data-stu-id="9eac3-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="9eac3-105">Contrairement aux programmes qui ciblent directement le CLR, les programmes de workflow sont hiérarchiquement des arborescences de portée d'activités qui s'exécutent dans un environnement de thread agnostique.</span><span class="sxs-lookup"><span data-stu-id="9eac3-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="9eac3-106">Cela implique que les mécanismes de TLS standard ne peuvent pas être utilisés directement pour déterminer quel contexte se trouve dans la portée d’un élément de travail donné.</span><span class="sxs-lookup"><span data-stu-id="9eac3-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="9eac3-107">Par exemple, deux branches parallèles d'exécution peuvent utiliser des transactions différentes, mais le planificateur peut entrelacer leur exécution sur le même thread de CLR.</span><span class="sxs-lookup"><span data-stu-id="9eac3-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="9eac3-108">Les propriétés d'exécution de workflow fournissent un mécanisme permettant d'ajouter des propriétés spécifiques au contexte à l'environnement d'une activité.</span><span class="sxs-lookup"><span data-stu-id="9eac3-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="9eac3-109">Ainsi, une activité peut déclarer les propriétés incluses dans la portée pour la sous-arborescence associée, tout en fournissant des connexions pour la configuration et la destruction de TLS afin d’interagir correctement avec les objets CLR.</span><span class="sxs-lookup"><span data-stu-id="9eac3-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="9eac3-110">Création et utilisation de propriétés d'exécution de workflow</span><span class="sxs-lookup"><span data-stu-id="9eac3-110">Creating and Using Workflow Execution Properties</span></span>  

 <span data-ttu-id="9eac3-111">Les propriétés d'exécution du workflow implémentent généralement l'interface <xref:System.Activities.IExecutionProperty>, même si les propriétés axées sur la messagerie peuvent implémenter <xref:System.ServiceModel.Activities.ISendMessageCallback> et <xref:System.ServiceModel.Activities.IReceiveMessageCallback> à la place.</span><span class="sxs-lookup"><span data-stu-id="9eac3-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="9eac3-112">Pour créer une propriété d'exécution de workflow, créez une classe qui implémente l'interface <xref:System.Activities.IExecutionProperty> et qui implémente les membres <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> et <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="9eac3-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="9eac3-113">Ces membres fournissent à la propriété d'exécution la possibilité de configurer et détruire correctement le stockage local des threads lors de chaque impulsion de travail de l'activité qui contient la propriété, y compris ses activités enfants.</span><span class="sxs-lookup"><span data-stu-id="9eac3-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="9eac3-114">Dans cet exemple, `ConsoleColorProperty` est créé afin de définir `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="9eac3-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 <span data-ttu-id="9eac3-115">Les auteurs d'activité peuvent utiliser cette propriété en l'inscrivant dans la substitution d'exécution de l'activité.</span><span class="sxs-lookup"><span data-stu-id="9eac3-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="9eac3-116">Dans cet exemple, une activité `ConsoleColorScope` est définie afin d'inscrire `ConsoleColorProperty` en l'ajoutant à la collection <xref:System.Activities.NativeActivityContext.Properties%2A> du contexte <xref:System.Activities.NativeActivityContext> actuel.</span><span class="sxs-lookup"><span data-stu-id="9eac3-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="9eac3-117">Lorsque le corps de l'activité commence une impulsion de travail, la méthode <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> de la propriété est appelée, et quand l'impulsion de travail est terminée, la méthode <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> est appelée.</span><span class="sxs-lookup"><span data-stu-id="9eac3-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="9eac3-118">Dans cet exemple, un workflow est créé afin d’utiliser une activité <xref:System.Activities.Statements.Parallel> avec trois branches.</span><span class="sxs-lookup"><span data-stu-id="9eac3-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="9eac3-119">Les deux premières branches utilisent l'activité `ConsoleColorScope`, contrairement à la troisième branche.</span><span class="sxs-lookup"><span data-stu-id="9eac3-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="9eac3-120">Les trois branches contiennent deux activités <xref:System.Activities.Statements.WriteLine> et une activité <xref:System.Activities.Statements.Delay>.</span><span class="sxs-lookup"><span data-stu-id="9eac3-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="9eac3-121">Lorsque l’activité <xref:System.Activities.Statements.Parallel> est exécutée, les activités contenues dans les branches sont exécutées de façon entrelacée, et lors de l’exécution de chaque activité enfant, la couleur de console correcte est appliquée par `ConsoleColorProperty`.</span><span class="sxs-lookup"><span data-stu-id="9eac3-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="9eac3-122">Lorsque le workflow est appelé, la sortie suivante est écrite dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="9eac3-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> <span data-ttu-id="9eac3-123">Bien que cela ne soit pas visible dans la sortie précédente, chaque ligne de texte contenue dans la fenêtre de console est affichée dans la couleur indiquée.</span><span class="sxs-lookup"><span data-stu-id="9eac3-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="9eac3-124">Les propriétés d'exécution de workflow peuvent être utilisées par les auteurs d'activités personnalisées, tout en fournissant également le mécanisme nécessaire pour gérer les activités telles que les activités <xref:System.ServiceModel.Activities.CorrelationScope> et <xref:System.Activities.Statements.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="9eac3-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eac3-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9eac3-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
