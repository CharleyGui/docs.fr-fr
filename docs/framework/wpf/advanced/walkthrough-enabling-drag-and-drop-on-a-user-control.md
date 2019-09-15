---
title: 'Procédure pas à pas : activation de Glisser-déplacer sur un contrôle utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthrough [WPF], drag-and-drop
- drag-and-drop [WPF], walkthrough
ms.assetid: cc844419-1a77-4906-95d9-060d79107fc7
ms.openlocfilehash: 172e49c2c255db4d24d2180f919b1305326b5e82
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991808"
---
# <a name="walkthrough-enabling-drag-and-drop-on-a-user-control"></a>Procédure pas à pas : activation de Glisser-déplacer sur un contrôle utilisateur

Cette procédure pas à pas montre comment créer un contrôle utilisateur personnalisé qui peut participer à un transfert de données par glisser-déplacer dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].

Dans cette procédure pas à pas, vous allez créer <xref:System.Windows.Controls.UserControl> un WPF personnalisé qui représente une forme de cercle. Vous implémentez la fonctionnalité sur le contrôle pour activer le transfert de données par glisser-déplacer. Par exemple, si vous faites glisser un contrôle de cercle sur un autre, les données de couleur de remplissage sont copiées du cercle source vers la cible. Si vous faites glisser un contrôle Circle vers un <xref:System.Windows.Controls.TextBox>, la représentation sous forme de chaîne de la couleur de remplissage <xref:System.Windows.Controls.TextBox>est copiée dans le. Vous allez également créer une petite application qui contient deux contrôles de panneau et <xref:System.Windows.Controls.TextBox> un pour tester la fonctionnalité de glisser-déplacer. Vous écrivez du code qui permet aux panneaux de traiter les données de cercle déplacées, ce qui vous permet de déplacer ou copier des cercles de la collection d’enfants d’un panneau à l’autre.

Cette procédure pas à pas décrit les tâches suivantes :

- Créer un contrôle utilisateur personnalisé.

- Permettre au contrôle utilisateur d’être une source de glissement.

- Permettre au contrôle utilisateur d’être une cible de déplacement.

- Permettre à un panneau de recevoir des données déplacées à partir du contrôle utilisateur.

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-the-application-project"></a>Créer le projet d’application
 Dans cette section, vous allez créer l’infrastructure de l’application, qui comprend une page principale avec deux panneaux <xref:System.Windows.Controls.TextBox>et un.

1. Créez un projet d’application WPF en Visual Basic ou Visual C# nommé `DragDropExample`. Pour plus d’informations, consultez [Procédure pas à pas : Ma première application](../getting-started/walkthrough-my-first-wpf-desktop-application.md)de bureau WPF.

2. Ouvrez MainWindow.xaml.

3. Ajoutez le balisage suivant entre les balises <xref:System.Windows.Controls.Grid> d’ouverture et de fermeture.

     Ce balisage crée l’interface utilisateur pour l’application de test.

     [!code-xaml[DragDropWalkthrough#PanelsStep1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep1xaml)]

## <a name="add-a-new-user-control-to-the-project"></a>Ajouter un nouveau contrôle utilisateur au projet
 Dans cette section, vous ajoutez un nouveau contrôle utilisateur au projet.

1. Dans le menu Projet, sélectionnez **Ajouter un contrôle utilisateur**.

2. Dans la boîte de dialogue **Ajouter un nouvel élément** , remplacez le `Circle.xaml`nom par, puis cliquez sur **Ajouter**.

     Circle.XAML et son code-behind sont ajoutés au projet.

3. Ouvrez Circle.xaml.

     Ce fichier doit contenir les éléments d’interface utilisateur du contrôle utilisateur.

4. Ajoutez le balisage suivant à la <xref:System.Windows.Controls.Grid> racine pour créer un contrôle utilisateur simple dont l’interface utilisateur est un cercle bleu.

     [!code-xaml[DragDropWalkthrough#EllipseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#ellipsexaml)]

5. Ouvrez Circle.xaml.cs ou Circle.xaml.vb.

6. Dans C#, ajoutez le code suivant après le constructeur sans paramètre pour créer un constructeur de copie. Dans Visual Basic, ajoutez le code suivant pour créer un constructeur sans paramètre et un constructeur de copie.

     Pour que le contrôle utilisateur puisse être copié, vous ajoutez une méthode de constructeur de copie dans le fichier code-behind. Dans le contrôle utilisateur de cercle simplifié, vous copiez uniquement les valeurs de remplissage et de taille du contrôle utilisateur.

     [!code-csharp[DragDropWalkthrough#CopyCtor](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#copyctor)]
     [!code-vb[DragDropWalkthrough#CopyCtor](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#copyctor)]

## <a name="add-the-user-control-to-the-main-window"></a>Ajouter le contrôle utilisateur à la fenêtre principale

1. Ouvrez MainWindow.xaml.

2. Ajoutez le code XAML suivant à la <xref:System.Windows.Window> balise d’ouverture pour créer une référence d’espace de noms XML à l’application actuelle.

    ```xaml
    xmlns:local="clr-namespace:DragDropExample"
    ```

3. Dans le premier <xref:System.Windows.Controls.StackPanel>, ajoutez le code XAML suivant pour créer deux instances du contrôle utilisateur Circle dans le premier panneau.

     [!code-xaml[DragDropWalkthrough#CirclesXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#circlesxaml)]

     Le code XAML complet pour le panneau ressemble à ce qui suit.

     [!code-xaml[DragDropWalkthrough#PanelsStep2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/SnippetWindow.xaml#panelsstep2xaml)]

## <a name="implement-drag-source-events-in-the-user-control"></a>Implémenter les événements de source de glissement dans le contrôle utilisateur
 Dans cette section, vous allez substituer la <xref:System.Windows.UIElement.OnMouseMove%2A> méthode et lancer l’opération de glisser-déplacer.

 Si un glisser-déplacer est démarré (un bouton de la souris est enfoncé et que la souris est déplacée), vous allez empaqueter les données à transférer dans un <xref:System.Windows.DataObject>. Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.

### <a name="to-initiate-a-drag-and-drop-operation"></a>Pour lancer une opération de glisser-déplacer

1. Ouvrez Circle.xaml.cs ou Circle.xaml.vb.

2. Ajoutez la substitution <xref:System.Windows.UIElement.OnMouseMove%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.MouseMove> l’événement.

     [!code-csharp[DragDropWalkthrough#OnMouseMove](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#onmousemove)]
     [!code-vb[DragDropWalkthrough#OnMouseMove](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#onmousemove)]

     Ce <xref:System.Windows.UIElement.OnMouseMove%2A> remplacement effectue les tâches suivantes:

    - Vérifie si le bouton gauche de la souris est enfoncé quand la souris se déplace.

    - Empaquette les données de <xref:System.Windows.DataObject>cercle dans un. Dans cet exemple, le contrôle de cercle empaquette trois éléments de données : une représentation sous forme de chaîne de sa couleur de remplissage, une double représentation de sa hauteur et une copie de lui-même.

    - Appelle la méthode <xref:System.Windows.DragDrop.DoDragDrop%2A?displayProperty=nameWithType> statique pour initier l’opération de glisser-déplacer. Vous transmettez les trois paramètres suivants à <xref:System.Windows.DragDrop.DoDragDrop%2A> la méthode:

        - `dragSource` : Référence à ce contrôle.

        - `data`: Le <xref:System.Windows.DataObject> créé dans le code précédent.

        - `allowedEffects`: Les opérations de glisser-déplacer autorisées, qui sont <xref:System.Windows.DragDropEffects.Copy> ou. <xref:System.Windows.DragDropEffects.Move>

3. Appuyez sur **F5** pour générer et exécuter l’application.

4. Cliquez sur l’un des contrôles de cercle et faites-le glisser sur les panneaux, l’autre <xref:System.Windows.Controls.TextBox>cercle et le. Lorsque vous faites glisser le <xref:System.Windows.Controls.TextBox>pointeur de la souris sur le, le curseur change pour indiquer un déplacement.

5. Tout en faisant glisser un cercle sur <xref:System.Windows.Controls.TextBox>le, appuyez sur la touche **CTRL** . Notez que le curseur change pour indiquer une copie.

6. Glissez-déposez un <xref:System.Windows.Controls.TextBox>cercle sur le. La représentation sous forme de chaîne de la couleur de remplissage du cercle est <xref:System.Windows.Controls.TextBox>ajoutée à.

     ![Représentation sous forme de chaîne de la couleur de remplissage du cercle](./media/dragdrop-colorstring.png "DragDrop_ColorString")

Par défaut, le curseur change pendant une opération de glisser-déplacer pour indiquer l’effet du déplacement des données. Vous pouvez personnaliser les commentaires donnés à l’utilisateur en gérant l' <xref:System.Windows.UIElement.GiveFeedback> événement et en définissant un autre curseur.

## <a name="give-feedback-to-the-user"></a>Envoyer des commentaires à l’utilisateur

1. Ouvrez Circle.xaml.cs ou Circle.xaml.vb.

2. Ajoutez la substitution <xref:System.Windows.UIElement.OnGiveFeedback%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.GiveFeedback> l’événement.

     [!code-csharp[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ongivefeedback)]
     [!code-vb[DragDropWalkthrough#OnGiveFeedback](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ongivefeedback)]

     Ce <xref:System.Windows.UIElement.OnGiveFeedback%2A> remplacement effectue les tâches suivantes:

    - Vérifie les <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> valeurs qui sont définies dans le gestionnaire d’événements <xref:System.Windows.UIElement.DragOver> de la cible de déplacement.

    - Définit un curseur personnalisé en fonction de <xref:System.Windows.GiveFeedbackEventArgs.Effects%2A> la valeur. Le curseur a pour objectif de fournir des commentaires visuels à l’utilisateur sur l’effet du déplacement des données.

3. Appuyez sur **F5** pour générer et exécuter l’application.

4. Faites glisser l’un des contrôles de cercle sur les panneaux, l’autre cercle et <xref:System.Windows.Controls.TextBox>le. Notez que les curseurs sont maintenant les curseurs personnalisés que vous avez spécifiés <xref:System.Windows.UIElement.OnGiveFeedback%2A> dans le remplacement.

     ![Glisser-déplacer avec des curseurs personnalisés](./media/dragdrop-customcursor.png "DragDrop_CustomCursor")

5. Sélectionnez le texte `green` <xref:System.Windows.Controls.TextBox>à partir du.

6. Faites glisser le texte `green` sur un contrôle de cercle. Notez que les curseurs par défaut sont affichés pour indiquer les effets de l’opération de glisser-déplacer. Le curseur de commentaire est toujours défini par la source de glissement.

## <a name="implement-drop-target-events-in-the-user-control"></a>Implémenter les événements cible de déplacement dans le contrôle utilisateur
 Dans cette section, vous indiquez que le contrôle utilisateur est une cible de déplacement, vous substituez les méthodes qui permettent au contrôle utilisateur d’être une cible de déplacement et vous traitez les données qui sont déplacées sur celui-ci.

### <a name="to-enable-the-user-control-to-be-a-drop-target"></a>Pour permettre au contrôle utilisateur d’être une cible de déplacement

1. Ouvrez Circle.xaml.

2. Dans la balise d’ouverture <xref:System.Windows.Controls.UserControl> , ajoutez la `true`propriété et affectez-lui la <xref:System.Windows.UIElement.AllowDrop%2A> valeur.

     [!code-xaml[DragDropWalkthrough#UCTagXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml#uctagxaml)]

La <xref:System.Windows.UIElement.OnDrop%2A> méthode est appelée lorsque la <xref:System.Windows.UIElement.AllowDrop%2A> propriété a la valeur `true` et que les données de la source de glissement sont déplacées sur le contrôle utilisateur Circle. Dans cette méthode, vous traitez les données qui ont été déplacées et appliquez les données au cercle.

### <a name="to-process-the-dropped-data"></a>Pour traiter les données déplacées

1. Ouvrez Circle.xaml.cs ou Circle.xaml.vb.

2. Ajoutez la substitution <xref:System.Windows.UIElement.OnDrop%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.Drop> l’événement.

     [!code-csharp[DragDropWalkthrough#OnDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondrop)]
     [!code-vb[DragDropWalkthrough#OnDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondrop)]

     Ce <xref:System.Windows.UIElement.OnDrop%2A> remplacement effectue les tâches suivantes:

    - Utilise la <xref:System.Windows.DataObject.GetDataPresent%2A> méthode pour vérifier si les données glissées contiennent un objet String.

    - Utilise la <xref:System.Windows.DataObject.GetData%2A> méthode pour extraire les données de chaîne si elles sont présentes.

    - Utilise un <xref:System.Windows.Media.BrushConverter> pour essayer de convertir la chaîne <xref:System.Windows.Media.Brush>en.

    - Si la conversion réussit, applique le pinceau au <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Ellipse> du qui fournit l’interface utilisateur du contrôle de cercle.

    - Marque l' <xref:System.Windows.UIElement.Drop> événement comme géré. Vous devez marquer l’événement de déplacement comme étant géré pour que les autres éléments qui reçoivent cet événement sachent que le contrôle utilisateur de cercle l’a géré.

3. Appuyez sur **F5** pour générer et exécuter l’application.

4. Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.

5. Faites glisser le texte vers un contrôle de cercle et déplacez-le. Le cercle passe du bleu au vert.

     ![Convertir une chaîne en pinceau](./media/dragdrop-dropgreentext.png "DragDrop_DropGreenText")

6. Tapez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.

7. Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox>.

8. Faites le glisser vers un contrôle de cercle et déplacez-le. Notez que le curseur change pour indiquer que le déplacement est autorisé, mais la couleur du cercle ne change pas, car `gre` n’est pas une couleur valide.

9. Faites glisser le contrôle de cercle vert et déplacez-le sur le contrôle de cercle bleu. Le cercle passe du bleu au vert. Notez que le curseur affiché varie selon que <xref:System.Windows.Controls.TextBox> le ou le cercle est la source du glissement.

Le fait <xref:System.Windows.UIElement.AllowDrop%2A> de définir `true` la propriété sur et de traiter les données déplacées est tout ce qui est nécessaire pour permettre à un élément d’être une cible de déplacement. Toutefois, pour offrir une meilleure expérience utilisateur, vous devez également gérer les <xref:System.Windows.UIElement.DragEnter>événements <xref:System.Windows.UIElement.DragLeave>, et <xref:System.Windows.UIElement.DragOver> . Dans ces événements, vous pouvez effectuer des vérifications et fournir des commentaires supplémentaires à l’utilisateur avant de déplacer les données.

Quand les données sont glissées sur le contrôle utilisateur de cercle, le contrôle doit notifier la source de glissement si elle peut ou non traiter les données en cours de glissement. Si le contrôle ne sait pas comment traiter les données, il doit refuser le déplacement. Pour ce faire, vous allez gérer l' <xref:System.Windows.UIElement.DragOver> événement et définir la <xref:System.Windows.DragEventArgs.Effects%2A> propriété.

### <a name="to-verify-that-the-data-drop-is-allowed"></a>Pour vérifier que le déplacement de données est autorisé

1. Ouvrez Circle.xaml.cs ou Circle.xaml.vb.

2. Ajoutez la substitution <xref:System.Windows.UIElement.OnDragOver%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.DragOver> l’événement.

     [!code-csharp[DragDropWalkthrough#OnDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragover)]
     [!code-vb[DragDropWalkthrough#OnDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragover)]

     Ce <xref:System.Windows.UIElement.OnDragOver%2A> remplacement effectue les tâches suivantes:

    - Affecte la valeur <xref:System.Windows.DragEventArgs.Effects%2A> à la propriété <xref:System.Windows.DragDropEffects.None>.

    - Effectue les mêmes vérifications que celles effectuées dans la <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si le contrôle utilisateur Circle peut traiter les données glissées.

    - Si le contrôle utilisateur peut traiter les données, affecte à <xref:System.Windows.DragEventArgs.Effects%2A> la propriété <xref:System.Windows.DragDropEffects.Copy> la <xref:System.Windows.DragDropEffects.Move>valeur ou.

3. Appuyez sur **F5** pour générer et exécuter l’application.

4. Sélectionnez le texte `gre` dans le <xref:System.Windows.Controls.TextBox>.

5. Faites glisser le texte vers un contrôle de cercle. Notez que le curseur change à présent pour indiquer que le déplacement n’est pas autorisé, car `gre` n’est pas une couleur valide.

 Vous pouvez améliorer l’expérience utilisateur en appliquant un aperçu de l’opération de déplacement. Pour le contrôle utilisateur Circle, vous allez substituer les <xref:System.Windows.UIElement.OnDragEnter%2A> méthodes <xref:System.Windows.UIElement.OnDragLeave%2A> et. Lorsque les données sont glissées sur le contrôle, l’arrière- <xref:System.Windows.Shapes.Shape.Fill%2A> plan actuel est enregistré dans une variable d’espace réservé. La chaîne est ensuite convertie en pinceau et appliquée au <xref:System.Windows.Shapes.Ellipse> qui fournit l’interface utilisateur du cercle. Si les données sont déplacées en dehors du cercle sans être supprimées, <xref:System.Windows.Shapes.Shape.Fill%2A> la valeur d’origine est réappliquée au cercle.

### <a name="to-preview-the-effects-of-the-drag-and-drop-operation"></a>Pour afficher un aperçu du résultat de l’opération de glisser-déplacer

1. Ouvrez Circle.xaml.cs ou Circle.xaml.vb.

2. Dans la classe Circle, déclarez une <xref:System.Windows.Media.Brush> variable privée `_previousFill` nommée et initialisez- `null`la sur.

     [!code-csharp[DragDropWalkthrough#Brush](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#brush)]
     [!code-vb[DragDropWalkthrough#Brush](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#brush)]

3. Ajoutez la substitution <xref:System.Windows.UIElement.OnDragEnter%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.DragEnter> l’événement.

     [!code-csharp[DragDropWalkthrough#OnDragEnter](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragenter)]
     [!code-vb[DragDropWalkthrough#OnDragEnter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragenter)]

     Ce <xref:System.Windows.UIElement.OnDragEnter%2A> remplacement effectue les tâches suivantes:

    - Enregistre la <xref:System.Windows.Shapes.Shape.Fill%2A> propriété <xref:System.Windows.Shapes.Ellipse> de dans la `_previousFill` variable.

    - Effectue les mêmes vérifications que celles effectuées dans la <xref:System.Windows.UIElement.OnDrop%2A> méthode pour déterminer si les données peuvent être converties <xref:System.Windows.Media.Brush>en.

    - Si les données sont converties en <xref:System.Windows.Media.Brush>valides, l’applique <xref:System.Windows.Shapes.Shape.Fill%2A> à l' <xref:System.Windows.Shapes.Ellipse>objet de l’objet.

4. Ajoutez la substitution <xref:System.Windows.UIElement.OnDragLeave%2A> suivante pour fournir la gestion de classe pour <xref:System.Windows.UIElement.DragLeave> l’événement.

     [!code-csharp[DragDropWalkthrough#OnDragLeave](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/Circle.xaml.cs#ondragleave)]
     [!code-vb[DragDropWalkthrough#OnDragLeave](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/Circle.xaml.vb#ondragleave)]

     Ce <xref:System.Windows.UIElement.OnDragLeave%2A> remplacement effectue les tâches suivantes:

    - Applique l' <xref:System.Windows.Media.Brush> enregistrement dans la `_previousFill` <xref:System.Windows.Shapes.Shape.Fill%2A>variableau du quifournitl’interfaceutilisateurducontrôleutilisateurdecercle.<xref:System.Windows.Shapes.Ellipse>

5. Appuyez sur **F5** pour générer et exécuter l’application.

6. Sélectionnez le texte `green` dans le <xref:System.Windows.Controls.TextBox>.

7. Faites glisser le texte sur un contrôle de cercle sans le déplacer. Le cercle passe du bleu au vert.

     ![Prévisualiser les effets d’une opération de glisser-déplacer](./media/dragdrop-previeweffects.png "DragDrop_PreviewEffects")

8. Faites glisser le texte en dehors du contrôle de cercle. Le cercle passe du vert au bleu.

## <a name="enable-a-panel-to-receive-dropped-data"></a>Permettre à un panneau de recevoir des données déplacées

Dans cette section, vous allez activer les panneaux qui hébergent les contrôles utilisateur de cercle pour agir en tant que cibles de dépôt pour les données de cercle glissées. Vous allez implémenter le code qui vous permet de déplacer un cercle d’un panneau à un autre, ou de faire une copie d’un contrôle de cercle en maintenant la touche **CTRL** enfoncée tout en faisant glisser un cercle et en le déposant.

1. Ouvrez MainWindow.xaml.

2. Comme indiqué dans le code XAML suivant, dans chacun des <xref:System.Windows.Controls.StackPanel> contrôles, ajoutez des gestionnaires pour les <xref:System.Windows.UIElement.DragOver> événements <xref:System.Windows.UIElement.Drop> et. Nommez <xref:System.Windows.UIElement.DragOver> le gestionnaire d' `panel_DragOver`événements, et nommez le <xref:System.Windows.UIElement.Drop> gestionnaire `panel_Drop`d’événements,.

     [!code-xaml[DragDropWalkthrough#PanelsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml#panelsxaml)]

3. Ouvrez MainWindows.xaml.cs ou MainWindow.xaml.vb.

4. Ajoutez le code suivant pour le <xref:System.Windows.UIElement.DragOver> gestionnaire d’événements.

     [!code-csharp[DragDropWalkthrough#PanelDragOver](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldragover)]
     [!code-vb[DragDropWalkthrough#PanelDragOver](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldragover)]

     Ce <xref:System.Windows.UIElement.DragOver> gestionnaire d’événements effectue les tâches suivantes:

    - Vérifie que les données déplacées contiennent les données d’objet qui ont été empaquetées dans le <xref:System.Windows.DataObject> par le contrôle utilisateur Circle et passées dans l’appel à. <xref:System.Windows.DragDrop.DoDragDrop%2A>

    - Si les données d’objet sont présentes, vérifie si la touche **CTRL** est enfoncée.

    - Si la touche **CTRL** est enfoncée, <xref:System.Windows.DragEventArgs.Effects%2A> affecte la <xref:System.Windows.DragDropEffects.Copy>valeur à la propriété. Sinon, affectez <xref:System.Windows.DragEventArgs.Effects%2A> à <xref:System.Windows.DragDropEffects.Move>la propriété la valeur.

5. Ajoutez le code suivant pour le <xref:System.Windows.UIElement.Drop> gestionnaire d’événements.

     [!code-csharp[DragDropWalkthrough#PanelDrop](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDropWalkthrough/CS/MainWindow.xaml.cs#paneldrop)]
     [!code-vb[DragDropWalkthrough#PanelDrop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDropWalkthrough/VB/MainWindow.xaml.vb#paneldrop)]

     Ce <xref:System.Windows.UIElement.Drop> gestionnaire d’événements effectue les tâches suivantes:

    - Vérifie si l' <xref:System.Windows.UIElement.Drop> événement a déjà été géré. Par exemple, si un cercle est déposé sur un autre cercle qui gère <xref:System.Windows.UIElement.Drop> l’événement, vous ne souhaitez pas que le panneau qui contient le cercle le gère également.

    - Si l' <xref:System.Windows.UIElement.Drop> événement n’est pas géré, vérifie si la touche **CTRL** est enfoncée.

    - Si la touche **CTRL** est enfoncée <xref:System.Windows.UIElement.Drop> lorsque le se produit, effectue une copie du contrôle Circle et l’ajoute <xref:System.Windows.Controls.Panel.Children%2A> à <xref:System.Windows.Controls.StackPanel>la collection de.

    - Si la touche **CTRL** n’est pas enfoncée, déplace le <xref:System.Windows.Controls.Panel.Children%2A> cercle de la collection de son panneau <xref:System.Windows.Controls.Panel.Children%2A> parent vers la collection du panneau sur lequel il a été déposé.

    - Définit la <xref:System.Windows.DragEventArgs.Effects%2A> propriété pour indiquer à <xref:System.Windows.DragDrop.DoDragDrop%2A> la méthode si une opération de déplacement ou de copie a été effectuée.

6. Appuyez sur **F5** pour générer et exécuter l’application.

7. Sélectionnez le texte `green` <xref:System.Windows.Controls.TextBox>à partir du.

8. Faites glisser le texte sur un contrôle de cercle et déplacez-le.

9. Faites glisser un contrôle de cercle du panneau gauche vers le panneau droit et déplacez-le. Le cercle est supprimé de la <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau gauche et ajouté à la collection Children du panneau droit.

10. Faites glisser un contrôle Circle du panneau dans lequel il se trouve et déposez-le tout en appuyant sur la touche **CTRL** . Le cercle est copié et la copie est ajoutée à la <xref:System.Windows.Controls.Panel.Children%2A> collection du panneau de réception.

     ![Glissement d'un cercle en maintenant la touche CTRL enfoncée](./media/dragdrop-paneldrop.png "DragDrop_PanelDrop")

## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du glisser-déplacer](drag-and-drop-overview.md)
