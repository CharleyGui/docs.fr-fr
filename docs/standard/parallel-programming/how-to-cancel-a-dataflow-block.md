---
title: 'Comment : annuler un bloc de flux de données'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
ms.openlocfilehash: aa175d95f27fcbf28c3f3da3eaa7b8f7988681e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140092"
---
# <a name="how-to-cancel-a-dataflow-block"></a>Comment : annuler un bloc de flux de données
Ce document montre comment activer l’annulation dans votre application. Cet exemple utilise des Windows Forms pour montrer où les éléments de travail sont actifs dans un pipeline de flux de données, ainsi que les effets de l’annulation.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a>Pour créer une Application Windows Forms  
  
1. Créez un projet C# ou **Application Windows Forms** Visual Basic. Dans les étapes suivantes, le projet est nommé `CancellationWinForms`.  
  
2. Dans le concepteur de formulaires pour le formulaire principal, Form1.cs (Form1.vb pour Visual Basic), ajoutez un contrôle <xref:System.Windows.Forms.ToolStrip>.  
  
3. Ajoutez un contrôle <xref:System.Windows.Forms.ToolStripButton> au contrôle <xref:System.Windows.Forms.ToolStrip>. Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> sur <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> et la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur **Ajouter des éléments de travail**.  
  
4. Ajoutez un deuxième contrôle <xref:System.Windows.Forms.ToolStripButton> au contrôle <xref:System.Windows.Forms.ToolStrip>. Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> sur <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur **Annuler** et la propriété <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> sur `False`.  
  
5. Ajoutez quatre objets <xref:System.Windows.Forms.ToolStripProgressBar> au contrôle <xref:System.Windows.Forms.ToolStrip>.  
  
## <a name="creating-the-dataflow-pipeline"></a>Création du pipeline de flux de données  
 Cette section décrit comment créer le pipeline de flux de données qui traite les éléments de travail et met à jour les barres de progression.  
  
### <a name="to-create-the-dataflow-pipeline"></a>Pour créer le pipeline de flux de données  
  
1. Dans votre projet, ajoutez une référence à System.Threading.Tasks.Dataflow.dll.  
  
2. Vérifiez que Form1.cs (Form1.vb pour Visual Basic) contient les instructions `using` suivantes (`Imports` en Visual Basic).  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. Ajouter la classe `WorkItem` comme un type interne de la classe `Form1`.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. Ajoutez les membres de données suivants à la classe `Form1`.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. Ajoutez la méthode suivante, `CreatePipeline`, à la classe `Form1`.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 Étant donné que les blocs de flux de données `incrementProgress` et `decrementProgress` agissent sur l’interface utilisateur, il est important que ces actions se produisent sur le thread de l’interface utilisateur. Pour cela, lors de la construction, chacun de ces objets fournit un objet <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> dont la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> est définie sur <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. La méthode <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> crée un objet <xref:System.Threading.Tasks.TaskScheduler> qui effectue le travail dans le contexte actuel de synchronisation. Étant donné que le constructeur `Form1` est appelé depuis le thread de l’interface utilisateur, les actions des blocs de flux de données `incrementProgress` et `decrementProgress` fonctionnent aussi sur le thread de l’interface utilisateur.  
  
 Cet exemple définit la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> lors de la construction des membres du pipeline. Étant donné que la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> annule définitivement l’exécution du bloc de flux de données, l’ensemble du pipeline doit être recréé si l’utilisateur annule l’opération et souhaite par la suite ajouter d’autres éléments de travail au pipeline. Pour obtenir un exemple illustrant une autre méthode d’annulation d’un bloc de flux de données de sorte que les autres travaux puissent être effectués après l’annulation d’une opération, consultez [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md) (Procédure pas à pas : utilisation d’un flux de données dans une application Windows Forms).  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a>Connexion du pipeline de flux de données à l’interface utilisateur  
 Cette section décrit comment connecter le pipeline de flux de données à l’interface utilisateur. La création du pipeline et l’ajout d’éléments de travail au pipeline sont contrôlés par le gestionnaire d’événements pour le bouton **Add Work Items** (Ajouter des éléments de travail). L’annulation est lancée par le bouton **Annuler**. Lorsque l’utilisateur clique sur un de ces boutons, l’action appropriée est lancée de manière asynchrone.  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a>Pour connecter le pipeline de flux de données à l’interface utilisateur  
  
1. Dans le concepteur de formulaires du formulaire principal, créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolStripItem.Click> du bouton **Ajouter des éléments de travail**.  
  
2. Implémentez l’événement <xref:System.Windows.Forms.ToolStripItem.Click> pour le bouton **Ajouter des éléments de travail**.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. Dans le concepteur de formulaires du formulaire principal, créez un gestionnaire d'événements pour le gestionnaire d’événements <xref:System.Windows.Forms.ToolStripItem.Click> du bouton **Annuler**.  
  
4. Implémentez le gestionnaire d’événements <xref:System.Windows.Forms.ToolStripItem.Click> pour le bouton **Annuler**.  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre le code complet pour Form1.cs (Form1.vb pour Visual Basic).  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 L'illustration suivante présente l'application en cours d'exécution.  
  
 ![Application Windows Forms](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")  

## <a name="see-also"></a>Voir aussi

- [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
