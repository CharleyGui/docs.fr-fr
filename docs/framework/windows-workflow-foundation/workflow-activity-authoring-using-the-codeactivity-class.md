---
title: Création de l'activité de workflow à l'aide de la classe CodeActivity
ms.date: 03/30/2017
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
ms.openlocfilehash: 714e0971a006db20d002b0f3a486533b1357fba7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293817"
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>Création de l'activité de workflow à l'aide de la classe CodeActivity

Les activités créées en héritant de <xref:System.Activities.CodeActivity> peuvent implémenter un comportement impératif de base en remplaçant la méthode <xref:System.Activities.CodeActivity.Execute%2A>.

## <a name="using-codeactivitycontext"></a>Utilisation de CodeActivityContext

 Les fonctionnalités de l'exécution du workflow sont accessibles à partir de la méthode <xref:System.Activities.CodeActivity.Execute%2A> en utilisant les membres du paramètre `context`, de type <xref:System.Activities.CodeActivityContext>. Les fonctionnalités disponibles via <xref:System.Activities.CodeActivityContext> sont notamment :

- Obtention et définition des valeurs de variables et d’arguments.

- Fonctionnalités de suivi personnalisées à l'aide de <xref:System.Activities.CodeActivityContext.Track%2A>.

- Accès aux propriétés d'exécution de l'activité à l'aide de <xref:System.Activities.CodeActivityContext.GetProperty%2A>.

#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>Pour créer une activité personnalisée qui hérite de CodeActivity

1. Ouvrez Visual Studio 2010.

2. Sélectionnez **fichier**, **nouveau**, puis **projet**. Sélectionnez **Workflow 4,0** sous **Visual C#** dans la fenêtre **types de projets** , puis sélectionnez le nœud **v2010** . Sélectionnez **bibliothèque d’activités** dans la fenêtre **modèles** . Nommez le nouveau projet HelloActivity.

3. Cliquez avec le bouton droit sur Activity1. xaml dans le projet HelloActivity, puis sélectionnez **supprimer**.

4. Cliquez avec le bouton droit sur le projet HelloActivity et sélectionnez **Ajouter** , puis **classe**. Nommez la nouvelle classe HelloActivity.cs.

5. Dans le fichier HelloActivity.cs, ajoutez les directives `using` suivantes.

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. Faites en sorte que la nouvelle classe hérite de <xref:System.Activities.CodeActivity> en ajoutant une classe de base à la déclaration de classe.

    ```csharp
    class HelloActivity : CodeActivity
    ```

7. Ajoutez des fonctionnalités à la classe en ajoutant une méthode <xref:System.Activities.CodeActivity.Execute%2A>.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. Utilisez le <xref:System.Activities.CodeActivityContext> pour créer un enregistrement de suivi.

    ```csharp
    protected override void Execute(CodeActivityContext context)
    {
        Console.WriteLine("Hello World!");
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));
        context.Track(record);
    }
    ```
