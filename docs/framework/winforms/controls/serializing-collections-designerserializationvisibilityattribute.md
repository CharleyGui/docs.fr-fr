---
title: 'Procédure pas à pas : sérialisation des collections de types standard avec DesignerSerializationVisibilityAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 297a7080b0c34fa10f976cbbbfb48d8c35786aca
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458082"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a>Procédure pas à pas : sérialiser des collections de types standard

Vos contrôles personnalisés exposent parfois une collection en tant que propriété. Cette procédure pas à pas montre comment utiliser la classe <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> pour contrôler la façon dont une collection est sérialisée au moment du Design. L’application de la valeur <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> à votre propriété de collection garantit que la propriété sera sérialisée.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : sérialiser des collections de types standard avec DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).

## <a name="prerequisites"></a>Configuration requise

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-a-control-with-a-serializable-collection"></a>Créer un contrôle avec une collection sérialisable

La première étape consiste à créer un contrôle qui a une collection sérialisable en tant que propriété. Vous pouvez modifier le contenu de cette collection à l’aide de l' **éditeur de collections**, auquel vous pouvez accéder à partir de la fenêtre **Propriétés** .

1. Dans Visual Studio, créez un projet de bibliothèque de contrôles Windows, puis nommez-le **SerializationDemoControlLib**.

2. Renommez `UserControl1` `SerializationDemoControl`. Pour plus d’informations, consultez [Renommer un symbole de code refactorisation](/visualstudio/ide/reference/rename).

3. Dans la fenêtre **Propriétés** , affectez à la propriété <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> la valeur **10**.

4. Placez un contrôle de <xref:System.Windows.Forms.TextBox> dans le `SerializationDemoControl`.

5. Sélectionnez le contrôle <xref:System.Windows.Forms.TextBox>. Dans la fenêtre **Propriétés** , définissez les propriétés suivantes.

    |Property|Remplacer par|
    |--------------|---------------|
    |**Multiline**|`true`|
    |**Sa**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |**ScrollBars**|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. Dans l' **éditeur de code**, déclarez un champ de tableau de chaînes nommé `stringsValue` dans `SerializationDemoControl`.

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. Définissez la propriété `Strings` sur l' `SerializationDemoControl`.

   > [!NOTE]
   > La valeur <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> est utilisée pour activer la sérialisation de la collection.

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. Appuyez sur **F5** pour générer le projet et exécuter votre contrôle dans le **conteneur de test UserControl**.

9. Recherchez la propriété **Strings** dans le <xref:System.Windows.Forms.PropertyGrid> du **conteneur de test UserControl**. Sélectionnez la propriété **Strings** , puis sélectionnez les points de suspension (![le bouton de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio](./media/visual-studio-ellipsis-button.png)) pour ouvrir l' **éditeur de collections String**.

10. Entrez plusieurs chaînes dans l **'éditeur de collections String**. Séparez-les en appuyant sur la touche **entrée** à la fin de chaque chaîne. Cliquez sur **OK** lorsque vous avez terminé d’entrer des chaînes.

   > [!NOTE]
   > Les chaînes que vous avez tapées apparaissent dans le <xref:System.Windows.Forms.TextBox> du `SerializationDemoControl`.

## <a name="serialize-a-collection-property"></a>Sérialiser une propriété de collection

Pour tester le comportement de sérialisation de votre contrôle, vous devez le placer dans un formulaire et modifier le contenu de la collection à l’aide de l' **éditeur de collections**. Vous pouvez voir l’état de la collection sérialisée en examinant un fichier de concepteur spécial dans lequel le **Concepteur Windows Forms** émet du code.

1. Ajoutez un projet d’application Windows à la solution. Attribuez un nom au projet `SerializationDemoControlTest`.

2. Dans la **boîte à outils**, recherchez l’onglet **Composants SerializationDemoControlLib**. Dans cet onglet, vous trouverez la `SerializationDemoControl`. Pour plus d’informations, consultez [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

3. Placez un `SerializationDemoControl` dans votre formulaire.

4. Recherchez la propriété `Strings` dans la fenêtre **Propriétés** . Cliquez sur la propriété `Strings`, puis sur les points de suspension (![le bouton de sélection (...) du bouton Fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) pour ouvrir l' **éditeur de collections String**.

5. Tapez plusieurs chaînes dans l **'éditeur de collections String**. Séparez-les en appuyant sur **entrée** à la fin de chaque chaîne. Cliquez sur **OK** lorsque vous avez terminé d’entrer des chaînes.

    > [!NOTE]
    > Les chaînes que vous avez tapées apparaissent dans le <xref:System.Windows.Forms.TextBox> du `SerializationDemoControl`.

6. Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.

7. Ouvrez le nœud **Form1** . En dessous, il s’agit d’un fichier nommé **Form1.Designer.cs** ou **Form1. Designer. vb**. Il s’agit du fichier dans lequel le **Concepteur Windows Forms** émet du code représentant l’État au moment du design de votre formulaire et de ses contrôles enfants. Ouvrez ce fichier dans **l’éditeur de code**.

8. Ouvrez la région appelée **code généré par le Concepteur Windows Form** et recherchez la section intitulée **serializationDemoControl1**. Sous cette étiquette se trouve le code qui représente l’État sérialisé de votre contrôle. Les chaînes que vous avez tapées à l’étape 5 apparaissent dans une assignation à la propriété `Strings`. Les exemples de code suivants C# dans et Visual Basic, montrent un code similaire à ce que vous verrez si vous avez tapé les chaînes « Red », « orange » et « Yellow ».

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. Dans l' **éditeur de code**, remplacez la valeur de la <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> de la propriété `Strings` par <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. Régénérez la solution et répétez les étapes 3 et 4.

> [!NOTE]
> Dans ce cas, le **Concepteur Windows Forms** n’émet aucune assignation à la propriété `Strings`.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous savez comment sérialiser une collection de types standard, envisagez d’intégrer vos contrôles personnalisés plus profondément dans l’environnement au moment du Design. Les rubriques suivantes décrivent comment améliorer l’intégration au moment du design de vos contrôles personnalisés :

- [Architecture au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Attributs dans les contrôles Windows Forms](attributes-in-windows-forms-controls.md)

- [Vue d’ensemble de la sérialisation du concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [Procédure pas à pas : création d’un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
