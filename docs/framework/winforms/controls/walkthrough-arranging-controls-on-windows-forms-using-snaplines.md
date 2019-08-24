---
title: 'Procédure pas à pas : organisation des contrôles dans des Windows Forms à l’aide de lignes d’alignement'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 83f0365ffb7335cb67c729c5a113e550c119191a
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986999"
---
# <a name="walkthrough-arrange-controls-on-windows-forms-using-snaplines"></a>Procédure pas à pas : Organiser les contrôles sur Windows Forms à l’aide de lignes d’alignement

Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications. Le Concepteur Windows Forms vous donne de nombreux outils de disposition pour y parvenir. L’une des plus importantes est la <xref:System.Windows.Forms.Design.Behavior.SnapLine> fonctionnalité.

Les lignes d’alignement vous montrent précisément où aligner les contrôles avec d’autres contrôles. Ils indiquent également les distances recommandées pour les marges entre les contrôles, comme spécifié par les instructions de l' [interface utilisateur Windows](/windows/win32/uxguide/guidelines).

Les lignes d’alignement facilitent l’alignement de vos contrôles, pour une apparence et un comportement professionnels nets (apparence et convivialité).

## <a name="create-the-project"></a>Créer le projet

1. Dans Visual Studio, créez un projet d’application Windows nommé «SnaplineExample».

2. Sélectionnez le formulaire dans le concepteur de formulaires.

## <a name="space-and-align-controls"></a>Espace et contrôles d’alignement

Les lignes d’alignement vous offrent un moyen précis et intuitif d’aligner les contrôles sur votre formulaire. Elles s’affichent lorsque vous déplacez un contrôle ou des contrôles sélectionnés à proximité d’une position qui s’aligne sur un autre contrôle ou ensemble de contrôles. Votre sélection sera «alignée» à la position suggérée quand vous la déplacerez après les autres contrôles.

### <a name="to-arrange-controls-using-snaplines"></a>Pour réorganiser les contrôles à l’aide des lignes d’alignement

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.

2. Déplacez le <xref:System.Windows.Forms.Button> contrôle vers le coin inférieur droit du formulaire. Notez les lignes d’alignement qui apparaissent <xref:System.Windows.Forms.Button> lorsque le contrôle s’approche des bordures inférieure et droite du formulaire. Ces lignes d’alignement affichent la distance recommandée entre les bordures du contrôle et le formulaire.

3. Déplacez le <xref:System.Windows.Forms.Button> contrôle autour des bordures du formulaire et notez l’endroit où les lignes d’alignement apparaissent. Lorsque vous avez terminé, déplacez le <xref:System.Windows.Forms.Button> contrôle vers le centre du formulaire.

4. Faites glisser <xref:System.Windows.Forms.Button> un autre contrôle de la **boîte à outils** vers votre formulaire.

5. Déplacez le deuxième <xref:System.Windows.Forms.Button> contrôle jusqu’à ce qu’il soit quasiment niveau avec le premier. Notez la ligne d’alignement (SnapLine) qui apparaît à la ligne de base de texte des deux boutons, et notez que le contrôle que vous déplacez s’aligne à une position qui est exactement au même niveau que l’autre contrôle.

6. Déplacez le deuxième <xref:System.Windows.Forms.Button> contrôle jusqu’à ce qu’il soit positionné directement au-dessus du premier. Notez les lignes d’alignement (SnapLines) qui apparaissent le long des bords gauche et droit des deux boutons, et notez que le contrôle que vous déplacez s’aligne sur une position qui est exactement alignée sur l’autre contrôle.

7. Sélectionnez l’un des <xref:System.Windows.Forms.Button> contrôles et déplacez-le à proximité de l’autre, jusqu’à ce qu’ils soient presque en contact. Notez la ligne d’alignement (SnapLine) qui apparaît entre eux. Cette distance est la distance recommandée entre les bordures des contrôles. Notez également que le contrôle que vous déplacez s’aligne à cette position.

8. Faites glisser <xref:System.Windows.Forms.Panel> deux contrôles de la **boîte à outils** vers votre formulaire.

9. Déplacez l’un des <xref:System.Windows.Forms.Panel> contrôles jusqu’à ce qu’il soit quasiment niveau avec le premier. Notez les lignes d’alignement (SnapLines) qui apparaissent le long des bords supérieur et inférieur des deux contrôles, et notez que le contrôle que vous déplacez s’aligne à une position qui est exactement au même niveau que l’autre contrôle.

## <a name="align-to-form-and-container-margins"></a>Aligner sur les marges de formulaire et de conteneur

Les lignes d’alignement vous aident à aligner vos contrôles sur les marges de formulaire et de conteneur de manière cohérente.

1. Sélectionnez l’un des <xref:System.Windows.Forms.Button> contrôles et déplacez-le à proximité de la bordure droite du formulaire jusqu’à ce qu’une ligne d’alignement s’affiche. La distance de la ligne d’alignement (SnapLine) par rapport à la bordure <xref:System.Windows.Forms.Control.Margin%2A> droite est la somme de <xref:System.Windows.Forms.Control.Padding%2A> la propriété du contrôle et des valeurs de propriété du formulaire.

   > [!NOTE]
   > Si la propriété du <xref:System.Windows.Forms.Control.Padding%2A> formulaire est définie sur 0, 0, 0, 0, le Concepteur Windows Forms donne à la forme une <xref:System.Windows.Forms.Control.Padding%2A> valeur ombrée de 9, 9, 9. Pour remplacer ce comportement, assignez une valeur différente de 0, 0, 0, 0.

2. Modifiez la valeur de la <xref:System.Windows.Forms.Button> propriété du <xref:System.Windows.Forms.Control.Margin%2A> contrôle en développant <xref:System.Windows.Forms.Control.Margin%2A> l’entrée dans la fenêtre **Propriétés** et en <xref:System.Windows.Forms.Padding.All%2A> affectant à la propriété la valeur 0. Pour plus d’informations [, consultez Procédure pas à pas: Disposition des contrôles Windows Forms avec le remplissage, les marges et la propriété](windows-forms-controls-padding-autosize.md)AutoSize.

3. Déplacez le <xref:System.Windows.Forms.Button> contrôle à proximité de la bordure droite du formulaire jusqu’à ce qu’une ligne d’alignement apparaisse. Cette distance est maintenant donnée par la valeur de la propriété du <xref:System.Windows.Forms.Control.Padding%2A> formulaire.

4. Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **boîte à outils** vers le formulaire.

5. Modifiez la valeur de la <xref:System.Windows.Forms.GroupBox> propriété du <xref:System.Windows.Forms.Control.Padding%2A> contrôle en développant <xref:System.Windows.Forms.Control.Padding%2A> l’entrée dans la fenêtre **Propriétés** et en <xref:System.Windows.Forms.Padding.All%2A> affectant à la propriété la valeur 10.

6. Faites glisser <xref:System.Windows.Forms.Button> un contrôle de la **boîte à outils** vers le <xref:System.Windows.Forms.GroupBox> contrôle.

7. Déplacez le <xref:System.Windows.Forms.Button> contrôle à proximité de la bordure droite <xref:System.Windows.Forms.GroupBox> du contrôle jusqu’à ce qu’une ligne d’alignement apparaisse. Déplacez le <xref:System.Windows.Forms.Button> contrôle dans le <xref:System.Windows.Forms.GroupBox> contrôle et notez où les lignes d’alignement apparaissent.

## <a name="align-to-grouped-controls"></a>Aligner sur les contrôles groupés

Vous pouvez utiliser des lignes d’alignement pour aligner les contrôles groupés et les <xref:System.Windows.Forms.GroupBox> contrôles dans un contrôle.

1. Sélectionnez deux des contrôles de votre formulaire. Déplacez la sélection autour et notez les lignes d’alignement qui apparaissent entre votre sélection et les autres contrôles.

2. Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **boîte à outils** vers le formulaire.

3. Faites glisser <xref:System.Windows.Forms.Button> un contrôle de la **boîte à outils** vers le <xref:System.Windows.Forms.GroupBox> contrôle.

4. Sélectionnez l’un des <xref:System.Windows.Forms.Button> contrôles et déplacez-le autour <xref:System.Windows.Forms.GroupBox> du contrôle. Notez les lignes d’alignement qui apparaissent aux bords du <xref:System.Windows.Forms.GroupBox> contrôle. Notez également les lignes d’alignement qui apparaissent aux bords du <xref:System.Windows.Forms.Button> contrôle contenu dans le <xref:System.Windows.Forms.GroupBox> contrôle. Les contrôles qui sont des enfants d’un contrôle conteneur prennent également en charge les lignes d’alignement.

## <a name="use-snaplines-to-place-a-control-by-outlining-its-size"></a>Utilisez des lignes d’alignement pour placer un contrôle en soulignant sa taille

1. Dans la **boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> . Ne la faites pas glisser sur le formulaire.

2. Placez le pointeur de la souris sur l’aire de conception du formulaire. Notez que le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.Button> . Notez également les lignes d’alignement qui apparaissent pour suggérer des positions <xref:System.Windows.Forms.Button> alignées pour le contrôle.

3. Cliquez et maintenez le bouton de la souris enfoncé.

4. Faites glisser le pointeur de la souris autour du formulaire. Notez qu’un contour est dessiné, indiquant la position et la taille du contrôle.

5. Faites glisser le pointeur jusqu’à ce qu’il s’aligne avec un autre contrôle sur le formulaire. Notez qu’une ligne d’alignement s’affiche pour indiquer l’alignement.

6. Relâchez le bouton de la souris. Le contrôle est créé à la position et à la taille indiquées par le plan.

## <a name="use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Utiliser des lignes d’alignement quand vous faites glisser un contrôle à partir de la boîte à outils

1. Faites glisser <xref:System.Windows.Forms.Button> un contrôle de la **boîte à outils** vers votre formulaire, mais ne relâchez pas le bouton de la souris.

2. Placez le pointeur de la souris sur l’aire de conception du formulaire. Notez que le pointeur change pour indiquer la position à laquelle le nouveau <xref:System.Windows.Forms.Button> contrôle sera créé.

3. Faites glisser le pointeur de la souris autour du formulaire. Notez les lignes d’alignement qui apparaissent pour suggérer des positions <xref:System.Windows.Forms.Button> alignées pour le contrôle. Recherche une position qui est alignée avec d’autres contrôles.

4. Relâchez le bouton de la souris. Le contrôle est créé à l’emplacement indiqué par les lignes d’alignement (SnapLines).

## <a name="resize-a-control-using-snaplines"></a>Redimensionner un contrôle à l’aide de lignes d’alignement

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.

2. Redimensionnez <xref:System.Windows.Forms.Button> le contrôle en saisissant l’une des poignées de redimensionnement d’angle et en la faisant glisser. Pour plus d’informations, consultez [Guide pratique pour Redimensionnez les contrôles](how-to-resize-controls-on-windows-forms.md)sur Windows Forms.

3. Faites glisser la poignée de redimensionnement <xref:System.Windows.Forms.Button> jusqu’à ce que l’une des bordures du contrôle soit alignée sur un autre contrôle. Notez qu’une ligne d’alignement (SnapLine) s’affiche. Notez également que la poignée de redimensionnement s’aligne à la position indiquée par la ligne d’alignement (SnapLine).

4. Redimensionner <xref:System.Windows.Forms.Button> le contrôle dans différentes directions et aligner la poignée de redimensionnement sur différents contrôles. Notez comment les lignes d’alignement apparaissent dans différentes orientations pour indiquer l’alignement.

## <a name="align-a-label-to-a-controls-text"></a>Aligner une étiquette sur le texte d’un contrôle

1. Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> de la **boîte à outils** vers le formulaire. Lorsque vous déposez le <xref:System.Windows.Forms.TextBox> contrôle sur le formulaire, cliquez sur le glyphe de balise active et sélectionnez l’option définir le **texte sur TextBox1** . Pour plus d’informations [, consultez Procédure pas à pas: Exécution de tâches courantes à l’aide de balises actives sur des contrôles](performing-common-tasks-using-smart-tags-on-wf-controls.md)Windows Forms.

2. Faites glisser un contrôle <xref:System.Windows.Forms.Label> de la **boîte à outils** vers le formulaire.

3. Affectez la valeur <xref:System.Windows.Forms.Label> à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle `true`. Notez que les bordures du contrôle sont ajustées pour s’ajuster au texte d’affichage.

4. Déplacez le <xref:System.Windows.Forms.Label> contrôle vers la gauche <xref:System.Windows.Forms.TextBox> du contrôle, afin qu’il soit aligné avec <xref:System.Windows.Forms.TextBox> le bord inférieur du contrôle. Notez la ligne d’alignement (SnapLine) qui apparaît le long des bords inférieurs des deux contrôles.

5. Déplacez légèrement <xref:System.Windows.Forms.Label> le contrôle vers le haut, <xref:System.Windows.Forms.Label> jusqu’à ce <xref:System.Windows.Forms.TextBox> que le texte et le texte soient alignés. Notez la ligne d’alignement (SnapLine) stylisée différente qui apparaît, indiquant quand les champs de texte des deux contrôles sont alignés.

## <a name="use-snaplines-with-keyboard-navigation"></a>Utiliser des lignes d’alignement avec la navigation au clavier

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire. Placez-le dans le coin supérieur gauche du formulaire.

2. Appuyez sur **CTRL**+**bas**. Notez que le contrôle descend le formulaire jusqu’à la première position d’alignement horizontal disponible.

3. Appuyez sur la **touche Ctrl**+enfoncée jusqu’à ce que le contrôle atteigne le bas du formulaire. Notez les positions qu’il occupe au fur et à mesure qu’il descend dans le formulaire.

4. Appuyez sur **CTRL**+**droite**. Notez que le contrôle se déplace dans le formulaire jusqu’à la première position d’alignement verticale disponible.

5. Appuyez sur **CTRL**+**droite** jusqu’à ce que le contrôle atteigne le côté du formulaire. Notez les positions qu’il occupe lorsqu’il se déplace dans le formulaire.

6. Déplacez le contrôle autour du formulaire à l’aide d’une combinaison de touches de direction. Notez les positions que le contrôle occupe et les lignes d’alignement (SnapLines) qui les accompagnent.

7. Appuyez sur les touches **MAJ**+**flèche** pour redimensionner le <xref:System.Windows.Forms.Button> contrôle par incréments d’un pixel.

8. Appuyez sur **CTRL**+**MAJ**+**touches fléchées** pour redimensionner le contrôle dans les <xref:System.Windows.Forms.Button> incréments de ligne d’alignement.

## <a name="selectively-disable-snaplines"></a>Désactiver de manière sélective les lignes d’alignement

1. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

2. Double-cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> dans la **boîte à outils**. Notez qu’un nouveau contrôle bouton s’affiche dans <xref:System.Windows.Forms.TableLayoutPanel> la première cellule du contrôle.

3. Double-cliquez sur <xref:System.Windows.Forms.Button> l’icône de contrôle dans la **boîte à outils** à deux reprises. Cela laisse une cellule vide dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôle.

4. Faites glisser <xref:System.Windows.Forms.Button> un contrôle de la **boîte à outils** vers la cellule <xref:System.Windows.Forms.TableLayoutPanel> vide du contrôle. Notez qu’aucune lignes d’alignement n’apparaît.

5. Faites glisser <xref:System.Windows.Forms.Button> le contrôle hors <xref:System.Windows.Forms.TableLayoutPanel> du contrôle et déplacez-le autour <xref:System.Windows.Forms.TableLayoutPanel> du contrôle. Notez que les lignes d’alignement s’affichent à nouveau.

## <a name="disable-snaplines"></a>Désactiver les lignes d’alignement

Appuyez sur la touche **ALT** et tout en déplaçant un contrôle dans le formulaire.

Aucune lignes d’alignement n’apparaît et le contrôle n’est pas aligné sur les positions d’alignement potentielles.

### <a name="to-disable-snaplines-in-the-design-environment"></a>Pour désactiver les lignes d’alignement dans l’environnement de conception

1. Dans le menu **Outils** , ouvrez la boîte de dialogue **options** . Sélectionnez **Concepteur Windows Forms**.

2. Sélectionnez le nœud **général** . Dans la section **mode disposition** , remplacez la sélection **lignes d’alignement (SnapLines)** par **SnapToGrid**.

3. Sélectionnez **OK** pour appliquer le paramètre.

4. Sélectionnez un contrôle dans votre formulaire et déplacez-le autour des autres contrôles. Notez que les lignes d’alignement n’apparaissent pas.

## <a name="next-steps"></a>Étapes suivantes

Les lignes d’alignement (SnapLines) offrent un moyen intuitif d’aligner les contrôles sur votre formulaire. Suggestions pour des recherches approfondies :

- Essayez d’imbriquer un <xref:System.Windows.Forms.GroupBox> contrôle dans un autre <xref:System.Windows.Forms.GroupBox> contrôle. Placez un <xref:System.Windows.Forms.Button> contrôle dans le contrôle <xref:System.Windows.Forms.GroupBox> enfant, et un autre dans le <xref:System.Windows.Forms.GroupBox> contrôle parent. Déplacez les <xref:System.Windows.Forms.Button> contrôles pour voir comment les lignes d’alignement croisent les limites des conteneurs.

- Créez une colonne de <xref:System.Windows.Forms.TextBox> contrôles et une colonne correspondante de <xref:System.Windows.Forms.Label> contrôles. Affectez la valeur à <xref:System.Windows.Forms.Label> `true`la <xref:System.Windows.Forms.Control.AutoSize%2A> propriété des contrôles. Utilisez des lignes d’alignement <xref:System.Windows.Forms.Label> pour déplacer les contrôles afin que le texte affiché soit aligné avec <xref:System.Windows.Forms.TextBox> le texte des contrôles.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Procédure pas à pas : Réorganisation des contrôles sur Windows Forms à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : Disposition des contrôles Windows Forms avec le remplissage, les marges et la propriété AutoSize](windows-forms-controls-padding-autosize.md)
