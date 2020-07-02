---
title: Organiser les contrôles à l’aide de FlowLayoutPanel
description: Apprenez à utiliser le contrôle FlowLayoutPanel et le contrôle TableLayoutPanel pour fournir des méthodes intuitives pour organiser les contrôles dans votre projet Windows Forms.
ms.date: 03/30/2017
helpviewer_keywords:
- FlowLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
- controls [Windows Forms], arranging with FlowLayoutPanel
- layout [Windows Forms], walkthroughs
ms.assetid: a1744323-0316-49c2-992e-ebfc0a976b85
ms.openlocfilehash: efcb38275be7b0cf94afb6b68aa139876f7cf5fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619284"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel"></a>Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un FlowLayoutPanel

Certaines applications exigent un formulaire dont la disposition s’organise de manière appropriée à mesure que le formulaire est redimensionné ou que le contenu change de taille. Si vous avez besoin d’une disposition dynamique et que vous ne souhaitez pas gérer les événements <xref:System.Windows.Forms.Control.Layout> explicitement dans votre code, envisagez d’utiliser un panneau de disposition.

Les contrôles <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel> vous permettent d’organiser de manière intuitive les contrôles sur votre formulaire. Tous deux vous permettent de contrôler automatiquement et de configurer la position relative des contrôles enfants qu’ils contiennent, et l’un et l’autre proposent des fonctionnalités de disposition dynamique au moment de l’exécution qui leur permettent de redimensionner et repositionner les contrôles enfants à mesure que les dimensions du formulaire parent changent. Les panneaux de disposition peuvent être imbriqués dans d’autres panneaux de disposition, ce qui permet de créer des interfaces utilisateur sophistiquées.

<xref:System.Windows.Forms.TableLayoutPanel>Réorganise son contenu dans une grille, en fournissant des fonctionnalités similaires à celles de l' \<table> élément HTML. Ses cellules sont organisées dans des lignes et des colonnes dont la taille peut varier. Pour plus d'informations, consultez [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).

<xref:System.Windows.Forms.FlowLayoutPanel> organise son contenu dans un sens de flux spécifique : horizontal ou vertical. Vous pouvez encapsuler son contenu d'une ligne à la suivante ou d'une colonne à la suivante. Vous pouvez également découper son contenu au lieu de l'encapsuler. Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création d’un projet Windows Forms

- Organisation de contrôles dans le sens horizontal ou vertical

- Modification du sens du flux

- Insertion d’interruptions de flux

- Organisation des contrôles en utilisant le remplissage et les marges

- Insertion de contrôles en double-cliquant dessus dans la boîte à outils

- Insertion d’un contrôle en dessinant son contour

- Insertion de contrôles en utilisant le signe insertion

- Réassignation de contrôles existants à un parent différent

Lorsque vous aurez terminé, vous aurez une compréhension du rôle joué par ces fonctionnalités de disposition importantes.

## <a name="create-the-project"></a>Créer le projet

1. Dans Visual Studio, créez un projet d’application Windows nommé « FlowLayoutPanelExample » (**fichier**  >  **nouveau**  >  **projet**  >  **Visual C#** ou **Visual Basic**  >  application Windows Forms de**Bureau classique**  >  **Windows Forms Application**).

2. Sélectionnez le formulaire dans le **Concepteur de formulaires**.

## <a name="arranging-controls-horizontally-and-vertically"></a>Organisation de contrôles dans le sens horizontal ou vertical
 Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> vous permet de placer des contrôles le long des lignes ou des colonnes sans avoir à indiquer précisément la position de chacun d’eux.

 Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> peut redimensionner ou ajuster dynamiquement ses contrôles enfants à mesure que les dimensions du formulaire parent changent.

### <a name="to-arrange-controls-horizontally-and-vertically-using-a-flowlayoutpanel"></a>Pour organiser les contrôles dans les sens horizontal et vertical à l’aide d’un FlowLayoutPanel

1. Faites glisser un contrôle <xref:System.Windows.Forms.FlowLayoutPanel> de la **boîte à outils** vers le formulaire.

2. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le <xref:System.Windows.Forms.FlowLayoutPanel>. Notez qu’il se déplace automatiquement vers le coin supérieur gauche du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

3. Faites glisser un autre contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le <xref:System.Windows.Forms.FlowLayoutPanel>. Notez que le contrôle <xref:System.Windows.Forms.Button> se déplace automatiquement à proximité du contrôle <xref:System.Windows.Forms.Button> . Si votre <xref:System.Windows.Forms.FlowLayoutPanel> est trop étroit pour accueillir les deux contrôles sur la même ligne, le nouveau contrôle <xref:System.Windows.Forms.Button> se déplace automatiquement vers la ligne suivante.

4. Faites glisser plusieurs autres contrôles <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le <xref:System.Windows.Forms.FlowLayoutPanel>. Continuez à placer des contrôles <xref:System.Windows.Forms.Button> jusqu’à ce que l’un deux soit renvoyé à la ligne suivante.

5. Affectez la valeur <xref:System.Windows.Forms.FlowLayoutPanel> à la propriété <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> du contrôle `false`. Notez que les contrôles enfants ne passent plus à la ligne suivante. Au lieu de cela, ils sont déplacés dans la première ligne et détourés.

6. Affectez la valeur <xref:System.Windows.Forms.FlowLayoutPanel> à la propriété <xref:System.Windows.Forms.FlowLayoutPanel.WrapContents%2A> du contrôle `true`. Notez que les contrôles enfants sont à nouveau renvoyés à la ligne suivante.

7. Diminuez la largeur du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> jusqu’à ce que tous les contrôles <xref:System.Windows.Forms.Button> soient déplacés dans la première colonne.

8. Augmentez la largeur du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> jusqu’à ce que tous les contrôles <xref:System.Windows.Forms.Button> soient déplacés dans la première ligne. Vous devrez peut-être redimensionner votre formulaire pour l’adapter à l’élargissement.

## <a name="changing-flow-direction"></a>Modification du sens du flux
 La propriété <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> vous permet de modifier le sens dans lequel les contrôles sont organisés. Vous pouvez organiser les contrôles enfants de gauche à droite, de droite à gauche, de haut en bas ou de bas en haut.

### <a name="to-change-the-flow-direction-in-a-flowlayoutpanel"></a>Pour modifier le sens du flux dans un FlowLayoutPanel

1. Affectez la valeur <xref:System.Windows.Forms.FlowLayoutPanel> à la propriété <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> du contrôle <xref:System.Windows.Forms.FlowDirection.TopDown>. Notez que les contrôles enfants sont réorganisés en une ou plusieurs colonnes, selon la hauteur du contrôle.

2. Redimensionnez le <xref:System.Windows.Forms.FlowLayoutPanel> de telle sorte que sa hauteur soit inférieure à la colonne des contrôles <xref:System.Windows.Forms.Button> . Notez que le <xref:System.Windows.Forms.FlowLayoutPanel> réorganise les contrôles enfants pour les placer dans la colonne suivante. Continuez à diminuer la hauteur et notez que les contrôles enfants passent dans les colonnes successives. Affectez la valeur <xref:System.Windows.Forms.FlowLayoutPanel> à la propriété <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> du contrôle <xref:System.Windows.Forms.FlowDirection.RightToLeft>. Notez que la position des contrôles enfants est inversée. Observez la disposition quand vous affectez à la propriété <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> la valeur <xref:System.Windows.Forms.FlowDirection.BottomUp>.

## <a name="inserting-flow-breaks"></a>Insertion d’interruptions de flux
 Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> fournit une propriété FlowBreak à ses contrôles enfants. L'affectation de la valeur `true` à la propriété FlowBreak fait en sorte que le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> cesse de disposer les contrôles dans le sens du flux actuel et qu'il encapsule à la ligne ou la colonne suivante.

### <a name="to-insert-flow-breaks"></a>Pour insérer des interruptions de flux

1. Affectez la valeur <xref:System.Windows.Forms.FlowLayoutPanel> à la propriété <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> du contrôle <xref:System.Windows.Forms.FlowDirection.TopDown>.

2. Sélectionnez l’un des contrôles <xref:System.Windows.Forms.Button> au milieu de la colonne de gauche.

3. Affectez à la propriété FlowBreak du contrôle <xref:System.Windows.Forms.Button> la valeur `true`. Notez que la colonne fait l’objet d’un saut et que les contrôles à la suite du contrôle <xref:System.Windows.Forms.Button> sélectionné sont placés dans la colonne suivante. Affectez à la propriété FlowBreak du contrôle <xref:System.Windows.Forms.Button> la valeur `false` pour revenir au comportement d’origine.

## <a name="positioning-controls-using-docking-and-anchoring"></a>Positionnement des contrôles en utilisant l’ancrage
 Le comportement de l’ancrage au niveau des contrôles enfants diffère de celui observé dans les autres contrôles conteneurs. L’ancrage se fait par rapport au plus grand contrôle dans le sens du flux.

### <a name="to-position-controls-using-docking-and-anchoring"></a>Pour positionner les contrôles en utilisant l’ancrage

1. Augmentez la taille du <xref:System.Windows.Forms.FlowLayoutPanel> jusqu’à ce que les contrôles <xref:System.Windows.Forms.Button> soient tous organisés dans une colonne.

2. Sélectionnez le contrôle <xref:System.Windows.Forms.Button> du haut. Augmentez sa largeur de sorte qu’il soit deux fois plus large que les autres contrôles <xref:System.Windows.Forms.Button> .

3. Sélectionnez le deuxième contrôle <xref:System.Windows.Forms.Button> . Remplacez la valeur de sa propriété <xref:System.Windows.Forms.Control.Anchor%2A> par <xref:System.Windows.Forms.AnchorStyles.Right>. Notez qu’il est déplacé de sorte que sa bordure droite soit alignée sur la bordure droite du premier contrôle <xref:System.Windows.Forms.Button> .

4. Remplacez la valeur de sa propriété <xref:System.Windows.Forms.Control.Anchor%2A> par <xref:System.Windows.Forms.AnchorStyles.Right> et <xref:System.Windows.Forms.AnchorStyles.Left>. Notez que sa taille est calquée sur la largeur du premier contrôle <xref:System.Windows.Forms.Button> .

5. Sélectionnez le troisième contrôle <xref:System.Windows.Forms.Button> . Remplacez la valeur de sa propriété <xref:System.Windows.Forms.Control.Dock%2A> par <xref:System.Windows.Forms.DockStyle.Fill>. Notez que sa taille est calquée sur la largeur du premier contrôle <xref:System.Windows.Forms.Button> .

## <a name="arranging-controls-using-padding-and-margins"></a>Organisation des contrôles en utilisant le remplissage et les marges
 Vous pouvez aussi organiser les contrôles contenus dans le <xref:System.Windows.Forms.FlowLayoutPanel> en modifiant les propriétés <xref:System.Windows.Forms.Control.Padding%2A> et <xref:System.Windows.Forms.Control.Margin%2A> .

 La propriété <xref:System.Windows.Forms.Control.Padding%2A> vous permet de contrôler la position des contrôles dans une cellule du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> . Elle spécifie l’espacement entre les contrôles enfants et la bordure du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

 La propriété <xref:System.Windows.Forms.Control.Margin%2A> vous permet de contrôler l’espacement entre les contrôles.

### <a name="to-arrange-controls-using-the-padding-and-margin-properties"></a>Pour organiser les contrôles en utilisant les propriétés Padding et Margin

1. Affectez la valeur <xref:System.Windows.Forms.FlowLayoutPanel> à la propriété <xref:System.Windows.Forms.Control.Dock%2A> du contrôle <xref:System.Windows.Forms.DockStyle.Fill>. Si votre formulaire est suffisamment grand, les contrôles <xref:System.Windows.Forms.Button> se déplacent dans la première colonne du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

2. Modifiez la valeur de la propriété <xref:System.Windows.Forms.FlowLayoutPanel> du contrôle <xref:System.Windows.Forms.Control.Padding%2A> en développant l’entrée <xref:System.Windows.Forms.Control.Padding%2A> dans la fenêtre **Propriétés** et en affectant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur **20**. Pour plus d’informations, consultez [procédure pas à pas : disposition des contrôles Windows Forms avec le remplissage, les marges et la propriété AutoSize](windows-forms-controls-padding-autosize.md). Notez que les contrôles enfants se déplacent vers le centre du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> . La valeur augmentée de la propriété <xref:System.Windows.Forms.Control.Padding%2A> éloigne les contrôles enfants des bordures du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

3. Sélectionnez tous les contrôles <xref:System.Windows.Forms.Button> contenus dans le <xref:System.Windows.Forms.FlowLayoutPanel> et affectez à la propriété <xref:System.Windows.Forms.Control.Margin%2A> la valeur **20**. Notez que l’espacement entre les contrôles <xref:System.Windows.Forms.Button> augmente de façon à les écarter davantage. Vous devrez peut-être agrandir le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> pour voir tous les contrôles enfants.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Insertion de contrôles en double-cliquant dessus dans la boîte à outils
 Vous pouvez remplir votre contrôle <xref:System.Windows.Forms.FlowLayoutPanel> en double-cliquant sur des contrôles dans la **boîte à outils**.

### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Pour insérer des contrôles en double-cliquant dessus dans la boîte à outils

1. Double-cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> dans la **boîte à outils**. Notez qu’un nouveau contrôle <xref:System.Windows.Forms.Button> s’affiche dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

2. Double-cliquez sur plusieurs autres contrôles dans la **boîte à outils**. Notez que les nouveaux contrôles s’affichent successivement dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

## <a name="inserting-a-control-by-drawing-its-outline"></a>Insertion d’un contrôle en dessinant son contour
 Vous pouvez insérer un contrôle dans un contrôle <xref:System.Windows.Forms.FlowLayoutPanel> et spécifier sa taille en dessinant son contour dans une cellule.

### <a name="to-insert-a-control-by-drawing-its-outline"></a>Pour insérer un contrôle en dessinant son contour

1. Dans la **boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> . Ne la faites pas glisser sur le formulaire.

2. Placez le pointeur de la souris sur le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> . Notez que le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.Button> .

3. Cliquez et maintenez le bouton de la souris enfoncé.

4. Faites glisser le pointeur de la souris pour tracer le contour du contrôle <xref:System.Windows.Forms.Button> . Quand la taille vous convient, relâchez le bouton de la souris. Notez que le contrôle <xref:System.Windows.Forms.Button> est créé à l’emplacement ouvert suivant du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

## <a name="inserting-controls-using-the-insertion-bar"></a>Insertion de contrôles à l’aide de la barre d’insertion
 Vous pouvez insérer des contrôles à un emplacement déterminé à l’intérieur d’un contrôle <xref:System.Windows.Forms.FlowLayoutPanel> . Quand vous faites glisser un contrôle dans la zone cliente du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> , une barre d’insertion s’affiche pour indiquer là où le contrôle sera inséré.

### <a name="to-insert-a-control-using-the-caret"></a>Pour insérer un contrôle à l’aide du signe insertion

1. Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> et pointez sur l’espace qui sépare deux contrôles <xref:System.Windows.Forms.Button> . Notez qu’une barre d’insertion est dessinée, indiquant où le <xref:System.Windows.Forms.Button> sera placé lorsqu’il sera déposé dans le <xref:System.Windows.Forms.FlowLayoutPanel> contrôle. Avant de déposer le nouveau contrôle <xref:System.Windows.Forms.Button> dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> , déplacez le pointeur de la souris pour observer la façon dont la barre d’insertion se déplace.

2. Déposez le nouveau contrôle <xref:System.Windows.Forms.Button> dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> . Notez que le nouveau contrôle <xref:System.Windows.Forms.Button> n’est pas aligné sur les autres, car sa propriété <xref:System.Windows.Forms.Control.Margin%2A> a une valeur différente.

## <a name="reassigning-existing-controls-to-a-different-parent"></a>Réassignation de contrôles existants à un parent différent
 Vous pouvez assigner des contrôles existants de votre formulaire à un nouveau contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

### <a name="to-reparent-existing-controls"></a>Pour attribuer un nouveau parent aux contrôles existants

1. Faites glisser trois contrôles <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le formulaire. Disposez-les près les uns des autres en les laissant non alignés.

2. Dans la **boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> . Ne la faites pas glisser sur le formulaire.

3. Placez le pointeur de la souris près des trois contrôles <xref:System.Windows.Forms.Button> . Notez que le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

4. Cliquez et maintenez le bouton de la souris enfoncé.

5. Faites glisser le pointeur de la souris pour tracer le contour du contrôle <xref:System.Windows.Forms.FlowLayoutPanel> . Tracez le contour des trois contrôles <xref:System.Windows.Forms.Button> .

6. Relâchez le bouton de la souris. Notez que les trois contrôles <xref:System.Windows.Forms.Button> sont insérés dans le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> .

## <a name="next-steps"></a>Étapes suivantes
 Vous pouvez obtenir une disposition complexe en combinant plusieurs contrôles et panneaux de disposition. Suggestions pour des recherches approfondies :

- Agrandissez l’un des contrôles <xref:System.Windows.Forms.Button> et observez l’effet du redimensionnement sur la disposition.

- Les panneaux de disposition peuvent contenir d’autres panneaux de disposition. Faites l’expérience de déposer un contrôle <xref:System.Windows.Forms.TableLayoutPanel> dans le contrôle existant.

- Ancrez le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> au formulaire parent. Redimensionnez le formulaire et observez-en l’effet sur la disposition.

- Affectez à la propriété <xref:System.Windows.Forms.Control.Visible%2A> de l’un des contrôles la valeur `false` et observez la façon dont le <xref:System.Windows.Forms.FlowLayoutPanel> est réajusté en réponse.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement (SnapLines)](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Vue d'ensemble de la propriété AutoSize](autosize-property-overview.md)
- [Guide pratique pour fixer des contrôles sur des Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Guide pratique pour ancrer des contrôles sur des Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](windows-forms-controls-padding-autosize.md)
