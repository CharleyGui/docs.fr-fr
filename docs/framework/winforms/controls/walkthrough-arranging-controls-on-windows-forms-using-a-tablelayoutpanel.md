---
title: Organisation des contrôles à l’aide d’un TableLayoutPanel
description: Découvrez comment organiser les contrôles sur votre Windows Forms à l’aide du contrôle FlowLayoutPanel et du contrôle TableLayoutPanel.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
ms.openlocfilehash: 6dfc6dbdef38d635dc94877f79a8e3659295bd98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622794"
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel

Certaines applications exigent un formulaire dont la disposition s’organise de manière appropriée à mesure que le formulaire est redimensionné ou que le contenu change de taille. Si vous avez besoin d’une disposition dynamique et que vous ne souhaitez pas gérer les événements <xref:System.Windows.Forms.Control.Layout> explicitement dans votre code, envisagez d’utiliser un panneau de disposition.

Les contrôles <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel> vous permettent d’organiser de manière intuitive les contrôles sur votre formulaire. Tous deux vous permettent de contrôler automatiquement et de configurer la position relative des contrôles enfants qu’ils contiennent, et l’un et l’autre proposent des fonctionnalités de disposition dynamique au moment de l’exécution qui leur permettent de redimensionner et repositionner les contrôles enfants à mesure que les dimensions du formulaire parent changent. Les panneaux de disposition peuvent être imbriqués dans d’autres panneaux de disposition, ce qui permet de créer des interfaces utilisateur sophistiquées.

<xref:System.Windows.Forms.FlowLayoutPanel> organise son contenu dans un sens de flux spécifique : horizontal ou vertical. Vous pouvez encapsuler son contenu d'une ligne à la suivante ou d'une colonne à la suivante. Vous pouvez également découper son contenu au lieu de l'encapsuler. Pour plus d’informations, consultez [procédure pas à pas : Organisation des contrôles sur Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).

<xref:System.Windows.Forms.TableLayoutPanel>Réorganise son contenu dans une grille, en fournissant des fonctionnalités similaires à celles de l' \<table> élément HTML. Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle vous permet de placer des contrôles dans une disposition de grille sans vous obliger à spécifier précisément la position de chaque contrôle individuel. Ses cellules sont organisées dans des lignes et des colonnes dont la taille peut varier. Les cellules peuvent être fusionnées entre les lignes et les colonnes. Les cellules peuvent contenir tout ce qu’un formulaire peut contenir et se comporter dans la plupart des autres aspects en tant que conteneurs.

Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle fournit également une fonctionnalité de redimensionnement proportionnel au moment de l’exécution. votre disposition peut donc changer en douceur au fur et à mesure que votre formulaire est redimensionné. Cela rend le <xref:System.Windows.Forms.TableLayoutPanel> contrôle bien adapté à des fins telles que les formulaires de saisie de données et les applications localisées. Pour plus d’informations, consultez [procédure pas à pas : création d’un Windows Form redimensionnable pour l’entrée de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)) et [procédure pas à pas : création d’un Windows Form localisable](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).

En général, vous ne devez pas utiliser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle comme conteneur pour l’ensemble de la disposition. Utilisez <xref:System.Windows.Forms.TableLayoutPanel> des contrôles pour fournir des fonctionnalités de redimensionnement proportionnels aux parties de la disposition.

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création d’un projet Windows Forms

- Réorganisation des contrôles dans les lignes et les colonnes

- Définition des propriétés de ligne et de colonne

- Fractionnement de lignes et de colonnes avec un contrôle

- Gestion automatique des dépassements de capacité

- Insertion de contrôles en double-cliquant dessus dans la boîte à outils

- Insertion d’un contrôle en dessinant son contour

- Réassignation de contrôles existants à un parent différent

À l’issue de cette procédure, vous comprendrez le rôle joué par ces fonctionnalités de disposition importantes.

## <a name="creating-the-project"></a>Création du projet

La première étape consiste à créer le projet et à configurer le formulaire.

#### <a name="to-create-the-project"></a>Pour créer le projet

1. Créez un projet d’application Windows nommé « TableLayoutPanelExample ». Pour plus d’informations, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) .

2. Sélectionnez le formulaire dans le concepteur **Windows** **Forms**.

## <a name="arranging-controls-in-rows-and-columns"></a>Réorganisation des contrôles dans les lignes et les colonnes

Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle vous permet de réorganiser facilement les contrôles en lignes et colonnes.

#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Pour réorganiser des contrôles dans des lignes et des colonnes à l’aide d’un TableLayoutPanel

1. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire. Notez que, par défaut, le <xref:System.Windows.Forms.TableLayoutPanel> contrôle a quatre cellules.

2. Faites glisser un <xref:System.Windows.Forms.Button> contrôle de la **boîte à outils** vers le <xref:System.Windows.Forms.TableLayoutPanel> contrôle et déposez-le dans l’une des cellules. Notez que le <xref:System.Windows.Forms.Button> contrôle est créé dans la cellule que vous avez sélectionnée.

3. Faites glisser trois autres <xref:System.Windows.Forms.Button> contrôles de la **boîte à outils** vers le <xref:System.Windows.Forms.TableLayoutPanel> contrôle, afin que chaque cellule contienne un bouton.

4. Saisissez la poignée de redimensionnement verticale entre les deux colonnes et déplacez-la vers la gauche. Notez que les <xref:System.Windows.Forms.Button> contrôles de la première colonne sont redimensionnés à une plus petite largeur, alors que la taille des <xref:System.Windows.Forms.Button> contrôles de la deuxième colonne est inchangée.

5. Saisissez la poignée de redimensionnement verticale entre les deux colonnes et déplacez-la vers la droite. Notez que les <xref:System.Windows.Forms.Button> contrôles de la première colonne retournent à leur taille d’origine, tandis que les <xref:System.Windows.Forms.Button> contrôles de la deuxième colonne sont déplacés vers la droite.

6. Déplacez la poignée de redimensionnement horizontale vers le haut et le haut pour voir l’effet sur les contrôles dans le panneau.

## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Positionnement des contrôles dans les cellules à l’aide de l’ancrage

Le comportement d’ancrage des contrôles enfants dans un <xref:System.Windows.Forms.TableLayoutPanel> diffère du comportement dans d’autres contrôles conteneurs. Le comportement d’ancrage des contrôles enfants est le même que les autres contrôles conteneurs.

#### <a name="positioning-controls-within-cells"></a>Positionner des contrôles dans des cellules

1. Sélectionnez le premier <xref:System.Windows.Forms.Button> contrôle. Remplacez la valeur de sa propriété <xref:System.Windows.Forms.Control.Dock%2A> par <xref:System.Windows.Forms.DockStyle.Fill>. Notez que le <xref:System.Windows.Forms.Button> contrôle se développe pour remplir sa cellule.

2. Sélectionnez l’un des autres <xref:System.Windows.Forms.Button> contrôles. Remplacez la valeur de sa propriété <xref:System.Windows.Forms.Control.Anchor%2A> par <xref:System.Windows.Forms.AnchorStyles.Right>. Notez qu’elle est déplacée pour que sa bordure droite soit proche de la bordure droite de la cellule. La distance entre les bordures est la somme de la <xref:System.Windows.Forms.Button> propriété du contrôle <xref:System.Windows.Forms.Control.Margin%2A> et de la <xref:System.Windows.Forms.Control.Padding%2A> propriété du panneau.

3. Modifiez la valeur de la <xref:System.Windows.Forms.Button> propriété du contrôle <xref:System.Windows.Forms.Control.Anchor%2A> en <xref:System.Windows.Forms.AnchorStyles.Right> et <xref:System.Windows.Forms.AnchorStyles.Left> . Notez que le contrôle est ajusté à la largeur de la cellule, avec les <xref:System.Windows.Forms.Control.Margin%2A> <xref:System.Windows.Forms.Control.Padding%2A> valeurs et prises en compte.

4. Répétez les étapes 2 et 3 avec les <xref:System.Windows.Forms.AnchorStyles.Top> <xref:System.Windows.Forms.AnchorStyles.Bottom> styles et.

## <a name="setting-row-and-column-properties"></a>Définition des propriétés de ligne et de colonne

Vous pouvez définir des propriétés individuelles de lignes et de colonnes à l’aide des <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> collections et.

#### <a name="to-set-row-and-column-properties"></a>Pour définir les propriétés de ligne et de colonne

1. Sélectionnez le <xref:System.Windows.Forms.TableLayoutPanel> contrôle dans la **Concepteur Windows Forms**.

2. Dans les fenêtres **Propriétés** , ouvrez la <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> collection en cliquant sur le bouton ![ de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio. ](./media/visual-studio-ellipsis-button.png) ) en regard de l’entrée **colonnes** .

3. Sélectionnez la première colonne et remplacez la valeur de sa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriété par <xref:System.Windows.Forms.SizeType.AutoSize> . Cliquez sur **OK** pour accepter la modification. Notez que la largeur de la première colonne est réduite pour s’ajuster au <xref:System.Windows.Forms.Button> contrôle. Notez également que la largeur de la colonne n’est pas redimensionnable.

4. Dans la fenêtre **Propriétés** , ouvrez la <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> collection et sélectionnez la première colonne. Remplacez la valeur de sa propriété <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> par <xref:System.Windows.Forms.SizeType.Percent>. Cliquez sur **OK** pour accepter la modification. Redimensionnez le <xref:System.Windows.Forms.TableLayoutPanel> contrôle à une plus grande largeur et notez que la largeur de la première colonne se développe. Redimensionnez le <xref:System.Windows.Forms.TableLayoutPanel> contrôle sur une plus petite largeur et notez que les boutons de la première colonne sont dimensionnés pour s’ajuster à la cellule. Notez également que la largeur de la colonne est redimensionnable.

5. Dans la fenêtre **Propriétés** , ouvrez la <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> collection et sélectionnez toutes les colonnes listées. Affectez <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> à chaque propriété la valeur <xref:System.Windows.Forms.SizeType.Percent> . Cliquez sur **OK** pour accepter la modification. Répétez la procédure avec la <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> collection.

6. Saisissez une des poignées de redimensionnement d’angle et redimensionnez la largeur et la hauteur du <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Notez que les lignes et les colonnes sont redimensionnées à mesure que la <xref:System.Windows.Forms.TableLayoutPanel> taille du contrôle change. Notez également que les lignes et les colonnes sont redimensionnables avec les poignées de redimensionnement horizontale et verticale.

## <a name="spanning-rows-and-columns-with-a-control"></a>Fractionnement de lignes et de colonnes avec un contrôle

Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle ajoute plusieurs nouvelles propriétés aux contrôles au moment du Design. Deux de ces propriétés sont `RowSpan` et `ColumnSpan` . Vous pouvez utiliser ces propriétés pour qu’un contrôle s’étende sur plusieurs lignes ou colonnes.

#### <a name="to-span-rows-and-columns-with-a-control"></a>Pour étendre les lignes et les colonnes avec un contrôle

1. Sélectionnez le <xref:System.Windows.Forms.Button> contrôle dans la première ligne et la première colonne.

2. Dans les fenêtres **Propriétés** , remplacez la valeur de la `ColumnSpan` propriété par **2**. Notez que le <xref:System.Windows.Forms.Button> contrôle remplit la première colonne et la deuxième colonne. Notez également qu’une ligne supplémentaire a été ajoutée pour prendre en compte cette modification.

3. Répétez l’étape 2 pour la `RowSpan` propriété.

## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Insertion de contrôles en double-cliquant dessus dans la boîte à outils

Vous pouvez remplir votre contrôle <xref:System.Windows.Forms.TableLayoutPanel> en double-cliquant sur des contrôles dans la **boîte à outils**.

#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Pour insérer des contrôles en double-cliquant dessus dans la boîte à outils

1. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

2. Double-cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> dans la **boîte à outils**. Notez qu’un nouveau contrôle bouton s’affiche dans la <xref:System.Windows.Forms.TableLayoutPanel> première cellule du contrôle.

3. Double-cliquez sur plusieurs autres contrôles dans la **boîte à outils**. Notez que les nouveaux contrôles s’affichent successivement dans les <xref:System.Windows.Forms.TableLayoutPanel> cellules inoccupées du contrôle. Notez également que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle se développe pour s’adapter aux nouveaux contrôles si aucune cellule ouverte n’est disponible.

## <a name="automatic-handling-of-overflows"></a>Gestion automatique des dépassements de capacité

Lorsque vous insérez des contrôles dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôle, vous pouvez manquer de cellules vides pour vos nouveaux contrôles. Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle gère cette situation automatiquement en accroissant le nombre de cellules.

#### <a name="to-observe-automatic-handling-of-overflows"></a>Pour observer la gestion automatique des dépassements de capacité

1. Si le contrôle contient toujours des cellules vides <xref:System.Windows.Forms.TableLayoutPanel> , continuez à insérer de nouveaux <xref:System.Windows.Forms.Button> contrôles jusqu’à ce que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle soit plein.

2. Une fois que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle est plein, double-cliquez sur l' <xref:System.Windows.Forms.Button> icône dans la **boîte à outils** pour insérer un autre <xref:System.Windows.Forms.Button> contrôle. Notez que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle crée des cellules pour s’adapter au nouveau contrôle. Insérez quelques contrôles supplémentaires et observez le comportement de redimensionnement.

3. Affectez la valeur <xref:System.Windows.Forms.TableLayoutPanel> à la propriété <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> du contrôle <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize>. Double-cliquez sur l' <xref:System.Windows.Forms.Button> icône dans la **boîte à outils** pour insérer des <xref:System.Windows.Forms.Button> contrôles jusqu’à ce que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle soit plein. Double-cliquez <xref:System.Windows.Forms.Button> de nouveau sur l’icône dans la **boîte à outils** . Notez que vous recevez un message d’erreur de la **Concepteur Windows Forms** vous informant que des lignes et des colonnes supplémentaires ne peuvent pas être créées.

## <a name="inserting-a-control-by-drawing-its-outline"></a>Insertion d’un contrôle en dessinant son contour

Vous pouvez insérer un contrôle dans un contrôle <xref:System.Windows.Forms.TableLayoutPanel> et spécifier sa taille en dessinant son contour dans une cellule.

#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Pour insérer un contrôle en dessinant son contour

1. Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **boîte à outils** vers le formulaire.

2. Dans la **boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> . Ne la faites pas glisser sur le formulaire.

3. Placez le pointeur de la souris sur le contrôle <xref:System.Windows.Forms.TableLayoutPanel> . Notez que le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.Button> .

4. Cliquez et maintenez le bouton de la souris enfoncé.

5. Faites glisser le pointeur de la souris pour tracer le contour du contrôle <xref:System.Windows.Forms.Button> . Quand la taille vous convient, relâchez le bouton de la souris. Notez que le <xref:System.Windows.Forms.Button> contrôle est créé dans la cellule dans laquelle vous avez dessiné le contour du contrôle.

## <a name="multiple-controls-within-cells-are-not-permitted"></a>Plusieurs contrôles dans les cellules ne sont pas autorisés

Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle ne peut contenir qu’un seul contrôle enfant par cellule.

#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Pour démontrer que plusieurs contrôles dans les cellules ne sont pas autorisés

- Faites glisser un <xref:System.Windows.Forms.Button> contrôle de la **boîte à outils** vers le <xref:System.Windows.Forms.TableLayoutPanel> contrôle et déposez-le dans l’une des cellules occupées. Notez que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle ne vous permet pas de déposer le <xref:System.Windows.Forms.Button> contrôle dans la cellule occupée.

## <a name="swapping-controls"></a>Permuter des contrôles

Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle vous permet d’échanger les contrôles occupant deux cellules différentes.

#### <a name="to-swap-controls"></a>Pour échanger des contrôles

- Faites glisser l’un des <xref:System.Windows.Forms.Button> contrôles à partir d’une cellule occupée et déposez-le dans sur une autre cellule occupée. Notez que les deux contrôles sont déplacés d’une cellule à l’autre.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez obtenir une disposition complexe en combinant plusieurs contrôles et panneaux de disposition. Suggestions pour des recherches approfondies :

- Essayez de redimensionner l’un des <xref:System.Windows.Forms.Button> contrôles à une plus grande taille et notez l’effet sur la disposition.

- Collez une sélection de plusieurs contrôles dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôle et notez la façon dont les contrôles sont insérés.

- Les panneaux de disposition peuvent contenir d’autres panneaux de disposition. Faites l’expérience de déposer un contrôle <xref:System.Windows.Forms.TableLayoutPanel> dans le contrôle existant.

- Ancrez le contrôle <xref:System.Windows.Forms.TableLayoutPanel> au formulaire parent. Redimensionnez le formulaire et observez-en l’effet sur la disposition.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement (SnapLines)](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [Procédure pas à pas : création d’un Windows Form redimensionnable pour l’entrée de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))
- [Procédure pas à pas : création d’un Windows Form localisable](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))
- [Meilleures pratiques pour le contrôle TableLayoutPanel](best-practices-for-the-tablelayoutpanel-control.md)
- [Vue d'ensemble de la propriété AutoSize](autosize-property-overview.md)
- [Guide pratique pour fixer des contrôles sur des Windows Forms](how-to-dock-controls-on-windows-forms.md)
- [Guide pratique pour ancrer des contrôles sur des Windows Forms](how-to-anchor-controls-on-windows-forms.md)
- [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](windows-forms-controls-padding-autosize.md)
