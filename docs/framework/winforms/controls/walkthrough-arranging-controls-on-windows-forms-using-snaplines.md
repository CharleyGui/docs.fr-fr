---
title: 'Procédure pas à pas : organisation des contrôles dans des Windows Forms à l’aide de lignes d’alignement'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
ms.openlocfilehash: c91fecf9e786f4a8e35486e7b30e9efe36c972e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771644"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Procédure pas à pas : organisation des contrôles dans des Windows Forms à l’aide de lignes d’alignement
Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications. Le Concepteur de formulaires Windows offre de nombreux outils de disposition pour effectuer cette opération. Une des plus importantes est la <xref:System.Windows.Forms.Design.Behavior.SnapLine> fonctionnalité.  
  
 Les lignes d’alignement vous indiquent précisément où aligner des contrôles avec d’autres contrôles. Ils indiquent également les distances recommandées pour les marges entre les contrôles, comme spécifié par les indications d’Interface utilisateur Windows. Pour plus d’informations, consultez [développement et conception de l’Interface utilisateur](https://go.microsoft.com/FWLink/?LinkId=83878).  
  
 Les lignes d’alignement facilitent aligner vos contrôles pour crisp, professionnels apparence et le comportement (aspect).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
- Création d’un projet Windows Forms  
  
- Espacement et alignement des contrôles à l’aide des lignes d’alignement  
  
- Alignement sur le formulaire et les marges de conteneur  
  
- Alignement des contrôles groupés  
  
- À l’aide des lignes d’alignement pour placer un contrôle en définissant sa taille  
  
- À l’aide des lignes d’alignement lorsque vous faites glisser un contrôle à partir de la boîte à outils  
  
- Redimensionnement de contrôles à l’aide des lignes d’alignement  
  
- Alignement d’une étiquette de texte d’un contrôle  
  
- À l’aide des lignes d’alignement avec la Navigation au clavier  
  
- Les lignes d’alignement et de panneaux de disposition  
  
- Désactiver les lignes d’alignement  
  
 Lorsque vous avez terminé, vous devez comprendre le rôle de disposition joué par la fonctionnalité de lignes d’alignement.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
### <a name="to-create-the-project"></a>Pour créer le projet  
  
1. Créer un projet d’application Windows appelé « SnaplineExample » (**fichier** > **New** > **projet**  >  **Visual C#** ou **Visual Basic** > **bureau classique** > **Windows Forms Application**).  
  
2. Sélectionnez le formulaire dans le Concepteur de formulaires.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>Espacement et alignement des contrôles à l’aide des lignes d’alignement  
 Les lignes d’alignement vous donnent un moyen précis et intuitif pour aligner des contrôles sur votre formulaire. Elles apparaissent lorsque vous déplacez un ou plusieurs contrôles sélectionnés près d’une position qui serait aligner avec un autre contrôle ou un ensemble de contrôles. Votre sélection se « aligne » à la position suggérée que vous dépassez les autres contrôles.  
  
### <a name="to-arrange-controls-using-snaplines"></a>Pour réorganiser des contrôles à l’aide des lignes d’alignement  
  
1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.  
  
2. Déplacer le <xref:System.Windows.Forms.Button> contrôle vers le coin inférieur droit du formulaire. Notez les lignes d’alignement apparaissent sous la forme la <xref:System.Windows.Forms.Button> contrôle approche les bordures inférieure et droite du formulaire. Ces lignes d’alignement affichent la distance recommandée entre les bordures du contrôle et le formulaire.  
  
3. Déplacer le <xref:System.Windows.Forms.Button> contrôle autour des bordures du formulaire et notez où les lignes d’alignement apparaissent. Lorsque vous avez terminé, déplacez le <xref:System.Windows.Forms.Button> contrôle près du centre du formulaire.  
  
4. Faites glisser un autre <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
5. Déplacer le second <xref:System.Windows.Forms.Button> contrôler jusqu'à ce qu’il soit presque au niveau du premier. Notez la ligne d’alignement qui apparaît au niveau de la ligne de base du texte des deux boutons et notez que le contrôle que vous déplacez s’aligne à une position qui est exactement au niveau de l’autre contrôle.  
  
6. Déplacer le second <xref:System.Windows.Forms.Button> contrôler jusqu'à ce qu’il est placé directement au-dessus du premier. Notez les lignes d’alignement qui apparaissent sur les bords gauche et droit des deux boutons et notez que le contrôle vous déplacez s’aligne à une position qui est alignée exactement avec l’autre contrôle.  
  
7. Sélectionnez une de la <xref:System.Windows.Forms.Button> contrôle et déplacez-le proche de l’autre, jusqu'à ce qu’ils se touchent presque. Notez la ligne d’alignement qui apparaît entre eux. Cette distance est la distance recommandée entre les bordures des contrôles. Notez également que le contrôle que vous déplacez s’aligne à cette position.  
  
8. Faites glisser deux <xref:System.Windows.Forms.Panel> des contrôles de la **boîte à outils** vers votre formulaire.  
  
9. Déplacez l’un de la <xref:System.Windows.Forms.Panel> contrôle jusqu'à ce qu’il soit presque au niveau du premier. Notez les lignes d’alignement qui apparaissent sur les bords supérieur et inférieur de ces deux contrôles et notez que le contrôle que vous déplacez s’aligne à une position qui est exactement au niveau de l’autre contrôle.  
  
## <a name="aligning-to-form-and-container-margins"></a>Alignement sur le formulaire et les marges de conteneur  
 Les lignes d’alignement vous aident à aligner vos contrôles aux marges de formulaire et le conteneur de manière cohérente.  
  
### <a name="to-align-controls-to-form-and-container-margins"></a>Pour aligner des contrôles pour les marges de formulaires et de conteneurs  
  
1. Sélectionnez une de la <xref:System.Windows.Forms.Button> contrôle et déplacez-le proche de la bordure droite du formulaire jusqu'à ce qu’une ligne d’alignement apparaît. Distance de la ligne d’alignement à partir de la bordure droite est la somme du contrôle <xref:System.Windows.Forms.Control.Margin%2A> propriété et du formulaire <xref:System.Windows.Forms.Control.Padding%2A> valeurs de propriété.  
  
> [!NOTE]
>  Si le formulaire <xref:System.Windows.Forms.Control.Padding%2A> propriété a la valeur 0,0,0,0, le Concepteur de formulaires Windows permet au formulaire d’un élément occulté <xref:System.Windows.Forms.Control.Padding%2A> valeur 9,9,9,9. Pour remplacer ce comportement, affectez une valeur autre que 0,0,0,0.  
  
1. Modifiez la valeur de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Margin%2A> en développant le <xref:System.Windows.Forms.Control.Margin%2A> entrée dans le **propriétés** fenêtre et en définissant le <xref:System.Windows.Forms.Padding.All%2A> 0 à la propriété. Pour plus d’informations, consultez [procédure pas à pas : Disposition des Windows Forms contrôles avec les propriétés Padding, marges et la propriété AutoSize](windows-forms-controls-padding-autosize.md).  
  
2. Déplacer le <xref:System.Windows.Forms.Button> contrôle proche de la bordure droite du formulaire jusqu'à ce qu’une ligne d’alignement apparaît. Cette distance est désormais fournie par la valeur de la forme <xref:System.Windows.Forms.Control.Padding%2A> propriété.  
  
3. Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **boîte à outils** vers le formulaire.  
  
4. Modifiez la valeur de la <xref:System.Windows.Forms.GroupBox> du contrôle <xref:System.Windows.Forms.Control.Padding%2A> en développant le <xref:System.Windows.Forms.Control.Padding%2A> entrée dans le **propriétés** fenêtre et en définissant le <xref:System.Windows.Forms.Padding.All%2A> propriété à 10.  
  
5. Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** dans le <xref:System.Windows.Forms.GroupBox> contrôle.  
  
6. Déplacer le <xref:System.Windows.Forms.Button> contrôle proche de la bordure droite de la <xref:System.Windows.Forms.GroupBox> contrôler jusqu'à ce qu’une ligne d’alignement apparaît. Déplacer le <xref:System.Windows.Forms.Button> contrôler au sein de la <xref:System.Windows.Forms.GroupBox> contrôle et notez où les lignes d’alignement apparaissent.  
  
## <a name="aligning-to-grouped-controls"></a>Alignement des contrôles groupés  
 Vous pouvez utiliser les lignes d’alignement pour aligner des contrôles groupés ainsi que des contrôles dans un <xref:System.Windows.Forms.GroupBox> contrôle.  
  
### <a name="to-align-to-grouped-controls"></a>Pour aligner des contrôles groupés  
  
1. Sélectionnez deux contrôles sur votre formulaire. Déplacer la sélection et notez les lignes d’alignement qui apparaissent entre votre sélection et les autres contrôles.  
  
2. Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **boîte à outils** vers le formulaire.  
  
3. Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** dans le <xref:System.Windows.Forms.GroupBox> contrôle.  
  
4. Sélectionnez une de la <xref:System.Windows.Forms.Button> contrôle et déplacez-le sur le <xref:System.Windows.Forms.GroupBox> contrôle. Notez les lignes d’alignement qui apparaissent sur les bords de la <xref:System.Windows.Forms.GroupBox> contrôle. Notez également les lignes d’alignement qui apparaissent sur les bords de la <xref:System.Windows.Forms.Button> contrôle contenu par le <xref:System.Windows.Forms.GroupBox> contrôle. Les contrôles qui sont des enfants d’un contrôle conteneur prennent également en charge les lignes d’alignement.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>À l’aide des lignes d’alignement pour placer un contrôle en définissant sa taille  
 Les lignes d’alignement vous aident à qu'aligner contrôle quand vous placez d’abord les sur un formulaire.  
  
### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Pour utiliser les lignes d’alignement pour placer un contrôle en définissant sa taille  
  
1. Dans la **boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> . Ne la faites pas glisser sur le formulaire.  
  
2. Déplacez le pointeur de la souris sur l’aire de conception du formulaire. Notez que le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.Button> . Notez également les lignes d’alignement qui apparaissent pour suggérer des positions alignées pour le <xref:System.Windows.Forms.Button> contrôle.  
  
3. Cliquez et maintenez le bouton de la souris enfoncé.  
  
4. Faites glisser le pointeur de la souris autour du formulaire. Notez qu’un plan est dessiné, indiquant la position et la taille du contrôle.  
  
5. Faites glisser le pointeur jusqu'à ce qu’il s’aligne sur un autre contrôle sur le formulaire. Notez qu’une ligne d’alignement apparaît pour indiquer l’alignement.  
  
6. Relâchez le bouton de la souris. Le contrôle est créé à la position et la taille indiquées par le plan.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>À l’aide des lignes d’alignement lorsque vous faites glisser un contrôle à partir de la boîte à outils  
 Les lignes d’alignement vous aident à aligner contrôle lorsque vous les faites glisser à partir de la **boîte à outils** vers votre formulaire.  
  
### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Pour utiliser les lignes d’alignement lorsque vous faites glisser un contrôle à partir de la boîte à outils  
  
1. Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire, mais ne relâchez pas le bouton de la souris.  
  
2. Déplacez le pointeur de la souris sur l’aire de conception du formulaire. Notez que le pointeur change pour indiquer la position à laquelle la nouvelle <xref:System.Windows.Forms.Button> contrôle sera créé.  
  
3. Faites glisser le pointeur de la souris autour du formulaire. Notez les lignes d’alignement qui apparaissent pour suggérer des positions alignées pour le <xref:System.Windows.Forms.Button> contrôle. Rechercher une position qui est alignée avec d’autres contrôles.  
  
4. Relâchez le bouton de la souris. Le contrôle est créé à la position indiquée par les lignes d’alignement.  
  
## <a name="resizing-controls-using-snaplines"></a>Redimensionnement de contrôles à l’aide des lignes d’alignement  
 Les lignes d’alignement vous aident à aligner des contrôles lorsque vous les redimensionnez.  
  
### <a name="to-resize-a-control-using-snaplines"></a>Pour redimensionner un contrôle à l’aide des lignes d’alignement  
  
1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire.  
  
2. Redimensionner le <xref:System.Windows.Forms.Button> contrôle en saisissant l’une des poignées de redimensionnement et en faisant glisser. Pour plus d’informations, consultez [Guide pratique pour Redimensionner des contrôles dans les Windows Forms](how-to-resize-controls-on-windows-forms.md).  
  
3. Faites glisser la poignée de redimensionnement jusqu'à ce qu’un de la <xref:System.Windows.Forms.Button> bordures du contrôle est aligné avec un autre contrôle. Notez qu’une ligne d’alignement apparaît. Notez également que la poignée de redimensionnement s’aligne à la position indiquée par la ligne d’alignement.  
  
4. Redimensionner le <xref:System.Windows.Forms.Button> contrôler dans différentes directions et alignez la poignée de dimensionnement aux différents contrôles. Notez comment les lignes d’alignement apparaissent dans différentes orientations pour indiquer l’alignement.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Alignement d’une étiquette de texte d’un contrôle  
 Certains contrôles offrent une ligne d’alignement pour aligner les autres contrôles au texte affiché.  
  
### <a name="to-align-a-label-to-a-controls-text"></a>Pour aligner une étiquette pour le texte d’un contrôle  
  
1. Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> de la **boîte à outils** vers le formulaire. Lorsque vous déposez le <xref:System.Windows.Forms.TextBox> contrôle vers le formulaire, cliquez sur le glyphe de balise active et sélectionnez le **la valeur texte textBox1** option. Pour plus d’informations, consultez [procédure pas à pas : Effectuer des tâches courantes à l’aide de balises actives sur les Windows Forms contrôles](performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2. Faites glisser un contrôle <xref:System.Windows.Forms.Label> de la **boîte à outils** vers le formulaire.  
  
3. Affectez la valeur <xref:System.Windows.Forms.Label> à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle `true`. Notez que les bordures du contrôle sont ajustées pour s’adapter au texte d’affichage.  
  
4. Déplacer le <xref:System.Windows.Forms.Label> contrôle vers la gauche de la <xref:System.Windows.Forms.TextBox> contrôler, afin qu’il est aligné avec le bord inférieur de la <xref:System.Windows.Forms.TextBox> contrôle. Notez la ligne d’alignement qui apparaît le long des bords des contrôles en bas.  
  
5. Déplacer le <xref:System.Windows.Forms.Label> contrôle légèrement pointant vers le haut, jusqu'à ce que le <xref:System.Windows.Forms.Label> texte et la <xref:System.Windows.Forms.TextBox> texte sont alignées. Notez la ligne d’alignement différemment de style qui s’affiche, indiquant quand les champs de texte des deux contrôles sont alignés.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>À l’aide des lignes d’alignement avec la Navigation au clavier  
 Les lignes d’alignement vous aident à qu'aligner contrôle lorsque vous les réorganisez à l’aide des touches de direction du clavier.  
  
### <a name="to-use-snaplines-with-keyboard-navigation"></a>Pour utiliser les lignes d’alignement avec la navigation au clavier  
  
1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le formulaire. Placez-le dans le coin supérieur gauche du formulaire.  
  
2. Appuyez sur CTRL + flèche bas. Notez que le contrôle se déplace vers le bas du formulaire à la première position d’alignement horizontal disponible.  
  
3. Appuyez sur CTRL + flèche bas jusqu'à ce que le contrôle atteint le bas du formulaire. Notez les positions qu’il occupe lors de leur déplacement vers le bas du formulaire.  
  
4. Appuyez sur CTRL + flèche droite. Notez que le contrôle se trouve sur le formulaire à la première position d’alignement vertical disponibles.  
  
5. Appuyez sur CTRL + flèche droite jusqu'à ce que le contrôle atteigne le côté du formulaire. Notez les positions qu’il occupe comme il se trouve sur le formulaire.  
  
6. Déplacez le contrôle autour du formulaire avec une combinaison de touches de direction. Notez les positions occupées par le contrôle et les lignes d’accrochage qui les accompagnent.  
  
7. Appuyez sur MAJ + touches de direction pour redimensionner le <xref:System.Windows.Forms.Button> contrôle par incréments d’un pixel.  
  
8. Appuyez sur CTRL + MAJ + touches de direction pour redimensionner le <xref:System.Windows.Forms.Button> contrôle par incréments de ligne d’alignement.  
  
## <a name="snaplines-and-layout-panels"></a>Les lignes d’alignement et de panneaux de disposition  
 Les lignes d’alignement sont désactivés dans les panneaux de disposition.  
  
### <a name="to-selectively-disable-snaplines"></a>Pour désactiver de manière sélective les lignes d’alignement  
  
1. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.  
  
2. Double-cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> dans la **boîte à outils**. Notez qu’un nouveau contrôle de bouton s’affiche dans le <xref:System.Windows.Forms.TableLayoutPanel> première cellule du contrôle.  
  
3. Double-cliquez sur le <xref:System.Windows.Forms.Button> icône de contrôle dans le **boîte à outils** deux fois plus. Cela laisse une cellule vide dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôle.  
  
4. Faites glisser un <xref:System.Windows.Forms.Button> contrôler à partir de la **boîte à outils** dans la cellule vide de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Notez qu’aucune ligne d’alignement n’apparaître.  
  
5. Faites glisser le <xref:System.Windows.Forms.Button> contrôler hors le <xref:System.Windows.Forms.TableLayoutPanel> contrôle et déplacez-le sur le <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Notez que les lignes d’alignement apparaissent à nouveau.  
  
## <a name="disabling-snaplines"></a>Désactiver les lignes d’alignement  
 Les lignes d’alignement sont activées par défaut. Vous pouvez désactiver sélectivement les lignes d’alignement, ou vous pouvez les désactiver dans l’environnement de conception.  
  
### <a name="to-selectively-disable-snaplines"></a>Pour désactiver de manière sélective les lignes d’alignement  
  
- Appuyez sur la touche ALT et tout en déplaçant un contrôle autour du formulaire.  
  
     Notez que sans les lignes d’alignement apparaissent et que le contrôle ne s’aligne sur les positions d’alignement potentielles.  
  
### <a name="to-disable-snaplines-in-the-design-environment"></a>Pour désactiver les lignes d’alignement dans l’environnement de conception  
  
1. À partir de la **outils** menu, ouvrez le **Options** boîte de dialogue. Ouvrez la boîte de dialogue Windows Forms Designer. Pour plus d’informations, consultez [général, le Concepteur Windows Forms, boîte de dialogue Options](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100)).  
  
2. Sélectionnez le **général** nœud. Dans le **Mode disposition** section, changez la sélection de **les lignes d’alignement** à **SnapToGrid**.  
  
3. Cliquez sur OK pour appliquer le paramètre.  
  
4. Sélectionnez un contrôle sur votre formulaire et déplacez-le sur les autres contrôles. Notez que les lignes d’alignement n’apparaissent pas.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Les lignes d’alignement offrent un moyen intuitif de l’alignement des contrôles sur votre formulaire. Suggestions pour des recherches approfondies :  
  
- Essayez d’imbriquer un <xref:System.Windows.Forms.GroupBox> contrôle dans une autre <xref:System.Windows.Forms.GroupBox> contrôle. Place un <xref:System.Windows.Forms.Button> contrôle au sein de l’enfant <xref:System.Windows.Forms.GroupBox> contrôle et l’autre dans le parent <xref:System.Windows.Forms.GroupBox> contrôle. Déplacer le <xref:System.Windows.Forms.Button> contrôles autour pour voir comment les lignes d’accrochage franchissent les limites du conteneur.  
  
- Créer une colonne de <xref:System.Windows.Forms.TextBox> contrôles et une colonne correspondante de <xref:System.Windows.Forms.Label> contrôles. Définissez la valeur de la <xref:System.Windows.Forms.Label> contrôles <xref:System.Windows.Forms.Control.AutoSize%2A> propriété `true`. Permet de déplacer les lignes d’alignement le <xref:System.Windows.Forms.Label> contrôle afin que leur texte affiché est aligné avec le texte dans le <xref:System.Windows.Forms.TextBox> contrôles.  
  
 Pour plus d’informations sur la conception de l’interface utilisateur Windows, consultez le livre *Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers* Redmond, Washington : Microsoft Press, 1999. (USBN : 0-7356-0566-1).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Design.Behavior.SnapLine>
- [Procédure pas à pas : Organisation des contrôles dans les formulaires de Windows à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Procédure pas à pas : Organisation des contrôles dans les formulaires de Windows à l’aide d’un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : Disposition des Windows Forms contrôles avec la propriété AutoSize, des marges et remplissage](windows-forms-controls-padding-autosize.md)
- [Disposition des contrôles dans les Windows Forms](arranging-controls-on-windows-forms.md)
