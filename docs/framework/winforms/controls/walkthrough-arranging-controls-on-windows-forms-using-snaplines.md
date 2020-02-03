---
title: Organisation des contrôles à l’aide des lignes d’alignement
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3b88f64fca8d3f11308f1cbfde97de2e6c2f22cc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740221"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>Procédure pas à pas : Organisation des contrôles sur Windows Forms à l’aide de lignes d’alignement

Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications. Le Concepteur Windows Forms vous donne de nombreux outils de disposition pour y parvenir. L’une des plus importantes est la fonctionnalité <xref:System.Windows.Forms.Design.Behavior.SnapLine>.

Les lignes d’alignement vous montrent précisément où aligner les contrôles avec d’autres contrôles. Ils indiquent également les distances recommandées pour les marges entre les contrôles, comme spécifié par les instructions de l' [interface utilisateur Windows](/windows/win32/uxguide/guidelines).

Les lignes d’alignement facilitent l’alignement de vos contrôles, pour une apparence et un comportement professionnels nets (apparence et convivialité).

## <a name="create-the-project"></a>Créer le projet

1. Dans Visual Studio, créez un projet d’application Windows nommé « SnaplineExample ».

2. Sélectionnez le formulaire dans le Concepteur de formulaires.

## <a name="space-and-align-controls"></a>Espace et contrôles d’alignement

Les lignes d’alignement vous offrent un moyen précis et intuitif d’aligner les contrôles sur votre formulaire. Elles s’affichent lorsque vous déplacez un contrôle ou des contrôles sélectionnés à proximité d’une position qui s’aligne sur un autre contrôle ou ensemble de contrôles. Votre sélection sera « alignée » à la position suggérée quand vous la déplacerez après les autres contrôles.

### <a name="to-arrange-controls-using-snaplines"></a>Pour réorganiser les contrôles à l’aide des lignes d’alignement

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.

2. Déplacez le contrôle <xref:System.Windows.Forms.Button> dans l’angle inférieur droit du formulaire. Notez les lignes d’alignement qui apparaissent lorsque le contrôle <xref:System.Windows.Forms.Button> approche des bordures inférieure et droite du formulaire. Ces lignes d’alignement affichent la distance recommandée entre les bordures du contrôle et le formulaire.

3. Déplacez le contrôle <xref:System.Windows.Forms.Button> autour des bordures du formulaire et notez l’endroit où les lignes d’alignement apparaissent. Lorsque vous avez terminé, déplacez le contrôle <xref:System.Windows.Forms.Button> près du centre du formulaire.

4. Faites glisser un autre contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers votre formulaire.

5. Déplacez le deuxième contrôle <xref:System.Windows.Forms.Button> jusqu’à ce qu’il soit quasiment niveau avec le premier. Notez la ligne d’alignement (SnapLine) qui apparaît à la ligne de base de texte des deux boutons, et notez que le contrôle que vous déplacez s’aligne à une position qui est exactement au même niveau que l’autre contrôle.

6. Déplacez le deuxième contrôle <xref:System.Windows.Forms.Button> jusqu’à ce qu’il soit positionné directement au-dessus du premier. Notez les lignes d’alignement (SnapLines) qui apparaissent le long des bords gauche et droit des deux boutons, et notez que le contrôle que vous déplacez s’aligne sur une position qui est exactement alignée sur l’autre contrôle.

7. Sélectionnez l’un des contrôles <xref:System.Windows.Forms.Button> et déplacez-le à proximité de l’autre, jusqu’à ce qu’ils soient presque en contact. Notez la ligne d’alignement (SnapLine) qui apparaît entre eux. Cette distance est la distance recommandée entre les bordures des contrôles. Notez également que le contrôle que vous déplacez s’aligne à cette position.

8. Faites glisser deux contrôles <xref:System.Windows.Forms.Panel> de la **boîte à outils** vers votre formulaire.

9. Déplacez l’un des contrôles <xref:System.Windows.Forms.Panel> jusqu’à ce qu’il soit quasiment niveau avec le premier. Notez les lignes d’alignement (SnapLines) qui apparaissent le long des bords supérieur et inférieur des deux contrôles, et notez que le contrôle que vous déplacez s’aligne à une position qui est exactement au même niveau que l’autre contrôle.

## <a name="align-to-form-and-container-margins"></a>Aligner sur les marges de formulaire et de conteneur

Les lignes d’alignement vous aident à aligner vos contrôles sur les marges de formulaire et de conteneur de manière cohérente.

1. Sélectionnez l’un des contrôles <xref:System.Windows.Forms.Button> et déplacez-le à proximité de la bordure droite du formulaire jusqu’à ce qu’une ligne d’alignement apparaisse. La distance de la ligne d’alignement (SnapLine) par rapport à la bordure droite est la somme de la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle et des valeurs de propriété <xref:System.Windows.Forms.Control.Padding%2A> du formulaire.

   > [!NOTE]
   > Si la propriété <xref:System.Windows.Forms.Control.Padding%2A> du formulaire est définie sur 0, 0, 0, 0, le Concepteur Windows Forms donne au formulaire une valeur de <xref:System.Windows.Forms.Control.Padding%2A> occultée de 9, 9, 9, 9. Pour remplacer ce comportement, assignez une valeur différente de 0, 0, 0, 0.

2. Modifiez la valeur de la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle <xref:System.Windows.Forms.Button> en développant l’entrée <xref:System.Windows.Forms.Control.Margin%2A> dans la fenêtre **Propriétés** et en affectant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur 0. Pour plus d’informations, consultez [procédure pas à pas : disposition des contrôles Windows Forms avec le remplissage, les marges et la propriété AutoSize](windows-forms-controls-padding-autosize.md).

3. Déplacez le contrôle <xref:System.Windows.Forms.Button> à proximité de la bordure droite du formulaire jusqu’à ce qu’une ligne d’alignement apparaisse. Cette distance est maintenant donnée par la valeur de la propriété <xref:System.Windows.Forms.Control.Padding%2A> du formulaire.

4. Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **boîte à outils** vers le formulaire.

5. Modifiez la valeur de la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.GroupBox> en développant l’entrée <xref:System.Windows.Forms.Control.Padding%2A> dans la fenêtre **Propriétés** et en affectant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur 10.

6. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le contrôle <xref:System.Windows.Forms.GroupBox>.

7. Déplacez le contrôle <xref:System.Windows.Forms.Button> à proximité de la bordure droite du contrôle <xref:System.Windows.Forms.GroupBox> jusqu’à ce qu’une ligne d’alignement s’affiche. Déplacez le contrôle <xref:System.Windows.Forms.Button> dans le contrôle <xref:System.Windows.Forms.GroupBox> et notez l’emplacement où les lignes d’alignement apparaissent.

## <a name="align-to-grouped-controls"></a>Aligner sur les contrôles groupés

Vous pouvez utiliser des lignes d’alignement pour aligner les contrôles groupés et les contrôles dans un contrôle de <xref:System.Windows.Forms.GroupBox>.

1. Sélectionnez deux des contrôles de votre formulaire. Déplacez la sélection autour et notez les lignes d’alignement qui apparaissent entre votre sélection et les autres contrôles.

2. Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **boîte à outils** vers le formulaire.

3. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le contrôle <xref:System.Windows.Forms.GroupBox>.

4. Sélectionnez l’un des contrôles <xref:System.Windows.Forms.Button> et déplacez-le autour du contrôle <xref:System.Windows.Forms.GroupBox>. Notez les lignes d’alignement qui apparaissent aux bords du contrôle <xref:System.Windows.Forms.GroupBox>. Notez également les lignes d’alignement qui apparaissent aux bords du contrôle <xref:System.Windows.Forms.Button> contenu dans le contrôle <xref:System.Windows.Forms.GroupBox>. Les contrôles qui sont des enfants d’un contrôle conteneur prennent également en charge les lignes d’alignement.

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>Utilisez des lignes d’alignement pour placer un contrôle en soulignant sa taille

1. Dans la **Boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> . Ne la faites pas glisser sur le formulaire.

2. Placez le pointeur de la souris sur l’aire de conception du formulaire. Notez que le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.Button> . Notez également les lignes d’alignement qui apparaissent pour suggérer des positions alignées pour le contrôle <xref:System.Windows.Forms.Button>.

3. Cliquez et maintenez le bouton de la souris enfoncé.

4. Faites glisser le pointeur de la souris autour du formulaire. Notez qu’un contour est dessiné, indiquant la position et la taille du contrôle.

5. Faites glisser le pointeur jusqu’à ce qu’il s’aligne avec un autre contrôle sur le formulaire. Notez qu’une ligne d’alignement s’affiche pour indiquer l’alignement.

6. Relâchez le bouton de la souris. Le contrôle est créé à la position et à la taille indiquées par le plan.

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Utiliser des lignes d’alignement quand vous faites glisser un contrôle à partir de la boîte à outils

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers votre formulaire, mais ne relâchez pas le bouton de la souris.

2. Placez le pointeur de la souris sur l’aire de conception du formulaire. Notez que le pointeur change pour indiquer la position à laquelle le nouveau contrôle de <xref:System.Windows.Forms.Button> sera créé.

3. Faites glisser le pointeur de la souris autour du formulaire. Notez les lignes d’alignement qui apparaissent pour suggérer des positions alignées pour le contrôle <xref:System.Windows.Forms.Button>. Recherche une position qui est alignée avec d’autres contrôles.

4. Relâchez le bouton de la souris. Le contrôle est créé à l’emplacement indiqué par les lignes d’alignement (SnapLines).

## <a name="resize-a-control-using-snaplines"></a>Redimensionner un contrôle à l’aide de lignes d’alignement

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.

2. Redimensionnez le contrôle <xref:System.Windows.Forms.Button> en saisissant l’une des poignées de dimensionnement d’angle et en la faisant glisser. Pour plus d’informations, consultez [Comment : redimensionner des contrôles sur Windows Forms](how-to-resize-controls-on-windows-forms.md).

3. Faites glisser la poignée de redimensionnement jusqu’à ce que l’une des bordures du contrôle <xref:System.Windows.Forms.Button> soit alignée sur un autre contrôle. Notez qu’une ligne d’alignement (SnapLine) s’affiche. Notez également que la poignée de redimensionnement s’aligne à la position indiquée par la ligne d’alignement (SnapLine).

4. Redimensionner le contrôle <xref:System.Windows.Forms.Button> dans différentes directions et aligner la poignée de redimensionnement sur différents contrôles. Notez comment les lignes d’alignement apparaissent dans différentes orientations pour indiquer l’alignement.

## <a name="align-a-label-to-a-controls-text"></a>Aligner une étiquette sur le texte d’un contrôle

1. Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> de la **boîte à outils** vers le formulaire. Lorsque vous déposez le contrôle <xref:System.Windows.Forms.TextBox> dans le formulaire, cliquez sur le glyphe de balise active et sélectionnez l’option **définir le texte sur TextBox1** . Pour plus d’informations, consultez [procédure pas à pas : exécution de tâches courantes à l’aide de balises actives sur des contrôles Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md).

2. Faites glisser un contrôle <xref:System.Windows.Forms.Label> de la **boîte à outils** vers le formulaire.

3. Affectez la valeur <xref:System.Windows.Forms.Label> à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle `true`. Notez que les bordures du contrôle sont ajustées pour s’ajuster au texte d’affichage.

4. Déplacez le contrôle <xref:System.Windows.Forms.Label> à gauche du contrôle <xref:System.Windows.Forms.TextBox>, afin qu’il soit aligné avec le bord inférieur du contrôle <xref:System.Windows.Forms.TextBox>. Notez la ligne d’alignement (SnapLine) qui apparaît le long des bords inférieurs des deux contrôles.

5. Déplacez légèrement le contrôle <xref:System.Windows.Forms.Label> vers le haut, jusqu’à ce que le texte <xref:System.Windows.Forms.Label> et le texte <xref:System.Windows.Forms.TextBox> soient alignés. Notez la ligne d’alignement (SnapLine) stylisée différente qui apparaît, indiquant quand les champs de texte des deux contrôles sont alignés.

## <a name="use-snaplines-with-keyboard-navigation"></a>Utiliser des lignes d’alignement avec la navigation au clavier

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire. Placez-le dans le coin supérieur gauche du formulaire.

2. Appuyez sur **Ctrl**+**flèche bas**. Notez que le contrôle descend le formulaire jusqu’à la première position d’alignement horizontal disponible.

3. Appuyez sur **Ctrl**+**flèche bas** jusqu’à ce que le contrôle atteigne le bas du formulaire. Notez les positions qu’il occupe au fur et à mesure qu’il descend dans le formulaire.

4. Appuyez sur **Ctrl**+**flèche droite**. Notez que le contrôle se déplace dans le formulaire jusqu’à la première position d’alignement verticale disponible.

5. Appuyez sur **Ctrl**+**flèche droite** jusqu’à ce que le contrôle atteigne le côté du formulaire. Notez les positions qu’il occupe lorsqu’il se déplace dans le formulaire.

6. Déplacez le contrôle autour du formulaire à l’aide d’une combinaison de touches de direction. Notez les positions que le contrôle occupe et les lignes d’alignement (SnapLines) qui les accompagnent.

7. Appuyez sur **maj**+**touches de direction** pour redimensionner le contrôle <xref:System.Windows.Forms.Button> par incréments d’un pixel.

8. Appuyez sur **Ctrl**+**MAJ**+**touches de direction** pour redimensionner le contrôle <xref:System.Windows.Forms.Button> dans les incréments de ligne d’alignement (SnapLine).

## <a name="selectively-disable-snaplines"></a>Désactiver de manière sélective les lignes d’alignement

1. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

2. Double-cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> dans la **boîte à outils**. Notez qu’un nouveau contrôle bouton s’affiche dans la première cellule du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

3. Double-cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> dans la **boîte à outils** à deux reprises. Cela laisse une cellule vide dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.

4. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers la cellule vide du contrôle <xref:System.Windows.Forms.TableLayoutPanel>. Notez qu’aucune lignes d’alignement n’apparaît.

5. Faites glisser le contrôle <xref:System.Windows.Forms.Button> en dehors du contrôle <xref:System.Windows.Forms.TableLayoutPanel> et déplacez-le autour du contrôle <xref:System.Windows.Forms.TableLayoutPanel>. Notez que les lignes d’alignement s’affichent à nouveau.

## <a name="disable-snaplines"></a>Désactiver les lignes d’alignement

Appuyez sur la touche **ALT** et tout en déplaçant un contrôle dans le formulaire.

Aucune lignes d’alignement n’apparaît et le contrôle n’est pas aligné sur les positions d’alignement potentielles.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Pour désactiver les lignes d’alignement dans l’environnement de conception

1. Dans le menu **Outils** , ouvrez la boîte de dialogue **options** . Sélectionnez **Concepteur Windows Forms**.

2. Sélectionnez le nœud **général** . Dans la section **mode disposition** , remplacez la sélection **lignes d’alignement (SnapLines)** par **SnapToGrid**.

3. Sélectionnez **OK** pour appliquer le paramètre.

4. Sélectionnez un contrôle dans votre formulaire et déplacez-le autour des autres contrôles. Notez que les lignes d’alignement n’apparaissent pas.

## <a name="next-steps"></a>Étapes suivantes :

Les lignes d’alignement (SnapLines) offrent un moyen intuitif d’aligner les contrôles sur votre formulaire. Suggestions pour des recherches approfondies :

- Essayez d’imbriquer un contrôle <xref:System.Windows.Forms.GroupBox> dans un autre contrôle <xref:System.Windows.Forms.GroupBox>. Placez un contrôle de <xref:System.Windows.Forms.Button> dans le contrôle de <xref:System.Windows.Forms.GroupBox> enfant et un autre dans le contrôle <xref:System.Windows.Forms.GroupBox> parent. Déplacez les contrôles <xref:System.Windows.Forms.Button> autour pour voir comment les lignes d’alignement croisent les limites des conteneurs.

- Créez une colonne de <xref:System.Windows.Forms.TextBox> contrôles et une colonne correspondante de <xref:System.Windows.Forms.Label> contrôles. Définissez la valeur de la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> des contrôles de <xref:System.Windows.Forms.Label> sur `true`. Utilisez des lignes d’alignement pour déplacer les contrôles <xref:System.Windows.Forms.Label> afin que le texte affiché soit aligné avec le texte des contrôles <xref:System.Windows.Forms.TextBox>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](windows-forms-controls-padding-autosize.md)
