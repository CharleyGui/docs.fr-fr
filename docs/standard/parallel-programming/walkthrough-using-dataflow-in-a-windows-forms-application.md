---
title: 'Procédure pas à pas : utilisation d’un dataflow dans une application Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- TPL dataflow library, in Windows Forms
- Task Parallel Library, dataflows
- Windows Forms, and TPL
ms.assetid: 9c65cdf7-660c-409f-89ea-59d7ec8e127c
ms.openlocfilehash: c09259afdc5ede32791ba895ca012cdc2a0a1c18
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829945"
---
# <a name="walkthrough-using-dataflow-in-a-windows-forms-application"></a>Procédure pas à pas : utilisation d’un dataflow dans une application Windows Forms
Ce document montre comment créer un réseau de blocs de flux de données qui effectuent un traitement des images dans une application Windows Forms.  
  
 Dans cet exemple, on charge des fichiers image à partir du dossier spécifié, on crée une image composite, et on affiche le résultat. L’exemple utilise le modèle de flux de données pour acheminer les images via le réseau. Dans le modèle de flux de données, les composants indépendants d’un programme communiquent entre eux en envoyant des messages. Lorsqu’un composant reçoit un message, il effectue une action, puis transmet le résultat à un autre composant. Comparez cela avec le modèle de flux de contrôle, dans lequel une application utilise des structures de contrôle (par exemple, des instructions conditionnelles, des boucles, etc.) pour contrôler l’ordre des opérations dans un programme.  
  
## <a name="prerequisites"></a>Prérequis  
 Lisez la rubrique [Flux de données](dataflow-task-parallel-library.md) avant de démarrer cette procédure pas à pas.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="sections"></a>Sections  
 Cette procédure pas à pas contient les sections suivantes :  
  
- [Création de l’application Windows Forms](#winforms)  
  
- [Création du réseau de flux de données](#network)  
  
- [Connexion du réseau de flux de données à l’interface utilisateur](#ui)  
  
- [Exemple complet](#complete)  
  
<a name="winforms"></a>
## <a name="creating-the-windows-forms-application"></a>Création de l’application Windows Forms  
 Cette section décrit comment créer l’application Windows Forms de base et ajouter des contrôles au formulaire principal.  
  
### <a name="to-create-the-windows-forms-application"></a>Pour créer une Application Windows Forms  
  
1. Dans Visual Studio, créez un projet **Application Windows Forms** en Visual C# ou en Visual Basic. Dans ce document, le projet est nommé `CompositeImages`.  
  
2. Dans le concepteur de formulaires pour le formulaire principal, Form1.cs (Form1.vb pour Visual Basic), ajoutez un contrôle <xref:System.Windows.Forms.ToolStrip>.  
  
3. Ajoutez un contrôle <xref:System.Windows.Forms.ToolStripButton> au contrôle <xref:System.Windows.Forms.ToolStrip>. Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> sur <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> et la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur **Choisir un dossier**.  
  
4. Ajoutez un deuxième contrôle <xref:System.Windows.Forms.ToolStripButton> au contrôle <xref:System.Windows.Forms.ToolStrip>. Définissez la propriété <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> sur <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, la propriété <xref:System.Windows.Forms.ToolStripItem.Text%2A> sur **Annuler** et la propriété <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> sur `False`.  
  
5. Ajoutez un objet <xref:System.Windows.Forms.PictureBox> au formulaire principal. Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.  
  
<a name="network"></a>
## <a name="creating-the-dataflow-network"></a>Création du réseau de flux de données  
 Cette section décrit comment créer le réseau de flux de données qui effectue le traitement des images.  
  
### <a name="to-create-the-dataflow-network"></a>Pour créer le réseau de flux de données  
  
1. Dans votre projet, ajoutez une référence à System.Threading.Tasks.Dataflow.dll.  
  
2. Vérifiez que Form1.cs (Form1.vb pour Visual Basic) contient les instructions `using` suivantes (`Using`en Visual Basic) :  
  
     [!code-csharp[TPLDataflow_CompositeImages#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#1)]  
  
3. Ajoutez les membres de données suivants à la classe `Form1` :  
  
     [!code-csharp[TPLDataflow_CompositeImages#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#2)]  
  
4. Ajoutez la méthode suivante, `CreateImageProcessingNetwork`, à la classe `Form1`. Cette méthode crée le réseau de traitement des images.  
  
     [!code-csharp[TPLDataflow_CompositeImages#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#3)]  
  
5. Implémentez la méthode `LoadBitmaps`.  
  
     [!code-csharp[TPLDataflow_CompositeImages#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#4)]  
  
6. Implémentez la méthode `CreateCompositeBitmap`.  
  
     [!code-csharp[TPLDataflow_CompositeImages#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#5)]  
  
    > [!NOTE]
    > La version C# de la méthode `CreateCompositeBitmap` utilise des pointeurs pour permettre un traitement efficace des objets <xref:System.Drawing.Bitmap?displayProperty=nameWithType>. Par conséquent, vous devez activer l’option **Autoriser les blocs de code unsafe** dans votre projet pour pouvoir utiliser le mot-clé [unsafe](../../csharp/language-reference/keywords/unsafe.md). Pour plus d’informations sur l’activation de code unsafe dans un projet Visual C#, consultez [Générer, page du Concepteur de projets (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
 Le tableau ci-dessous décrit les membres du réseau.  
  
|Membre|Type|Description|  
|------------|----------|-----------------|  
|`loadBitmaps`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Prend un chemin d’accès à un dossier en entrée, et produit une collection d’objets <xref:System.Drawing.Bitmap> en sortie.|  
|`createCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Prend une collection d’objets <xref:System.Drawing.Bitmap> en entrée, et produit une bitmap composite en sortie.|  
|`displayCompositeBitmap`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Affiche l’image bitmap composite sur le formulaire.|  
|`operationCancelled`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Affiche une image pour indiquer que l’opération est annulée et permet à l’utilisateur de sélectionner un autre dossier.|  
  
 Pour connecter les blocs de flux de données afin de former un réseau, cet exemple utilise la méthode <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A>. <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> Celle-ci contient une version surchargée qui prend un objet <xref:System.Predicate%601> définissant si le bloc cible accepte ou rejette un message. Ce mécanisme de filtrage permet aux blocs de messages de ne recevoir que certaines valeurs. Dans cet exemple, le réseau peut créer une branche de deux manières. La branche principale charge les images à partir du disque, crée l’image composite et affiche cette image sur le formulaire. L’autre branche annule l’opération en cours. Les objets <xref:System.Predicate%601> permettent aux blocs de flux de données de la branche principale de basculer vers l’autre branche en rejetant certains messages. Par exemple, si l’utilisateur annule l’opération, le bloc de flux de données `createCompositeBitmap` produit `null` (`Nothing` en Visual Basic) comme sortie. Le bloc de flux de données `displayCompositeBitmap` rejette les valeurs d’entrée `null`. Par conséquent, le message est proposé aux `operationCancelled`. Le bloc de flux de données `operationCancelled` accepte tous les messages. Par conséquent, il affiche une image pour indiquer que l’opération est annulée.  
  
 L’illustration suivante montre le réseau de traitement des images :  
  
 ![Illustration qui montre le réseau de traitement des images.](./media/walkthrough-using-dataflow-in-a-windows-forms-application/dataflow-winforms-image-processing.png)  
  
 Étant donné que les blocs de flux de données `displayCompositeBitmap` et `operationCancelled` agissent sur l’interface utilisateur, il est important que ces actions se produisent sur le thread de l’interface utilisateur. Pour cela, lors de la construction, chacun de ces objets fournit un objet <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> dont la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> est définie sur <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>. La méthode <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> crée un objet <xref:System.Threading.Tasks.TaskScheduler> qui effectue le travail dans le contexte actuel de synchronisation. Étant donné que la méthode `CreateImageProcessingNetwork` est appelée à partir du gestionnaire du bouton **Choisir le dossier**, qui est exécuté sur le thread de l’interface utilisateur, les actions des blocs de flux de données `displayCompositeBitmap` et `operationCancelled` sont également exécutées sur le thread de l’interface utilisateur.  
  
 Cet exemple utilise un jeton d’annulation partagé au lieu de définir la propriété <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>, car cette dernière annule définitivement l’exécution du bloc de flux de données<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>. Cet exemple explique comment un jeton d’annulation permet de réutiliser un réseau de flux de données plusieurs fois, même lorsque l’utilisateur annule une ou plusieurs opérations. Vous trouverez un exemple utilisant <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> pour annuler définitivement l’exécution d’un bloc de flux de données sur la page [Guide pratique : annuler un bloc de flux de données](how-to-cancel-a-dataflow-block.md).  
  
<a name="ui"></a>
## <a name="connecting-the-dataflow-network-to-the-user-interface"></a>Connexion du réseau de flux de données à l’interface utilisateur  
 Cette section décrit comment connecter le réseau de flux de données à l’interface utilisateur. La création de l’image composite et l’annulation de l’opération sont lancées à partir des boutons **Choisir le dossier** et **Annuler**. Lorsque l’utilisateur clique sur l’un de ces boutons, l’action appropriée est lancée de manière asynchrone.  
  
### <a name="to-connect-the-dataflow-network-to-the-user-interface"></a>Connecter le réseau de flux de données à l’interface utilisateur  
  
1. Dans le concepteur de formulaires du formulaire principal, créez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.ToolStripItem.Click> du bouton **Annuler**.  
  
2. Implémentez l’événement <xref:System.Windows.Forms.ToolStripItem.Click> pour le bouton **Choisir un dossier**.  
  
     [!code-csharp[TPLDataflow_CompositeImages#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#6)]  
  
3. Dans le concepteur de formulaires du formulaire principal, créez un gestionnaire d'événements pour l’événement <xref:System.Windows.Forms.ToolStripItem.Click> du bouton **Annuler**.  
  
4. Implémentez l’événement <xref:System.Windows.Forms.ToolStripItem.Click> pour le bouton **Annuler**.  
  
     [!code-csharp[TPLDataflow_CompositeImages#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#7)]  
  
<a name="complete"></a>
## <a name="the-complete-example"></a>Exemple complet  
 L'exemple suivant présente le code complet pour cette visite.  
  
 [!code-csharp[TPLDataflow_CompositeImages#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_compositeimages/cs/compositeimages/form1.cs#100)]  
  
 L’illustration suivante montre une sortie type du dossier \Échantillons d'images\.  
  
 ![Application Windows Forms](media/tpldataflow-compositeimages.gif "TPLDataflow_CompositeImages")  

## <a name="see-also"></a>Voir aussi

- [Dataflow](dataflow-task-parallel-library.md)
