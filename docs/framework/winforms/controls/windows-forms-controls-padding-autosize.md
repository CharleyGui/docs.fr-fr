---
title: Disposer les contrôles avec le remplissage, les marges et la propriété AutoSize
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ca7942c04434592f2541252c47ac3dd17e03dbac
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742373"
---
# <a name="walkthrough-lay-out-controls-with-padding-margins-and-the-autosize-property"></a>Procédure pas à pas : disposition des contrôles avec le remplissage, les marges et la propriété AutoSize

Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications. La **Concepteur Windows Forms** dans Visual Studio vous donne de nombreux outils de mise en page pour y parvenir. Trois des plus importantes sont les propriétés <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Control.Padding%2A>et <xref:System.Windows.Forms.Control.AutoSize%2A>, qui sont présentes sur tous les contrôles Windows Forms.

La propriété <xref:System.Windows.Forms.Control.Margin%2A> définit l'espace autour du contrôle qui maintient les autres contrôles à une distance spécifiée des bordures du contrôle.

La propriété <xref:System.Windows.Forms.Control.Padding%2A> définit l'espace à l'intérieur d'un contrôle qui maintient le contenu du contrôle (par exemple la valeur de sa propriété <xref:System.Windows.Forms.Control.Text%2A>) à une distance spécifiée des bordures du contrôle.

L'illustration suivante montre les propriétés <xref:System.Windows.Forms.Control.Padding%2A> et <xref:System.Windows.Forms.Control.Margin%2A> d'un contrôle.

![Remplissage et marge pour les contrôles Windows Forms](./media/vs-winformpadmargin.gif)

La propriété <xref:System.Windows.Forms.Control.AutoSize%2A> indique à un contrôle de se redimensionner automatiquement à son contenu. Il ne se redimensionne pas pour être plus petit que la valeur de sa propriété <xref:System.Windows.Forms.Control.Size%2A> d’origine, et il prend en compte la valeur de sa propriété <xref:System.Windows.Forms.Control.Padding%2A>.

## <a name="prerequisites"></a>Composants requis

Pour effectuer cette procédure pas à pas, vous avez besoin de Visual Studio.

## <a name="create-the-project"></a>Créer le projet

1. Dans Visual Studio, créez un projet d' **application Windows** appelé `LayoutExample`.

2. Sélectionnez le formulaire dans la **Concepteur Windows Forms**.

## <a name="set-margins-for-controls"></a>Définir des marges pour les contrôles

Vous pouvez définir la distance par défaut entre vos contrôles à l’aide de la propriété <xref:System.Windows.Forms.Control.Margin%2A>. Lorsque vous déplacez un contrôle suffisamment près d’un autre contrôle, une ligne d’alignement (SnapLine) s’affiche pour afficher les marges des deux contrôles. Le contrôle que vous déplacez est également aligné sur la distance définie par les marges.

### <a name="arrange-controls-on-your-form-using-the-margin-property"></a>Organiser des contrôles sur votre formulaire à l’aide de la propriété Margin

1. Faites glisser deux contrôles <xref:System.Windows.Forms.Button> de la **boîte à outils** vers votre formulaire.

2. Sélectionnez l’un des contrôles <xref:System.Windows.Forms.Button> et déplacez-le à proximité de l’autre, jusqu’à ce qu’ils soient presque en contact.

   Observez la ligne d’alignement (SnapLine) qui apparaît entre eux. Cette distance est la somme des valeurs <xref:System.Windows.Forms.Control.Margin%2A> des deux contrôles. Le contrôle que vous déplacez s’aligne à cette distance. Pour plus d’informations, consultez [procédure pas à pas : Organisation des contrôles sur Windows Forms à l’aide des lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).

3. Modifiez la propriété <xref:System.Windows.Forms.Control.Margin%2A> de l’un des contrôles en développant l’entrée <xref:System.Windows.Forms.Control.Margin%2A> dans la fenêtre **Propriétés** et en affectant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur **20**.

4. Sélectionnez l’un des contrôles <xref:System.Windows.Forms.Button> et déplacez-le à proximité de l’autre.

   La ligne d’alignement (SnapLine) définissant la somme des valeurs de marge est plus longue et le contrôle s’aligne sur une distance supérieure de l’autre contrôle.

5. Modifiez la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle sélectionné en développant l’entrée <xref:System.Windows.Forms.Control.Margin%2A> dans la fenêtre **Propriétés** et en affectant à la propriété <xref:System.Windows.Forms.Padding.Top%2A> la valeur **5**.

6. Déplacez le contrôle sélectionné sous l’autre contrôle et observez que la ligne d’alignement (SnapLine) est plus petite. Déplacez le contrôle sélectionné à gauche de l’autre contrôle et observez que la ligne d’alignement (SnapLine) conserve la valeur observée à l’étape 4.

7. Vous pouvez définir chacun des aspects de la propriété <xref:System.Windows.Forms.Control.Margin%2A>, <xref:System.Windows.Forms.Padding.Left%2A>, <xref:System.Windows.Forms.Padding.Top%2A>, <xref:System.Windows.Forms.Padding.Right%2A>, <xref:System.Windows.Forms.Padding.Bottom%2A>, sur différentes valeurs, ou vous pouvez les affecter à la même valeur que la propriété <xref:System.Windows.Forms.Padding.All%2A>.

## <a name="set-padding-for-controls"></a>Définir le remplissage des contrôles

Pour obtenir la disposition précise requise pour votre application, vos contrôles contiennent souvent des contrôles enfants. Lorsque vous souhaitez spécifier la proximité de la bordure du contrôle enfant à la bordure du contrôle parent, utilisez la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle parent conjointement avec la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle enfant. La propriété <xref:System.Windows.Forms.Control.Padding%2A> est également utilisée pour contrôler la proximité du contenu d’un contrôle (par exemple, la propriété <xref:System.Windows.Forms.Control.Text%2A> d’un contrôle <xref:System.Windows.Forms.Button>) à ses bordures.

### <a name="arrange-controls-on-your-form-using-padding"></a>Organiser des contrôles sur votre formulaire à l’aide du remplissage

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.

2. Remplacez la valeur de la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button> par **true**.

3. Modifiez la propriété <xref:System.Windows.Forms.Control.Padding%2A> en développant l’entrée <xref:System.Windows.Forms.Control.Padding%2A> dans la fenêtre **Propriétés** et en affectant la valeur **5**à la propriété <xref:System.Windows.Forms.Padding.All%2A>.

   Le contrôle se développe pour fournir de l’espace pour le nouveau remplissage.

4. Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **boîte à outils** vers le formulaire. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le contrôle <xref:System.Windows.Forms.GroupBox>. Placez le contrôle <xref:System.Windows.Forms.Button> pour qu’il soit vidé avec l’angle inférieur droit du contrôle <xref:System.Windows.Forms.GroupBox>.

   Observez les lignes d’alignement qui apparaissent lorsque le contrôle <xref:System.Windows.Forms.Button> approche des bordures inférieure et droite du contrôle <xref:System.Windows.Forms.GroupBox>. Ces lignes d’alignement correspondent à la propriété <xref:System.Windows.Forms.Control.Margin%2A> du <xref:System.Windows.Forms.Button>.

5. Modifiez la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.GroupBox> en développant l’entrée <xref:System.Windows.Forms.Control.Padding%2A> dans la fenêtre **Propriétés** et en affectant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur **20**.

6. Sélectionnez le contrôle <xref:System.Windows.Forms.Button> dans le contrôle <xref:System.Windows.Forms.GroupBox> et déplacez-le vers le centre de la <xref:System.Windows.Forms.GroupBox>.

   Les lignes d’alignement apparaissent à une distance supérieure des bordures du contrôle <xref:System.Windows.Forms.GroupBox>. Cette distance est la somme de la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle <xref:System.Windows.Forms.Button> et de la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.GroupBox>.

## <a name="size-controls-automatically"></a>Dimensionner automatiquement les contrôles

Dans certaines applications, la taille d’un contrôle ne sera pas la même au moment de l’exécution qu’au moment de la conception. Le texte d’un contrôle de <xref:System.Windows.Forms.Button>, par exemple, peut être extrait d’une base de données, et sa longueur n’est pas connue à l’avance.

Lorsque la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> est définie sur `true`, le contrôle se redimensionne en son contenu. Pour plus d’informations, consultez [vue d’ensemble de la propriété AutoSize](autosize-property-overview.md).

### <a name="arrange-controls-on-your-form-using-the-autosize-property"></a>Organiser des contrôles sur votre formulaire à l’aide de la propriété AutoSize

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.

2. Remplacez la valeur de la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button> par **true**.

3. Remplacez la valeur de la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle <xref:System.Windows.Forms.Button> par **ce bouton par une chaîne longue pour sa propriété Text**.

   Lorsque vous validez la modification, le contrôle <xref:System.Windows.Forms.Button> se redimensionne pour s’adapter au nouveau texte.

4. Faites glisser un autre contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers votre formulaire.

5. Affectez à la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur "**ce bouton a une longue chaîne pour sa propriété Text.** "

   Lorsque vous validez la modification, le contrôle <xref:System.Windows.Forms.Button> ne se redimensionne pas et le texte est coupé par le bord droit du contrôle.

6. Modifiez la propriété <xref:System.Windows.Forms.Control.Padding%2A> en développant l’entrée <xref:System.Windows.Forms.Control.Padding%2A> dans la fenêtre **Propriétés** et en affectant la valeur **5**à la propriété <xref:System.Windows.Forms.Padding.All%2A>.

   Le texte de l’intérieur du contrôle est coupé sur les quatre côtés.

7. Affectez à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button> la **valeur true**.

   Le contrôle <xref:System.Windows.Forms.Button> se redimensionne pour englober la chaîne entière. En outre, le remplissage a été ajouté autour du texte, provoquant le développement du contrôle <xref:System.Windows.Forms.Button> dans les quatre directions.

8. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire. Placez-le près de l’angle inférieur droit du formulaire.

9. Remplacez la valeur de la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Button> par **true**.

10. Affectez à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur <xref:System.Windows.Forms.AnchorStyles.Right>, <xref:System.Windows.Forms.AnchorStyles.Bottom>.

11. Affectez à la propriété <xref:System.Windows.Forms.Control.Text%2A> du contrôle <xref:System.Windows.Forms.Button> la valeur "**ce bouton a une longue chaîne pour sa propriété Text.** "

   Lorsque vous validez la modification, le contrôle <xref:System.Windows.Forms.Button> se redimensionne vers la gauche. En général, le dimensionnement automatique augmente la taille d’un contrôle dans la direction opposée à son paramètre de propriété <xref:System.Windows.Forms.Control.Anchor%2A>.

## <a name="autosize-and-autosizemode-properties"></a>Propriétés AutoSize et AutoSizeMode

 Certains contrôles prennent en charge la propriété `AutoSizeMode`, qui vous donne un contrôle plus précis du comportement de dimensionnement automatique d’un contrôle.

### <a name="use-the-autosizemode-property"></a>Utiliser la propriété AutoSizeMode

1. Faites glisser un contrôle <xref:System.Windows.Forms.Panel> de la **boîte à outils** vers le formulaire.

2. Affectez la valeur **true**à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Panel>.

3. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le contrôle <xref:System.Windows.Forms.Panel>.

4. Placez le contrôle <xref:System.Windows.Forms.Button> près du coin inférieur droit du contrôle <xref:System.Windows.Forms.Panel>.

5. Sélectionnez le contrôle <xref:System.Windows.Forms.Panel> et saisissez la poignée de redimensionnement inférieure droite. Redimensionnez le contrôle <xref:System.Windows.Forms.Panel> pour qu’il soit plus grand et plus petit.

   > [!NOTE]
   > Vous pouvez redimensionner librement le contrôle <xref:System.Windows.Forms.Panel>, mais vous ne pouvez pas le dimensionner plus petit que la position du coin inférieur droit du contrôle <xref:System.Windows.Forms.Button>. Ce comportement est spécifié par la valeur par défaut de la propriété `AutoSizeMode`, qui est <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>.

6. Définissez la valeur de la propriété `AutoSizeMode` du contrôle <xref:System.Windows.Forms.Panel> sur <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>.

   Le contrôle <xref:System.Windows.Forms.Panel> se dimensionne lui-même pour entourer le contrôle <xref:System.Windows.Forms.Button>. Vous ne pouvez pas redimensionner le contrôle de <xref:System.Windows.Forms.Panel>.

7. Faites glisser le contrôle <xref:System.Windows.Forms.Button> vers le coin supérieur gauche du contrôle <xref:System.Windows.Forms.Panel>.

   Le contrôle <xref:System.Windows.Forms.Panel> est redimensionné en fonction de la nouvelle position du contrôle <xref:System.Windows.Forms.Button>.

## <a name="next-steps"></a>Étapes suivantes :

Il existe de nombreuses autres fonctionnalités de disposition pour organiser les contrôles dans vos applications Windows Forms. Voici quelques combinaisons que vous pouvez essayer :

- Générez un formulaire à l’aide d’un contrôle de <xref:System.Windows.Forms.TableLayoutPanel>. Pour plus d’informations, consultez [procédure pas à pas : Organisation des contrôles sur Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md). Essayez de modifier les valeurs de la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.TableLayoutPanel>, ainsi que la propriété <xref:System.Windows.Forms.Control.Margin%2A> sur ses contrôles enfants.

- Essayez la même expérience à l’aide d’un contrôle de <xref:System.Windows.Forms.FlowLayoutPanel>. Pour plus d’informations, consultez [procédure pas à pas : Organisation des contrôles sur Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

- Expérimentez l’ancrage des contrôles enfants dans un contrôle de <xref:System.Windows.Forms.Panel>. La propriété <xref:System.Windows.Forms.Control.Padding%2A> est une réalisation plus générale de la propriété <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>, et vous pouvez vous assurer que c’est le cas en plaçant un contrôle enfant dans un contrôle <xref:System.Windows.Forms.Panel> et en affectant à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle enfant la valeur <xref:System.Windows.Forms.DockStyle.Fill>. Affectez à la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.Panel> des valeurs différentes et notez l’effet.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.ScrollableControl.DockPadding%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- [Vue d’ensemble de la propriété AutoSize](autosize-property-overview.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
