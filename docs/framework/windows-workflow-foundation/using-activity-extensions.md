---
title: Utilisation d'extensions d'activité
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 3a9cabda9fe92b2ea4e708da8f853f3029328775
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293284"
---
# <a name="using-activity-extensions"></a>Utilisation d'extensions d'activité

Les activités peuvent interagir avec les extensions d’application de workflow qui permettent à l’hôte de fournir des fonctionnalités supplémentaires qui ne sont pas explicitement modélisées dans le workflow.  Cette rubrique explique comment créer et utiliser une extension pour compter le nombre de fois où l'activité s'exécute.

### <a name="to-use-an-activity-extension-to-count-executions"></a>Pour utiliser une extension d’activité pour compter les exécutions

1. Ouvrez Visual Studio 2010. Sélectionnez **nouveau**, **projet**. Sous le nœud **Visual C#** , sélectionnez **Workflow**.  Dans la liste des modèles, sélectionnez **application console de workflow** . Nommez le projet `Extensions`. Cliquez sur **OK** pour créer le projet.

2. Ajoutez une `using` instruction dans le fichier Program.cs pour l’espace de noms **System. Collections. Generic** .

    ```csharp
    using System.Collections.Generic;
    ```

3. Dans le fichier Program.cs, créez une nouvelle classe nommée **ExecutionCountExtension**. Le code suivant crée une extension de workflow qui suit les ID d’instance lorsque sa méthode **Register** est appelée.

    ```csharp
    // This extension collects a list of workflow Ids
    public class ExecutionCountExtension
    {
        IList<Guid> instances = new List<Guid>();

        public int ExecutionCount
        {
            get
            {
                return this.instances.Count;
            }
        }

        public IEnumerable<Guid> InstanceIds
        {
            get
            {
                return this.instances;
            }
        }

        public void Register(Guid activityInstanceId)
        {
            if (!this.instances.Contains<Guid>(activityInstanceId))
            {
                instances.Add(activityInstanceId);
            }
        }
    }
    ```

4. Créez une activité qui consomme **ExecutionCountExtension**. Le code suivant définit une activité qui récupère l’objet **ExecutionCountExtension** à partir du runtime et appelle sa méthode **Register** lorsque l’activité s’exécute.

    ```csharp
    // Activity that consumes an extension provided by the host. If the extension is available
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)
    public class MyActivity: CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();
            if (ext != null)
            {
                ext.Register(context.WorkflowInstanceId);
            }

        }
    }
    ```

5. Implémentez l’activité dans la méthode **main** du fichier Program.cs. Le code suivant contient les méthodes pour générer deux workflows distincts, exécuter plusieurs fois chaque workflow et afficher les données résultantes contenues dans l’extension.

    ```csharp
    class Program
    {
        // Creates a workflow that uses the activity that consumes the extension
        static Activity CreateWorkflow1()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity()
                }
            };
        }

        // Creates a workflow that uses two instances of the activity that consumes the extension
        static Activity CreateWorkflow2()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity(),
                    new MyActivity()
                }
            };
        }

        static void Main(string[] args)
        {
            // create the extension
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();

            // configure the first invoker and execute 3 times
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());
            invoker.Extensions.Add(executionCountExt);
            invoker.Invoke();
            invoker.Invoke();
            invoker.Invoke();

            // configure the second invoker and execute 2 times
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());
            invoker2.Extensions.Add(executionCountExt);
            invoker2.Invoke();
            invoker2.Invoke();

            // show the data in the extension
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));
        }
    }
    ```
