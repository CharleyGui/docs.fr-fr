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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f051d7a51a5f4ff8debf40fafbb8acfd8f7098f5
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182631"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a>Procédure pas à pas : Sérialiser des collections de types standard

Vos contrôles personnalisés exposent parfois une collection en tant que propriété. Cette procédure pas à pas montre comment <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> utiliser la classe pour contrôler la façon dont une collection est sérialisée au moment du Design. L’application <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> de la valeur à votre propriété de collection garantit que la propriété sera sérialisée.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Sérialiser des collections de types standard avec DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).

## <a name="prerequisites"></a>Prérequis

Cette procédure pas à pas nécessite Visual Studio.

## <a name="create-a-control-with-a-serializable-collection"></a>Créer un contrôle avec une collection sérialisable

La première étape consiste à créer un contrôle qui a une collection sérialisable en tant que propriété. Vous pouvez modifier le contenu de cette collection à l’aide de l' **éditeur de collections**, auquel vous pouvez accéder à partir de la fenêtre **Propriétés** .

1. Dans Visual Studio, créez un projet de bibliothèque de contrôles Windows, puis nommez-le **SerializationDemoControlLib**.

2. `UserControl1` Renommez `SerializationDemoControl`-le. Pour plus d’informations, consultez [Renommer un symbole de code refactorisation](/visualstudio/ide/reference/rename).

3. Dans la fenêtre **Propriétés** , affectez à la <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> propriété la valeur **10**.

4. Placez un <xref:System.Windows.Forms.TextBox> contrôle dans le `SerializationDemoControl`.

5. Sélectionnez le contrôle <xref:System.Windows.Forms.TextBox>. Dans la fenêtre **Propriétés** , définissez les propriétés suivantes.

    |Property|Remplacer par|
    |--------------|---------------|
    |**Multiline**|`true`|
    |**Sa**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |**ScrollBars**|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. Dans l' **éditeur de code**, déclarez un champ de `stringsValue` tableau `SerializationDemoControl`de chaînes nommé dans.

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. Définissez la `Strings` propriété sur le `SerializationDemoControl`.

   > [!NOTE]
   > La <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> valeur est utilisée pour activer la sérialisation de la collection.

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. Appuyez sur **F5** pour générer le projet et exécuter votre contrôle dans le **conteneur de test UserControl**.

9. Recherchez la propriété **Strings** dans <xref:System.Windows.Forms.PropertyGrid> le du **conteneur de test UserControl**. Sélectionnez la **propriété chaînes** , puis cliquez sur le bouton![de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio](./media/visual-studio-ellipsis-button.png)) pour ouvrir l' **éditeur de collections String**.

10. Entrez plusieurs chaînes dans l **'éditeur de collections String**. Séparez-les en appuyant sur la touche **entrée** à la fin de chaque chaîne. Cliquez sur **OK** lorsque vous avez terminé d’entrer des chaînes.

   > [!NOTE]
   > Les chaînes que vous avez tapées <xref:System.Windows.Forms.TextBox> apparaissent dans `SerializationDemoControl`le de.

## <a name="serialize-a-collection-property"></a>Sérialiser une propriété de collection

Pour tester le comportement de sérialisation de votre contrôle, vous devez le placer dans un formulaire et modifier le contenu de la collection à l’aide de l' **éditeur de collections**. Vous pouvez voir l’état de la collection sérialisée en examinant un fichier de concepteur spécial dans lequel le **Concepteur Windows Forms** émet du code.

1. Ajoutez un projet d’application Windows à la solution. Attribuez un nom au projet `SerializationDemoControlTest`.

2. Dans la **boîte à outils**, recherchez l’onglet **Composants SerializationDemoControlLib**. Dans cet onglet, vous trouverez le `SerializationDemoControl`. Pour plus d’informations, consultez [Procédure pas à pas : Remplissage automatique de la boîte à outils](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)avec des composants personnalisés.

3. Placez un `SerializationDemoControl` sur votre formulaire.

4. Recherchez la `Strings` propriété dans la fenêtre **Propriétés** . Cliquez sur `Strings` la propriété, puis sur le![bouton de sélection (...) dans le bouton fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) pour ouvrir l' **éditeur de collections String**.

5. Tapez plusieurs chaînes dans l **'éditeur de collections String**. Séparez-les en appuyant sur **entrée** à la fin de chaque chaîne. Cliquez sur **OK** lorsque vous avez terminé d’entrer des chaînes.

    > [!NOTE]
    > Les chaînes que vous avez tapées <xref:System.Windows.Forms.TextBox> apparaissent dans `SerializationDemoControl`le de.

6. Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.

7. Ouvrez le nœud **Form1** . En dessous, il s’agit d’un fichier nommé **Form1.Designer.cs** ou **Form1. Designer. vb**. Il s’agit du fichier dans lequel le **Concepteur Windows Forms** émet du code représentant l’État au moment du design de votre formulaire et de ses contrôles enfants. Ouvrez ce fichier dans **l’éditeur de code**.

8. Ouvrez la région appelée **code généré par le Concepteur Windows Form** et recherchez la section intitulée **serializationDemoControl1**. Sous cette étiquette se trouve le code qui représente l’État sérialisé de votre contrôle. Les chaînes que vous avez tapées à l’étape 5 apparaissent dans `Strings` une assignation à la propriété. Les exemples de code suivants C# dans et Visual Basic, montrent un code similaire à ce que vous verrez si vous avez tapé les chaînes « Red », « orange » et « Yellow ».

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. Dans l' **éditeur de code**, affectez à <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>la `Strings` propriété de la propriété la valeur.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. Régénérez la solution et répétez les étapes 3 et 4.

> [!NOTE]
> Dans ce cas, le **Concepteur Windows Forms** n’émet aucune assignation à `Strings` la propriété.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous savez comment sérialiser une collection de types standard, envisagez d’intégrer vos contrôles personnalisés plus profondément dans l’environnement au moment du Design. Les rubriques suivantes décrivent comment améliorer l’intégration au moment du design de vos contrôles personnalisés :

- [Architecture au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Attributs dans les contrôles Windows Forms](attributes-in-windows-forms-controls.md)

- [Vue d’ensemble de la sérialisation du concepteur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [Procédure pas à pas : Création d’un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
