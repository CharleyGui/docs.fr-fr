---
title: Utilisation de délégués d'activité
ms.date: 03/30/2017
ms.assetid: e33cf876-8979-440b-9b23-4a12d1139960
ms.openlocfilehash: 66a03187336475ed377fda032506cfa66d3daf58
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293297"
---
# <a name="using-activity-delegates"></a>Utilisation de délégués d'activité

Les délégués d'activité permettent aux auteurs d'activités d'exposer des rappels avec des signatures spécifiques pour lesquelles les utilisateurs de l'activité peuvent fournir des gestionnaires basés sur l'activité. Deux types de délégués d'activité sont disponibles : <xref:System.Activities.ActivityAction%601> est utilisé pour définir des délégués d'activité qui n'ont pas de valeur de retour et <xref:System.Activities.ActivityFunc%601> est utilisé pour définir des délégués d'activité qui ont une valeur de retour.

Les délégués d'activité sont utiles dans les scénarios où une activité enfant doit être limitée à une certaine signature. Par exemple, une activité <xref:System.Activities.Statements.While> peut contenir tout type d’activité enfant sans contraintes, mais le corps d’une activité <xref:System.Activities.Statements.ForEach%601> est un <xref:System.Activities.ActivityAction%601>, et l’activité enfant exécutée finalement par <xref:System.Activities.Statements.ForEach%601> doit avoir un <xref:System.Activities.InArgument%601> qui est du même type que les membres de la collection que le <xref:System.Activities.Statements.ForEach%601> énumère.

## <a name="using-activityaction"></a>Utilisation d'ActivityAction

Plusieurs activités [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] utilisent des actions de l'activité, telles que l'activité <xref:System.Activities.Statements.Catch> et l'activité <xref:System.Activities.Statements.ForEach%601>. Dans chaque cas, l'action de l'activité représente un emplacement où l'auteur de workflow spécifie une activité pour fournir le comportement voulu lors de la composition d'un workflow à l'aide de l'une de ces activités. Dans l'exemple suivant, une activité <xref:System.Activities.Statements.ForEach%601> est utilisée pour afficher un texte dans la fenêtre de console. Le corps du <xref:System.Activities.Statements.ForEach%601> est spécifié à l'aide d'un <xref:System.Activities.ActivityAction%601> qui correspond au type du <xref:System.Activities.Statements.ForEach%601> qui est le type chaîne. L’activité <xref:System.Activities.Statements.WriteLine> spécifiée dans le <xref:System.Activities.ActivityDelegate.Handler%2A> a son argument <xref:System.Activities.Statements.WriteLine.Text%2A> lié aux valeurs de chaîne dans la collection au sein de laquelle l’activité <xref:System.Activities.Statements.ForEach%601> itère.

[!code-csharp[CFX_ActivityExample#6](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#6)]

L'actionArgument est utilisé pour transférer les éléments individuels dans la collection au WriteLine. Lorsque le workflow est appelé, la sortie suivante s'affiche sur la console.

```console
HelloWorld.
```

Les exemples de cette rubrique utilisent la syntaxe d'initialisation d'objet. La syntaxe d'initialisation d'objet peut être une méthode utile pour créer des définitions de workflow dans le code, car elle fournit une vue hiérarchique des activités dans le workflow et affiche la relation entre les activités. Il n'est pas impératif d'utiliser la syntaxe d'initialisation d'objet lorsque vous créez des workflows par programmation. L'exemple suivant est d'un point de vue fonctionnel équivalent à l'exemple précédent :

[!code-csharp[CFX_ActivityExample#7](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#7)]

Pour plus d’informations sur les initialiseurs d’objets, consultez [Comment : initialiser des objets sans appeler de constructeur (Guide de programmation C#)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) et [Comment : déclarer un objet à l’aide d’un initialiseur d’objet (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md).

Dans l'exemple suivant, une activité <xref:System.Activities.Statements.TryCatch> est utilisée dans un workflow. Un <xref:System.ApplicationException> est levé par le workflow et géré par une activité <xref:System.Activities.Statements.Catch%601>. Le gestionnaire de l' <xref:System.Activities.Statements.Catch%601> action d’activité de l’activité est une <xref:System.Activities.Statements.WriteLine> activité, et le détail de l’exception est transmis à celui-ci à l’aide de `ex` <xref:System.Activities.DelegateInArgument%601> .

[!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]

Lorsque vous créez une activité personnalisée qui définit un <xref:System.Activities.ActivityAction%601>, utilisez un <xref:System.Activities.Statements.InvokeAction%601> pour modéliser l'appel de ce <xref:System.Activities.ActivityAction%601>. Dans cet exemple, une activité `WriteLineWithNotification` personnalisée est définie. Cette activité est composée d'un <xref:System.Activities.Statements.Sequence> qui contient une activité <xref:System.Activities.Statements.WriteLine> suivie d'un <xref:System.Activities.Statements.InvokeAction%601> qui appelle un <xref:System.Activities.ActivityAction%601> qui prend un argument de chaîne.

[!code-csharp[CFX_ActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#1)]

Lorsqu'un workflow est créé à l'aide de l'activité `WriteLineWithNotification`, l'auteur de workflow spécifie la logique personnalisée voulue dans le <xref:System.Activities.ActivityDelegate.Handler%2A> de l'action de l'activité. Dans cet exemple, un workflow qui utilise l'activité `WriteLineWithNotification` est créé et une activité <xref:System.Activities.Statements.WriteLine> est utilisée comme <xref:System.Activities.ActivityDelegate.Handler%2A>.

[!code-csharp[CFX_ActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#2)]

Il existe plusieurs versions génériques de <xref:System.Activities.Statements.InvokeAction%601> et <xref:System.Activities.ActivityAction%601> fournies pour le passage d’un ou de plusieurs arguments.

## <a name="using-activityfunc"></a>Utilisation d'ActivityFunc

<xref:System.Activities.ActivityAction%601> est utile en l'absence de valeur de résultat de l'activité et <xref:System.Activities.ActivityFunc%601> est utilisé lorsqu'une valeur de résultat est retournée. Lorsque vous créez une activité personnalisée qui définit un <xref:System.Activities.ActivityFunc%601>, utilisez un <xref:System.Activities.Expressions.InvokeFunc%601> pour modéliser l'appel de ce <xref:System.Activities.ActivityFunc%601>. Dans l'exemple suivant, une activité `WriteFillerText` est définie. Pour fournir le texte de remplissage, un <xref:System.Activities.Expressions.InvokeFunc%601> qui prend un argument entier et a un résultat de chaîne est spécifié. Une fois le texte de remplissage récupéré, il est affiché sur la console à l'aide d'une activité <xref:System.Activities.Statements.WriteLine>.

[!code-csharp[CFX_ActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#3)]

Pour fournir le texte, une activité qui prend un argument `int` et a un résultat de chaîne doit être utilisée. Cet exemple montre une activité `TextGenerator` qui répond à ces critères.

[!code-csharp[CFX_ActivityExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#4)]

Pour utiliser l'activité `TextGenerator` avec l'activité `WriteFillerText`, spécifiez-la en tant que <xref:System.Activities.ActivityDelegate.Handler%2A>.

[!code-csharp[CFX_ActivityExample#5](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_ActivityExample/cs/Program.cs#5)]
