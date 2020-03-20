---
title: Propriétés d'exécution de workflow
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 0f958e7e112bfddc2740c2605d446493f2d49010
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182660"
---
# <a name="workflow-execution-properties"></a>Propriétés d'exécution de workflow
Par le biais du stockage local des threads (TLS), le CLR maintient un contexte d’exécution pour chaque thread. Ce contexte d’exécution gouverne des propriétés de thread connues, telles que l’identité de thread, la transaction ambiante et le jeu d’autorisations actuel, en plus des propriétés de thread définies par l’utilisateur (comme les emplacements nommés).  
  
 Contrairement aux programmes qui ciblent directement le CLR, les programmes de workflow sont hiérarchiquement des arborescences de portée d'activités qui s'exécutent dans un environnement de thread agnostique. Cela implique que les mécanismes de TLS standard ne peuvent pas être utilisés directement pour déterminer quel contexte se trouve dans la portée d’un élément de travail donné. Par exemple, deux branches parallèles d'exécution peuvent utiliser des transactions différentes, mais le planificateur peut entrelacer leur exécution sur le même thread de CLR.  
  
 Les propriétés d'exécution de workflow fournissent un mécanisme permettant d'ajouter des propriétés spécifiques au contexte à l'environnement d'une activité. Ainsi, une activité peut déclarer les propriétés incluses dans la portée pour la sous-arborescence associée, tout en fournissant des connexions pour la configuration et la destruction de TLS afin d’interagir correctement avec les objets CLR.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Création et utilisation de propriétés d'exécution de workflow  
 Les propriétés d'exécution du workflow implémentent généralement l'interface <xref:System.Activities.IExecutionProperty>, même si les propriétés axées sur la messagerie peuvent implémenter <xref:System.ServiceModel.Activities.ISendMessageCallback> et <xref:System.ServiceModel.Activities.IReceiveMessageCallback> à la place. Pour créer une propriété d'exécution de workflow, créez une classe qui implémente l'interface <xref:System.Activities.IExecutionProperty> et qui implémente les membres <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> et <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Ces membres fournissent à la propriété d'exécution la possibilité de configurer et détruire correctement le stockage local des threads lors de chaque impulsion de travail de l'activité qui contient la propriété, y compris ses activités enfants. Dans cet exemple, `ConsoleColorProperty` est créé afin de définir `Console.ForegroundColor`.  
  
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
  
 Les auteurs d'activité peuvent utiliser cette propriété en l'inscrivant dans la substitution d'exécution de l'activité. Dans cet exemple, une activité `ConsoleColorScope` est définie afin d'inscrire `ConsoleColorProperty` en l'ajoutant à la collection <xref:System.Activities.NativeActivityContext.Properties%2A> du contexte <xref:System.Activities.NativeActivityContext> actuel.  
  
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
  
 Lorsque le corps de l'activité commence une impulsion de travail, la méthode <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> de la propriété est appelée, et quand l'impulsion de travail est terminée, la méthode <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> est appelée. Dans cet exemple, un workflow est créé afin d’utiliser une activité <xref:System.Activities.Statements.Parallel> avec trois branches. Les deux premières branches utilisent l'activité `ConsoleColorScope`, contrairement à la troisième branche. Les trois branches contiennent deux activités <xref:System.Activities.Statements.WriteLine> et une activité <xref:System.Activities.Statements.Delay>. Lorsque l’activité <xref:System.Activities.Statements.Parallel> est exécutée, les activités contenues dans les branches sont exécutées de façon entrelacée, et lors de l’exécution de chaque activité enfant, la couleur de console correcte est appliquée par `ConsoleColorProperty`.  
  
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
  
 Lorsque le workflow est appelé, la sortie suivante est écrite dans la fenêtre de console.  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> Bien que cela ne soit pas visible dans la sortie précédente, chaque ligne de texte contenue dans la fenêtre de console est affichée dans la couleur indiquée.  
  
 Les propriétés d'exécution de workflow peuvent être utilisées par les auteurs d'activités personnalisées, tout en fournissant également le mécanisme nécessaire pour gérer les activités telles que les activités <xref:System.ServiceModel.Activities.CorrelationScope> et <xref:System.Activities.Statements.TransactionScope>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
