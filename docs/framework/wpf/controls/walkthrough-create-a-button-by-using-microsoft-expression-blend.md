---
title: "Procédure pas à pas : création d'un bouton à l'aide de Microsoft Expression Blend"
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [WPF]
- converting [WPF], shape to button
- Expression Blend [WPF Designer]
ms.assetid: ff5037c2-bba7-4cae-8abb-6475b686c48e
ms.openlocfilehash: 10342d97abc2e3c158f93171f5fe5cd560f9b7e4
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920265"
---
# <a name="walkthrough-create-a-button-by-using-microsoft-expression-blend"></a>Procédure pas à pas : création d'un bouton à l'aide de Microsoft Expression Blend

Cette procédure pas à pas vous guide tout au long du processus de création d’un [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bouton personnalisé à l’aide de Microsoft Expression Blend.

> [!IMPORTANT]
> Microsoft Expression Blend fonctionne en générant [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] qui est ensuite compilé pour créer le programme exécutable. Si vous préférez travailler directement avec XAML, il existe une autre procédure pas à pas qui crée la même application que celle-ci à l’aide de XAML avec Visual Studio au lieu de Blend. Pour plus d’informations, consultez [créer un bouton à l’aide de XAML](walkthrough-create-a-button-by-using-xaml.md) .

L’illustration suivante montre le bouton personnalisé que vous allez créer.

![Bouton personnalisé que vous allez créer](./media/custom-button-blend-intro.jpg)

## <a name="convert-a-shape-to-a-button"></a>Convertir une forme en bouton

Dans la première partie de cette procédure pas à pas, vous allez créer l’apparence personnalisée du bouton personnalisé. Pour ce faire, vous devez d’abord convertir un rectangle en bouton. Vous ajoutez ensuite des formes supplémentaires au modèle du bouton, en créant un bouton d’apparence plus complexe. Pourquoi ne pas démarrer avec un bouton normal et le personnaliser ? Étant donné qu’un bouton a des fonctionnalités intégrées dont vous n’avez pas besoin ; pour les boutons personnalisés, il est plus facile de commencer par un rectangle.

### <a name="to-create-a-new-project-in-expression-blend"></a>Pour créer un projet dans Expression Blend

1. Démarrez Expression Blend. (Cliquez sur **Démarrer**, pointez sur **tous les programmes**, sur **expression Microsoft**, puis cliquez sur **Microsoft Expression Blend**.)

2. Agrandissez l’application si nécessaire.

3. Dans le menu **Fichier**, cliquez sur **Nouveau projet**.

4. Sélectionnez **application standard (. exe)** .

5. Nommez le projet `CustomButton`, puis cliquez sur **OK**.

À ce stade, vous avez un projet de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vide. Vous pouvez appuyer sur F5 pour exécuter l’application. Comme vous pouvez vous y attendre, l’application se compose uniquement d’une fenêtre vide. Vous allez ensuite créer un rectangle arrondi et le convertir en bouton.

### <a name="to-convert-a-rectangle-to-a-button"></a>Pour convertir un rectangle en bouton

1. **Définissez la propriété arrière-plan de la fenêtre sur noir :** Sélectionnez la fenêtre, cliquez sur l' **onglet Propriétés**et affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur `Black`.

    ![Comment définir un arrière-plan noir pour un bouton](./media/custom-button-blend-changebackground.png)

2. **Dessinez un rectangle approximativement la taille d’un bouton sur la fenêtre :** Sélectionnez l’outil Rectangle dans le panneau d’outils de gauche, puis faites glisser le rectangle dans la fenêtre.

    ![Comment dessiner un rectangle](./media/custom-button-blend-drawrect.png)

3. **Arrondir les angles du rectangle :** Faites glisser les points de contrôle du rectangle ou définissez directement les propriétés <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>. Définissez les valeurs de <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> sur 20.

    ![Comment arrondir les angles d'un rectangle](./media/custom-button-blend-roundcorners.png)

4. **Modifiez le rectangle en un bouton :** Sélectionnez le rectangle. Dans le menu **Outils** , cliquez sur **bouton créer**.

    ![Comment transformer une forme en bouton](./media/custom-button-blend-makebutton.png)

5. **Spécifiez l’étendue du style/modèle :** Une boîte de dialogue semblable à la suivante s’affiche.

    ![Boîte de dialogue Créer une ressource de style](./media/custom-button-blend-makebutton2.gif)

    Pour **nom de la ressource (clé)** , sélectionnez **appliquer à tout**.  Le style et le modèle de bouton qui en résultent s’appliquent à tous les objets qui sont des boutons. Pour **définir dans**, sélectionnez **application**. Ainsi, le style et le modèle de bouton résultants ont une portée sur l’ensemble de l’application. Lorsque vous définissez les valeurs de ces deux zones, le style de bouton et le modèle s’appliquent à tous les boutons de l’application entière et tout bouton que vous créez dans l’application utilisera, par défaut, ce modèle.

## <a name="edit-the-button-template"></a>Modifier le modèle de bouton

Vous avez maintenant un rectangle qui a été remplacé par un bouton. Dans cette section, vous allez modifier le modèle du bouton et personnaliser davantage son apparence.

### <a name="to-edit-the-button-template-to-change-the-button-appearance"></a>Pour modifier le modèle de bouton pour modifier l’apparence du bouton

1. **Accédez à la vue modifier le modèle :** Pour personnaliser davantage l’apparence de notre bouton, nous devons modifier le modèle de bouton. Ce modèle a été créé lors de la conversion du rectangle en bouton. Pour modifier le modèle de bouton, cliquez avec le bouton droit sur le bouton, puis sélectionnez **modifier les parties du contrôle (modèle)** , puis **modifier le modèle**.

    ![Comment modifier un modèle](./media/custom-button-blend-edittemplate.jpg)

    Dans l’éditeur de modèle, Notez que le bouton est maintenant scindé en <xref:System.Windows.Shapes.Rectangle> et le <xref:System.Windows.Controls.ContentPresenter>. Le <xref:System.Windows.Controls.ContentPresenter> est utilisé pour présenter le contenu dans le bouton (par exemple, la chaîne « Button »). Le rectangle et le <xref:System.Windows.Controls.ContentPresenter> sont disposés à l’intérieur d’une <xref:System.Windows.Controls.Grid>.

    ![Composants de la présentation d'un rectangle](./media/custom-button-blend-templatepanel.png)

2. **Modifiez les noms des composants du modèle :** Cliquez avec le bouton droit sur le rectangle dans l’inventaire des modèles, modifiez le nom du <xref:System.Windows.Shapes.Rectangle> de « [rectangle] » en « RectangleExterne », puis remplacez « [ContentPresenter] » par « myContentPresenter ».

    ![Comment renommer un composant d'un modèle](./media/custom-button-blend-renamecomponents.png)

3. **Modifiez le rectangle afin qu’il soit vide dans (comme un anneau) :** Sélectionnez **RectangleExterne** et définissez <xref:System.Windows.Shapes.Shape.Fill%2A> sur « transparent » et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> sur 5.

    ![Comment obtenir un rectangle vide](./media/custom-button-blend-changerectproperties.png)

    Affectez ensuite à la <xref:System.Windows.Shapes.Shape.Stroke%2A> la couleur du modèle. Pour ce faire, cliquez sur la petite zone blanche en regard du **trait**, sélectionnez **CustomExpression**, puis tapez « {TemplateBinding background} » dans la boîte de dialogue.

    ![Comment utiliser la couleur du modèle](./media/custom-button-blend-templatestroke.png)

4. **Créez un rectangle interne :** À présent, créez un autre rectangle (nommez-le « innerRectangle ») et positionnez-le de manière symétrique à l’intérieur de **RectangleExterne** . Pour ce type de travail, vous souhaiterez probablement effectuer un zoom pour agrandir le bouton dans la zone d’édition.

    > [!NOTE]
    > Le rectangle peut être différent de celui de la figure (par exemple, il peut avoir des angles arrondis).

    ![Comment créer un rectangle dans un autre rectangle](./media/custom-button-blend-innerrectangleproperties.png)

5. **Déplacer ContentPresenter vers le haut :** À ce stade, il est possible que le texte « Button » ne soit plus visible. Si c’est le cas, cela est dû au fait que **innerRectangle** se trouve au-dessus du **myContentPresenter**. Pour résoudre ce problème, faites glisser **myContentPresenter** sous **innerRectangle**. Repositionnez les rectangles et **myContentPresenter** pour qu’ils se présentent comme ci-dessous.

    > [!NOTE]
    > Vous pouvez également placer **myContentPresenter** en haut en cliquant dessus avec le bouton droit et en appuyant sur **Envoyer vers l’avant**.

    ![Comment placer un bouton sur un autre bouton](./media/custom-button-blend-innerrectangle2.png)

6. **Modifiez l’apparence de innerRectangle :** Définissez les valeurs <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>, <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>et <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> sur 20. En outre, définissez le <xref:System.Windows.Shapes.Shape.Fill%2A> à l’arrière-plan du modèle à l’aide de l’expression personnalisée « {TemplateBinding Background} ») et affectez à <xref:System.Windows.Shapes.Shape.Stroke%2A> la valeur « transparent ». Notez que les paramètres de la <xref:System.Windows.Shapes.Shape.Fill%2A> et <xref:System.Windows.Shapes.Shape.Stroke%2A> de **innerRectangle** sont l’inverse de ceux de **RectangleExterne**.

    ![Comment modifier l'apparence d'un rectangle](./media/custom-button-blend-glassrectangleproperties1.png)

7. **Ajouter une couche de verre en haut :** La dernière partie de la personnalisation de l’apparence du bouton consiste à ajouter une couche de verre en haut. Cette couche de verre est constituée d’un troisième rectangle. Étant donné que la vitre couvre l’ensemble du bouton, le rectangle de transparence est semblable aux dimensions du **RectangleExterne**. Par conséquent, créez le rectangle en effectuant simplement une copie de **RectangleExterne**. Mettez en surbrillance **RectangleExterne** et utilisez Ctrl + C et Ctrl + V pour effectuer une copie. Nommez ce nouveau rectangle « glassCube ».

8. **Repositionner glassCube si nécessaire :** Si **glassCube** n’est pas déjà positionné afin qu’il couvre l’ensemble du bouton, faites-le glisser vers la position.

9. **Donnez à glassCube une forme légèrement différente de la forme RectangleExterne :** Modifiez les propriétés de **glassCube**. Commencez par modifier les propriétés <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> et <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> sur 10 et la <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> sur 2.

    ![Paramètres d'apparence d'un glassCube](./media/custom-button-blend-glasscubeappearance.gif)

10. **Faire ressembler à glassCube :** Affectez à la <xref:System.Windows.Shapes.Shape.Fill%2A> une apparence en verre à l’aide d’un dégradé linéaire de 75% opaque et de remplacements entre la couleur blanche et transparente sur 6 intervalles uniformément espacés approximativement. Voici ce à quoi les points de dégradé doivent être définis :

    - Point de dégradé 1 : blanc avec une valeur alpha de 75%

    - Point de dégradé 2 : transparent

    - Point de dégradé 3 : blanc avec une valeur alpha de 75%

    - Point de dégradé 4 : transparent

    - Point de dégradé 5 : blanc avec une valeur alpha de 75%

    - Point de dégradé 6 : transparent

    Cela crée un aspect de verre « ondulé ».

    ![Rectangle ressemblant à un verre](./media/custom-button-blend-glassrectangleproperties2.png)

11. **Masquer la couche de verre :** Maintenant que vous voyez à quoi ressemble la couche de verre, accédez au **volet apparence** du **panneau Propriétés** et définissez l’opacité sur 0% pour la masquer. Dans les sections suivantes, nous allons utiliser des déclencheurs de propriété et des événements pour afficher et manipuler la couche de verre.

    ![Comment masquer le rectangle transparent](./media/custom-button-glassrectangleproperties3.gif)

## <a name="customize-the-button-behavior"></a>Personnaliser le comportement du bouton

À ce stade, vous avez personnalisé la présentation du bouton en modifiant son modèle, mais le bouton ne réagit pas aux actions de l’utilisateur comme les boutons habituels (par exemple, en modifiant l’apparence à la souris, en recevant le focus et en cliquant sur.) Les deux procédures suivantes montrent comment générer des comportements comme ceux-ci dans le bouton personnalisé. Nous allons commencer par des déclencheurs de propriété simples, puis ajouter des déclencheurs et des animations d’événements.

### <a name="to-set-property-triggers"></a>Pour définir des déclencheurs de propriété

1. **Créer un déclencheur de propriété :** Avec **glassCube** sélectionné, cliquez sur **+ propriété** dans le panneau **déclencheurs** (voir la figure qui suit l’étape suivante). Cela permet de créer un déclencheur de propriété avec un déclencheur de propriété par défaut.

2. **Définissez IsMouseOver comme la propriété utilisée par le déclencheur :** Remplacez la valeur de la propriété par <xref:System.Windows.UIElement.IsMouseOver%2A>. Ainsi, le déclencheur de propriété est activé lorsque la propriété <xref:System.Windows.UIElement.IsMouseOver%2A> est `true` (lorsque l’utilisateur pointe sur le bouton à l’aide de la souris).

    ![Comment définir un déclencheur sur une propriété](./media/custom-button-blend-ismousedoverpropertytrigger.png)

3. **IsMouseOver déclenche l’opacité de 100% pour glassCube :** Notez que l' **enregistrement du déclencheur est activé** (voir la figure précédente). Cela signifie que toutes les modifications apportées aux valeurs de propriété de **glassCube** alors que l’enregistrement est activé deviendront une action qui a lieu lorsque <xref:System.Windows.UIElement.IsMouseOver%2A> est `true`. Pendant l’enregistrement, modifiez la <xref:System.Windows.UIElement.Opacity%2A> de **glassCube** à 100%.

    ![Comment définir l'opacité d'un bouton](./media/custom-button-blend-ismousedoverpropertytrigger2.gif)

    Vous avez maintenant créé votre premier déclencheur de propriété. Notez que le **panneau Déclencheurs** de l’éditeur a enregistré le <xref:System.Windows.UIElement.Opacity%2A> en cours de modification à 100%.

    ![Volet Déclencheurs](./media/custom-button-blend-propertytriggerinfo.png)

    Appuyez sur F5 pour exécuter l’application et déplacez le pointeur de la souris sur le bouton. Vous devez voir apparaître la couche de transparence quand vous placez la souris sur le bouton et disparaissez quand le pointeur quitte.

4. La **valeur du trait des déclencheurs IsMouseOver change :** Nous allons associer d’autres actions au déclencheur <xref:System.Windows.UIElement.IsMouseOver%2A>. Pendant l’enregistrement, basculez votre sélection de **glassCube** à **RectangleExterne**. Définissez ensuite la <xref:System.Windows.Shapes.Shape.Stroke%2A> de **RectangleExterne** sur l’expression personnalisée « {DynamicResource {x :static SystemColors. HighlightBrushKey}} ». Cela définit la <xref:System.Windows.Shapes.Shape.Stroke%2A> sur la couleur de surbrillance classique utilisée par les boutons. Appuyez sur F5 pour voir l’effet lorsque vous pointez avec la souris sur le bouton.

    ![Comment définir le trait sur la couleur de surbrillance](./media/custom-button-blend-ismousedoverpropertytrigger3.png)

5. Le **texte flou des déclencheurs IsMouseOver est le suivant :** Nous allons associer une action supplémentaire au déclencheur de propriété <xref:System.Windows.UIElement.IsMouseOver%2A>. Faites en sorte que le contenu du bouton apparaisse un peu flou lorsque la vitre s’affiche au-dessus. Pour ce faire, nous pouvons appliquer un flou <xref:System.Windows.Media.Effects.BitmapEffect> à la <xref:System.Windows.Controls.ContentPresenter> (**myContentPresenter**).

    ![Comment estomper le contenu d'un bouton](./media/custom-button-blend-propertytriggerwithbitmapeffect.png)

    > [!NOTE]
    > Pour revenir au **panneau Propriétés** avant d’avoir effectué la recherche de <xref:System.Windows.Media.Effects.BitmapEffect>, effacez le texte de la **zone de recherche**.

    À ce stade, nous avons utilisé un déclencheur de propriété avec plusieurs actions associées pour créer un comportement de mise en surbrillance lorsque le pointeur de la souris entre et quitte la zone de bouton. Un autre comportement classique d’un bouton consiste à mettre en surbrillance lorsqu’il a le focus (comme après l’avoir cliqué dessus). Nous pouvons ajouter un tel comportement en ajoutant un autre déclencheur de propriété pour la propriété <xref:System.Windows.UIElement.IsFocused%2A>.

6. **Créer un déclencheur de propriété pour IsFocused :** À l’aide de la même procédure que pour <xref:System.Windows.UIElement.IsMouseOver%2A> (voir la première étape de cette section), créez un autre déclencheur de propriété pour la propriété <xref:System.Windows.UIElement.IsFocused%2A>. Lorsque l' **enregistrement du déclencheur est activé**, ajoutez les actions suivantes au déclencheur :

    - **glassCube** obtient une <xref:System.Windows.UIElement.Opacity%2A> de 100%.

    - **RectangleExterne** obtient une <xref:System.Windows.Shapes.Shape.Stroke%2A> valeur d’expression personnalisée « {DynamicResource {x :static SystemColors. HighlightBrushKey}} ».

Comme dernière étape de cette procédure pas à pas, nous allons ajouter des animations au bouton. Ces animations sont déclenchées par les événements, en particulier les événements <xref:System.Windows.UIElement.MouseEnter> et <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

### <a name="to-use-event-triggers-and-animations-to-add-interactivity"></a>Pour utiliser les animations et les déclencheurs d’événements pour ajouter l’interactivité

1. **Créer un déclencheur d’événement MouseEnter :** Ajoutez un nouveau déclencheur d’événements et sélectionnez <xref:System.Windows.UIElement.MouseEnter> comme événement à utiliser dans le déclencheur.

     ![Comment créer un déclencheur d'événement MouseEnter](./media/custom-button-blend-mouseovereventtrigger.png)

2. **Créer une chronologie d’animation :** Ensuite, associez une chronologie d’animation à l’événement <xref:System.Windows.UIElement.MouseEnter>.

    ![Comment ajouter une chronologie d'animation à un événement](./media/custom-button-blend-mouseovereventtrigger2.png)

    Une fois que vous avez cliqué sur **OK** pour créer une nouvelle chronologie, un **panneau chronologie** s’affiche et « l’enregistrement de la chronologie est activé » est visible dans le panneau de conception. Cela signifie que nous pouvons commencer à enregistrer les modifications apportées aux propriétés dans la chronologie (animer les modifications de propriété).

    > [!NOTE]
    > Vous devrez peut-être redimensionner votre fenêtre et/ou vos panneaux pour voir l’affichage.

    ![Volet chronologie](./media/custom-button-blend-mouseovereventtrigger3.png)

3. **Créer une image clé :** Pour créer une animation, sélectionnez l’objet que vous souhaitez animer, créez deux images clés ou plus sur la chronologie, et pour ces images clés, définissez les valeurs de propriété que l’animation doit interpoler. La figure suivante vous guide tout au long de la création d’une image clé.

    ![Comment créer une image clé](./media/custom-button-blend-mouseovereventtrigger4.png)

4. **Réduire glassCube à cette image clé :** Après avoir sélectionné la deuxième image clé, réduisez la taille du **glassCube** à 90% de sa taille maximale à l’aide de la **transformation taille**.

    ![Comment réduire la taille d'un bouton](./media/custom-button-blend-sizetransform.png)

    Appuyez sur F5 pour exécuter l'application. Déplacez le pointeur de la souris sur le bouton. Notez que la couche de verre se réduit au-dessus du bouton.

5. **Créez un autre déclencheur d’événement et associez-lui une animation différente :** Nous allons ajouter une animation supplémentaire. Utilisez une procédure similaire à celle que vous avez utilisée pour créer l’animation précédente du déclencheur d’événements :

    1. Créez un déclencheur d’événement à l’aide de l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

    2. Associez une nouvelle chronologie à l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

        ![Comment créer une nouvelle chronologie](./media/custom-button-blend-clickeventtrigger1.png)

    3. Pour cette chronologie, créez deux images clés, une à 0,0 secondes et la seconde à 0,3 secondes.

    4. Avec l’image clé à 0,3 secondes en surbrillance, définissez l' **angle de transformation de rotation** sur 360 degrés.

        ![Comment créer une transformation de rotation](./media/custom-button-blend-rotatetransform.gif)

    5. Appuyez sur F5 pour exécuter l'application. Cliquez sur le bouton. Notez que la couche de verre tourne autour.

## <a name="conclusion"></a>Conclusion

Vous avez terminé un bouton personnalisé. Vous l’avez fait à l’aide d’un modèle de bouton qui a été appliqué à tous les boutons de l’application. Si vous laissez le mode de modification de modèle (voir la figure ci-dessous) et que vous créez d’autres boutons, vous verrez qu’ils apparaissent et se comportent comme votre bouton personnalisé plutôt que comme le bouton par défaut.

![Modèle de bouton personnalisé](./media/custom-button-blend-scopeup.gif)

![Plusieurs boutons utilisant le même modèle](./media/custom-button-blend-createmultiplebuttons.png)

Appuyez sur F5 pour exécuter l'application. Cliquez sur les boutons et notez la façon dont ils se comportent tous de la même façon.

N’oubliez pas que lors de la personnalisation du modèle, vous affectez à la propriété <xref:System.Windows.Shapes.Shape.Fill%2A> de **innerRectangle** et à la propriété <xref:System.Windows.Shapes.Shape.Stroke%2A> **RectangleExterne** la valeur de l’arrière-plan du modèle ({TemplateBinding Background}). Pour cette raison, lorsque vous définissez la couleur d’arrière-plan des boutons individuels, l’arrière-plan que vous définissez sera utilisé pour ces propriétés respectives. Essayez de modifier les arrière-plans maintenant. Dans l’illustration suivante, différents dégradés sont utilisés. Par conséquent, bien qu’un modèle soit utile pour la personnalisation globale de contrôles tels que Button, les contrôles avec des modèles peuvent toujours être modifiés pour être différents les uns des autres.

![Boutons avec le même modèle qui ressemblent à différent](./media/custom-button-blend-blendconclusion.jpg "custom_button_blend_BlendConclusion")

En conclusion, dans le processus de personnalisation d’un modèle de bouton, vous avez appris à effectuer les opérations suivantes dans Microsoft Expression Blend :

- Personnaliser l’apparence d’un contrôle.

- Définissez les déclencheurs de propriété. Les déclencheurs de propriété sont très utiles car ils peuvent être utilisés sur la plupart des objets, et pas seulement sur les contrôles.

- Définir des déclencheurs d’événements. Les déclencheurs d’événements sont très utiles car ils peuvent être utilisés sur la plupart des objets, et pas seulement sur les contrôles.

- Créer des animations.

- Divers : créer des dégradés, ajouter des BitmapEffects, utiliser des transformations et définir les propriétés de base des objets.

## <a name="see-also"></a>Voir aussi

- [Créer un bouton avec XAML](walkthrough-create-a-button-by-using-xaml.md)
- [Application d’un style et création de modèles](styling-and-templating.md)
- [Vue d’ensemble de l’animation](../graphics-multimedia/animation-overview.md)
- [Vue d’ensemble de la peinture avec des couleurs unies ou des dégradés](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Vue d’ensemble des effets bitmap](../graphics-multimedia/bitmap-effects-overview.md)
