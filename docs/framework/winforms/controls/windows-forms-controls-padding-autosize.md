---
title: 'Procédure pas à pas : disposition des contrôles Windows Forms avec le remplissage, les marges et la propriété AutoSize'
ms.date: 03/30/2017
f1_keywords:
- Margin.Bottom
- Margin.Left
- Margin.Top
- Margin.All
- Margin.Right
helpviewer_keywords:
- Margin property [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], layout
- AutoSize property [Windows Forms], walkthroughs
- Padding property [Windows Forms], walkthroughs
- layout [Windows Forms], margins and padding
- Windows Forms, layout
ms.assetid: f8ae2a6b-db13-4630-8e25-d104091205c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: daf0c6495b89033e75c27a1ff0cbceaff9d85f34
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987164"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>Procédure pas à pas : Disposer les contrôles avec le remplissage, les marges et la propriété AutoSize

Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications. La **Concepteur Windows Forms** dans Visual Studio vous donne de nombreux outils de mise en page pour y parvenir. Trois des plus importantes sont les <xref:System.Windows.Forms.Control.Margin%2A>propriétés, <xref:System.Windows.Forms.Control.Padding%2A>et <xref:System.Windows.Forms.Control.AutoSize%2A> , qui sont présentes sur tous les contrôles Windows Forms.

La propriété <xref:System.Windows.Forms.Control.Margin%2A> définit l'espace autour du contrôle qui maintient les autres contrôles à une distance spécifiée des bordures du contrôle.

La propriété <xref:System.Windows.Forms.Control.Padding%2A> définit l'espace à l'intérieur d'un contrôle qui maintient le contenu du contrôle (par exemple la valeur de sa propriété <xref:System.Windows.Forms.Control.Text%2A>) à une distance spécifiée des bordures du contrôle.

L'illustration suivante montre les propriétés <xref:System.Windows.Forms.Control.Padding%2A> et <xref:System.Windows.Forms.Control.Margin%2A> d'un contrôle.

![Remplissage et marge pour les contrôles Windows Forms](./media/vs-winformpadmargin.gif)

La <xref:System.Windows.Forms.Control.AutoSize%2A> propriété indique à un contrôle de se Dimensionner automatiquement à son contenu. Il ne se redimensionne pas pour être plus petit que la valeur de <xref:System.Windows.Forms.Control.Size%2A> sa propriété d’origine, et il prend en compte la <xref:System.Windows.Forms.Control.Padding%2A> valeur de sa propriété.

## <a name="prerequisites"></a>Prérequis

Pour effectuer cette procédure pas à pas, vous avez besoin de Visual Studio.

## <a name="create-the-project"></a>Créer le projet

1. Dans Visual Studio, créez un projet d' **application Windows** appelé `LayoutExample`.

2. Sélectionnez le formulaire dans la **Concepteur Windows Forms**.

## <a name="set-margins-for-controls"></a>Définir des marges pour les contrôles

Vous pouvez définir la distance par défaut entre vos contrôles à <xref:System.Windows.Forms.Control.Margin%2A> l’aide de la propriété. Lorsque vous déplacez un contrôle suffisamment près d’un autre contrôle, une ligne d’alignement (SnapLine) s’affiche pour afficher les marges des deux contrôles. Le contrôle que vous déplacez est également aligné sur la distance définie par les marges.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Organiser des contrôles sur votre formulaire à l’aide de la propriété Margin

1. Faites glisser <xref:System.Windows.Forms.Button> deux contrôles de la **boîte à outils** vers votre formulaire.

2. Sélectionnez l’un des <xref:System.Windows.Forms.Button> contrôles et déplacez-le à proximité de l’autre, jusqu’à ce qu’ils soient presque en contact.

   Observez la ligne d’alignement (SnapLine) qui apparaît entre eux. Cette distance est la somme des <xref:System.Windows.Forms.Control.Margin%2A> valeurs des deux contrôles. Le contrôle que vous déplacez s’aligne à cette distance. Pour plus d’informations [, consultez Procédure pas à pas: Réorganisation des contrôles sur Windows Forms à](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)l’aide des lignes d’alignement.

3. Modifiez la <xref:System.Windows.Forms.Control.Margin%2A> propriété de l’un des contrôles en développant <xref:System.Windows.Forms.Control.Margin%2A> l’entrée dans la fenêtre **Propriétés** et en <xref:System.Windows.Forms.Padding.All%2A> affectant à la propriété la valeur **20**.

4. Sélectionnez l’un des <xref:System.Windows.Forms.Button> contrôles et déplacez-le à proximité de l’autre.

   La ligne d’alignement (SnapLine) définissant la somme des valeurs de marge est plus longue et le contrôle s’aligne sur une distance supérieure de l’autre contrôle.

5. Modifiez la <xref:System.Windows.Forms.Control.Margin%2A> propriété du contrôle sélectionné en développant l' <xref:System.Windows.Forms.Control.Margin%2A> entrée dans la fenêtre **Propriétés** et en affectant à la propriété la <xref:System.Windows.Forms.Padding.Top%2A> valeur **5**.

6. Déplacez le contrôle sélectionné sous l’autre contrôle et observez que la ligne d’alignement (SnapLine) est plus petite. Déplacez le contrôle sélectionné à gauche de l’autre contrôle et observez que la ligne d’alignement (SnapLine) conserve la valeur observée à l’étape 4.

7. Vous pouvez définir chacun <xref:System.Windows.Forms.Control.Margin%2A> des aspects de la propriété <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A> <xref:System.Windows.Forms.Padding.Left%2A> <xref:System.Windows.Forms.Padding.Right%2A>,,,, à différentes valeurs, ou vous pouvez les affecter à la même valeur que la <xref:System.Windows.Forms.Padding.All%2A> propriété.

## <a name="set-padding-for-controls"></a>Définir le remplissage des contrôles

Pour obtenir la disposition précise requise pour votre application, vos contrôles contiennent souvent des contrôles enfants. Lorsque vous souhaitez spécifier la proximité de la bordure du contrôle enfant à la bordure du contrôle parent, utilisez la <xref:System.Windows.Forms.Control.Padding%2A> propriété du contrôle parent conjointement avec la propriété du <xref:System.Windows.Forms.Control.Margin%2A> contrôle enfant. La <xref:System.Windows.Forms.Control.Padding%2A> propriété est également utilisée pour contrôler la proximité du contenu d’un contrôle (par exemple, la <xref:System.Windows.Forms.Button> propriété d' <xref:System.Windows.Forms.Control.Text%2A> un contrôle) à ses bordures.

### <a name="arrange-controls-on-your-form-using-padding"></a>Organiser des contrôles sur votre formulaire à l’aide du remplissage

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.

2. Remplacez la valeur de la <xref:System.Windows.Forms.Button> propriété du <xref:System.Windows.Forms.Control.AutoSize%2A> contrôle par **true**.

3. Modifiez la <xref:System.Windows.Forms.Control.Padding%2A> propriété en développant <xref:System.Windows.Forms.Control.Padding%2A> l’entrée dans la fenêtre **Propriétés** et en <xref:System.Windows.Forms.Padding.All%2A> affectant à la propriété la valeur **5**.

   Le contrôle se développe pour fournir de l’espace pour le nouveau remplissage.

4. Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **boîte à outils** vers le formulaire. Faites glisser <xref:System.Windows.Forms.Button> un contrôle de la **boîte à outils** vers le <xref:System.Windows.Forms.GroupBox> contrôle. Placez le <xref:System.Windows.Forms.Button> contrôle afin qu’il soit vidé avec l’angle inférieur droit <xref:System.Windows.Forms.GroupBox> du contrôle.

   Observez les lignes <xref:System.Windows.Forms.GroupBox> d’alignement qui <xref:System.Windows.Forms.Button> apparaissent lorsque le contrôle s’approche des bordures inférieure et droite du contrôle. Ces lignes d’alignement correspondent <xref:System.Windows.Forms.Control.Margin%2A> à la propriété <xref:System.Windows.Forms.Button>de.

5. Modifiez la <xref:System.Windows.Forms.GroupBox> propriété du <xref:System.Windows.Forms.Control.Padding%2A> contrôle en développant <xref:System.Windows.Forms.Control.Padding%2A> l’entrée dans la fenêtre **Propriétés** et en <xref:System.Windows.Forms.Padding.All%2A> affectant à la propriété la valeur **20**.

6. Sélectionnez le <xref:System.Windows.Forms.Button> contrôle dans le <xref:System.Windows.Forms.GroupBox> contrôle et déplacez-le <xref:System.Windows.Forms.GroupBox>vers le centre de.

   Les lignes d’alignement apparaissent à une distance supérieure des bordures <xref:System.Windows.Forms.GroupBox> du contrôle. Cette distance est la somme de la <xref:System.Windows.Forms.Button> propriété du <xref:System.Windows.Forms.Control.Margin%2A> contrôle et de <xref:System.Windows.Forms.GroupBox> la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle.

## <a name="size-controls-automatically"></a>Dimensionner automatiquement les contrôles

Dans certaines applications, la taille d’un contrôle ne sera pas la même au moment de l’exécution qu’au moment de la conception. Le texte d’un <xref:System.Windows.Forms.Button> contrôle, par exemple, peut être extrait d’une base de données, et sa longueur n’est pas connue à l’avance.

Lorsque la <xref:System.Windows.Forms.Control.AutoSize%2A> propriété a la `true`valeur, le contrôle se redimensionne en son contenu. Pour plus d’informations, consultez [vue d’ensemble](autosize-property-overview.md)de la propriété AutoSize.

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>Organiser des contrôles sur votre formulaire à l’aide de la propriété AutoSize

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.

2. Remplacez la valeur de la <xref:System.Windows.Forms.Button> propriété du <xref:System.Windows.Forms.Control.AutoSize%2A> contrôle par **true**.

3. Remplacez la <xref:System.Windows.Forms.Button> valeur de <xref:System.Windows.Forms.Control.Text%2A> la propriété du contrôle par **ce bouton par une chaîne longue pour sa propriété Text**.

   Lorsque vous validez la modification, <xref:System.Windows.Forms.Button> le contrôle se redimensionne pour s’adapter au nouveau texte.

4. Faites glisser <xref:System.Windows.Forms.Button> un autre contrôle de la **boîte à outils** vers votre formulaire.

5. Modifier le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Text%2A> propriété à « **ce bouton a une longue chaîne pour sa propriété Text.** »

   Lorsque vous validez la modification, <xref:System.Windows.Forms.Button> le contrôle ne se redimensionne pas et le texte est coupé par le bord droit du contrôle.

6. Modifiez la <xref:System.Windows.Forms.Control.Padding%2A> propriété en développant <xref:System.Windows.Forms.Control.Padding%2A> l’entrée dans la fenêtre **Propriétés** et en <xref:System.Windows.Forms.Padding.All%2A> affectant à la propriété la valeur **5**.

   Le texte de l’intérieur du contrôle est coupé sur les quatre côtés.

7. Affectez <xref:System.Windows.Forms.Button> à la <xref:System.Windows.Forms.Control.AutoSize%2A> propriété du contrôle la **valeur true**.

   Le <xref:System.Windows.Forms.Button> contrôle se redimensionne pour englober la chaîne entière. En outre, le remplissage a été ajouté autour du texte, provoquant le développement du <xref:System.Windows.Forms.Button> contrôle dans les quatre directions.

8. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire. Placez-le près de l’angle inférieur droit du formulaire.

9. Remplacez la valeur de la <xref:System.Windows.Forms.Button> propriété du <xref:System.Windows.Forms.Control.AutoSize%2A> contrôle par **true**.

10. Affectez <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> à <xref:System.Windows.Forms.AnchorStyles.Bottom>la propriété du contrôle la valeur,. <xref:System.Windows.Forms.AnchorStyles.Right>

11. Modifier le <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Text%2A> propriété à « **ce bouton a une longue chaîne pour sa propriété Text.** »

   Lorsque vous validez la modification, <xref:System.Windows.Forms.Button> le contrôle se redimensionne vers la gauche. En général, le dimensionnement automatique augmente la taille d’un contrôle dans la direction opposée à son <xref:System.Windows.Forms.Control.Anchor%2A> paramètre de propriété.

## <a name="autosize-and-autosizemode-properties"></a>Propriétés AutoSize et AutoSizeMode

 Certains contrôles prennent en `AutoSizeMode` charge la propriété, qui vous donne un contrôle plus précis du comportement de dimensionnement automatique d’un contrôle.

### <a name="use-the-autosizemode-property"></a>Utiliser la propriété AutoSizeMode

1. Faites glisser un contrôle <xref:System.Windows.Forms.Panel> de la **boîte à outils** vers le formulaire.

2. Affectez la valeur <xref:System.Windows.Forms.Panel> **true**à la <xref:System.Windows.Forms.Control.AutoSize%2A> propriété du contrôle.

3. Faites glisser <xref:System.Windows.Forms.Button> un contrôle de la **boîte à outils** vers le <xref:System.Windows.Forms.Panel> contrôle.

4. Placez le <xref:System.Windows.Forms.Button> contrôle près <xref:System.Windows.Forms.Panel> de l’angle inférieur droit du contrôle.

5. Sélectionnez le <xref:System.Windows.Forms.Panel> contrôle et saisissez la poignée de redimensionnement inférieure droite. Redimensionnez <xref:System.Windows.Forms.Panel> le contrôle pour qu’il soit plus grand et plus petit.

   > [!NOTE]
   > Vous pouvez redimensionner librement <xref:System.Windows.Forms.Panel> le contrôle, mais vous ne pouvez pas le redimensionner plus <xref:System.Windows.Forms.Button> petit que la position du coin inférieur droit du contrôle. Ce comportement est spécifié par la valeur par défaut de `AutoSizeMode` la propriété, qui <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>est.

6. Affectez à <xref:System.Windows.Forms.Panel> `AutoSizeMode` la<xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>propriété du contrôle la valeur.

   Le <xref:System.Windows.Forms.Panel> contrôle se redimensionne pour <xref:System.Windows.Forms.Button> entourer le contrôle. Vous ne pouvez pas redimensionner le <xref:System.Windows.Forms.Panel> contrôle.

7. Faites glisser <xref:System.Windows.Forms.Button> le contrôle vers le coin supérieur gauche <xref:System.Windows.Forms.Panel> du contrôle.

   Le <xref:System.Windows.Forms.Panel> contrôle est redimensionné à la <xref:System.Windows.Forms.Button> nouvelle position du contrôle.

## <a name="next-steps"></a>Étapes suivantes

Il existe de nombreuses autres fonctionnalités de disposition pour organiser les contrôles dans vos applications Windows Forms. Voici quelques combinaisons que vous pouvez essayer:

- Générez un formulaire à <xref:System.Windows.Forms.TableLayoutPanel> l’aide d’un contrôle. Pour plus d’informations [, consultez Procédure pas à pas: Réorganisation des contrôles sur Windows Forms à l'](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)aide d’un TableLayoutPanel. Essayez de modifier les valeurs de <xref:System.Windows.Forms.TableLayoutPanel> la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle, ainsi que la <xref:System.Windows.Forms.Control.Margin%2A> propriété sur ses contrôles enfants.

- Essayez la même expérience à l' <xref:System.Windows.Forms.FlowLayoutPanel> aide d’un contrôle. Pour plus d’informations [, consultez Procédure pas à pas: Réorganisation des contrôles sur Windows Forms à l'](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)aide d’un FlowLayoutPanel.

- Expérimentez l’ancrage des contrôles enfants dans <xref:System.Windows.Forms.Panel> un contrôle. La <xref:System.Windows.Forms.Control.Padding%2A> propriété est une réalisation plus générale de la <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A> propriété, et vous pouvez vous assurer que c’est le cas en plaçant un contrôle enfant dans un <xref:System.Windows.Forms.Panel> contrôle et en affectant à <xref:System.Windows.Forms.Control.Dock%2A> <xref:System.Windows.Forms.DockStyle.Fill>lapropriétéducontrôleenfantlavaleur. Affectez <xref:System.Windows.Forms.Panel> à la <xref:System.Windows.Forms.Control.Padding%2A> propriété du contrôle des valeurs différentes et notez l’effet.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [Vue d’ensemble de la propriété AutoSize](autosize-property-overview.md)
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide de lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
