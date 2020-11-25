---
title: 'Procédure : spécifier un planificateur de tâches dans un bloc de dataflow'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
ms.openlocfilehash: b8c27c1ca61356b36183bb74b8360e41f5324d25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722438"
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a>Procédure : spécifier un planificateur de tâches dans un bloc de dataflow

Ce document montre comment associer un planificateur de tâches spécifique lorsque vous utilisez le flux de données dans votre application. L’exemple utilise la classe <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> dans une application Windows Forms pour indiquer lorsque les tâches de lecture sont actives et lorsqu’une tâche d’écriture est active. Il utilise également la méthode <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> pour permettre à un bloc de flux de données de s'exécuter sur le thread de l'interface utilisateur.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="to-create-the-windows-forms-application"></a>Pour créer une Application Windows Forms  
  
1. Créez un projet **Application Windows Forms** en Visual C# ou Visual Basic. Dans les étapes suivantes, le projet est nommé `WriterReadersWinForms`.  
  
2. Dans le concepteur de formulaires pour le formulaire principal, Form1.cs (Form1.vb pour Visual Basic), ajoutez quatre contrôles <xref:System.Windows.Forms.CheckBox>. Définissez la propriété <xref:System.Windows.Forms.Control.Text%2A> sur **Lecteur 1** pour `checkBox1`, **Lecteur 2** pour `checkBox2`, **Lecteur 3** pour `checkBox3`, et **Enregistreur** pour `checkBox4`. Définissez la propriété <xref:System.Windows.Forms.Control.Enabled%2A> pour chaque contrôle sur `False`.  
  
3. Ajoutez un contrôle <xref:System.Windows.Forms.Timer> au formulaire. Affectez à la propriété <xref:System.Windows.Forms.Timer.Interval%2A> la valeur `2500`.  
  
## <a name="adding-dataflow-functionality"></a>Ajout de fonctionnalités de flux de données  

 Cette section décrit comment créer des blocs de flux de données participant à l'application et comment associer chacun d'entre eux à un planificateur de tâches.  
  
### <a name="to-add-dataflow-functionality-to-the-application"></a>Pour ajouter des fonctionnalités de flux de données à l'application  
  
1. Dans votre projet, ajoutez une référence à System.Threading.Tasks.Dataflow.dll.  
  
2. Vérifiez que Form1.cs (Form1.vb pour Visual Basic) contient les instructions `using` suivantes (`Imports` en Visual Basic).  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3. Ajoutez des données membre <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> à la classe `Form1`.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4. Dans le constructeur `Form1`, après l'appel à `InitializeComponent`, créez un objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> qui fait basculer l'état des objets <xref:System.Windows.Forms.CheckBox>.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5. Dans le constructeur `Form1`, créez un objet <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> et quatre objets <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, un objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> pour chaque objet <xref:System.Windows.Forms.CheckBox>. Pour chaque objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, spécifiez un objet <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> qui contient le jeu de propriétés <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> affectées à la propriété <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> pour les lecteurs, la propriété <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> pour l'enregistreur.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6. Dans le constructeur `Form1`, démarrez l'objet <xref:System.Windows.Forms.Timer>.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7. Dans le concepteur de formulaires pour le formulaire principal, créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.Timer.Tick> pour la minuterie.  
  
8. Implémentez l'événement <xref:System.Windows.Forms.Timer.Tick> pour la minuterie.  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 Étant donné que le bloc de flux de données `toggleCheckBox` agit sur l'interface utilisateur, il est important que cette action se produisent sur le thread de l'interface utilisateur. Pour ce faire, lors de la construction, cet objet est un objet <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> qui contient la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> définie sur <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. La méthode <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> crée un objet <xref:System.Threading.Tasks.TaskScheduler> qui effectue le travail dans le contexte actuel de synchronisation. Étant donné que le constructeur `Form1` est appelé depuis le thread de l'interface utilisateur, l'action du bloc de flux de données `toggleCheckBox` fonctionne aussi sur le thread de l'interface utilisateur.  
  
 Cet exemple utilise également une classe <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> pour permettre à des blocs de flux de données d'agir simultanément, et à un autre bloc de flux de données d'agir de façon exclusive par rapport à tous les autres blocs de flux de données qui s'exécutent sur le même objet <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair>. Cette technique est utile lorsque plusieurs blocs de flux de données partagent une ressource et que certains requièrent un accès exclusif à cette ressource, car elle élimine le besoin de synchroniser manuellement l'accès à cette ressource. L'élimination de la synchronisation manuelle peut rendre le code plus efficace.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre le code complet pour Form1.cs (Form1.vb pour Visual Basic).  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a>Voir aussi

- [Dataflow](dataflow-task-parallel-library.md)
