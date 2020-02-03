---
title: Hériter d’un contrôle
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 713ccf97a73ce9684b9124a121369f22751861d0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740141"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a>Procédure pas à pas : hériter d’un contrôle Windows Forms avec C\#

Avec C#, vous pouvez créer des contrôles personnalisés puissants par le biais de *l’héritage*. L’héritage vous permet de créer des contrôles qui conservent toutes les fonctionnalités inhérentes des contrôles Windows Forms standard, tout en intégrant des fonctionnalités personnalisées. Dans cette procédure pas à pas, vous allez créer un contrôle hérité simple appelé `ValueButton`. Ce bouton hérite des fonctionnalités du contrôle de <xref:System.Windows.Forms.Button> Windows Forms standard et expose une propriété personnalisée appelée `ButtonValue`.

## <a name="create-the-project"></a>Créer le projet

Lorsque vous créez un nouveau projet, vous spécifiez son nom afin de définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et de vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Pour créer la bibliothèque de contrôles ValueButtonLib et le contrôle ValueButton

1. Dans Visual Studio, créez un projet de **bibliothèque de contrôles Windows Forms** , puis nommez-le **ValueButtonLib**.

     Le nom du projet, `ValueButtonLib`, est également assigné à l’espace de noms racine par défaut. L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly. Par exemple, si deux assemblies contiennent des composants nommés `ValueButton`, vous pouvez spécifier votre composant `ValueButton` à l’aide de `ValueButtonLib.ValueButton`. Pour plus d’informations, consultez l’article [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md).

2. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **UserControl1.cs**, puis sélectionnez **Renommer** dans le menu contextuel. Remplacez le nom de fichier par **ValueButton.cs**. Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « `UserControl1` ».

3. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.cs**, puis sélectionnez **Afficher le code**.

4. Localisez la ligne d’instruction `class`, `public partial class ValueButton`et remplacez le type dont hérite ce contrôle <xref:System.Windows.Forms.UserControl> par <xref:System.Windows.Forms.Button>. Cela permet à votre contrôle hérité d’hériter de toutes les fonctionnalités du contrôle <xref:System.Windows.Forms.Button>.

5. Dans **l’Explorateur de solutions**, ouvrez le nœud **ValueButton.cs** pour afficher le fichier de code généré par le concepteur, **ValueButton.Designer.cs**. Ouvrez ce fichier dans **l’éditeur de code**.

6. Recherchez la méthode `InitializeComponent` et supprimez la ligne qui affecte la propriété <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>. Cette propriété n’existe pas dans le contrôle <xref:System.Windows.Forms.Button>.

7. Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.

    > [!NOTE]
    > Plus aucun concepteur visuel n’est disponible. Étant donné que le contrôle <xref:System.Windows.Forms.Button> effectue sa propre peinture, vous ne pouvez pas modifier son apparence dans le concepteur. Sa représentation visuelle sera exactement la même que celle de la classe dont elle hérite (autrement dit, <xref:System.Windows.Forms.Button>), sauf si elle est modifiée dans le code. Vous pouvez toujours ajouter sur l’aide de conception des composants n’ayant aucun élément d’interface utilisateur.

## <a name="add-a-property-to-your-inherited-control"></a>Ajouter une propriété à votre contrôle hérité

Les contrôles Windows Forms hérités permettent notamment de créer des contrôles ayant le même aspect que les contrôles Windows Forms standard, mais qui exposent des propriétés personnalisées. Dans cette section, vous allez ajouter une propriété appelée `ButtonValue` à votre contrôle.

### <a name="to-add-the-value-property"></a>Pour ajouter la propriété Valeur

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.cs**, puis cliquez sur **Afficher le code** dans le menu contextuel.

2. Recherchez l’instruction `class`. Saisissez le code suivant immédiatement après `{` :

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     Ce code définit les méthodes utilisées pour stocker et récupérer la propriété `ButtonValue`. L’instruction `get` définit la valeur retournée à la valeur stockée dans la variable privée `varValue`et l’instruction `set` définit la valeur de la variable privée à l’aide du mot clé `value`.

3. Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.

## <a name="test-the-control"></a>Tester le contrôle

Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur. Pour tester votre contrôle, vous devez fournir un projet de test dans lequel il sera exécuté. Vous devez également rendre votre contrôle accessible au projet de test en le générant (compilant). Dans cette section, vous allez générer votre contrôle et le tester dans un environnement Windows Form.

### <a name="to-build-your-control"></a>Pour générer votre contrôle

Dans le menu **Générer** , cliquez sur **Générer la solution**. L’opération doit s’exécuter sans aucun avertissement ou erreur de compilation.

### <a name="to-create-a-test-project"></a>Pour créer un projet de test

1. Dans le menu **Fichier**, pointez vers**Ajouter**, puis cliquez sur **Nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet**.

2. Sélectionnez le nœud **Windows** sous le nœud **Visual C#** , puis cliquez sur **Application Windows Forms**.

3. Dans la zone **nom** , entrez **test**.

4. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre projet de test, puis sélectionnez **Ajouter une référence** dans le menu contextuel pour afficher la boîte de dialogue **Ajouter une référence**.

5. Cliquez sur l’onglet intitulé **Projets**. Votre projet ValueButtonLib sera listé sous **nom du projet**. Double-cliquez sur le projet pour ajouter la référence au projet de test.

6. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test**, puis sélectionnez **Générer**.

### <a name="to-add-your-control-to-the-form"></a>Pour ajouter votre contrôle au formulaire

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.cs** et sélectionnez **Concepteur de vues** dans le menu contextuel.

2. Dans la **boîte à outils**, sélectionnez **composants ValueButtonLib**. Double-cliquez sur **ValueButton**.

     Un élément **ValueButton** apparaît sur le formulaire.

3. Cliquez avec le bouton droit sur l’élément **ValueButton** et sélectionnez **Propriétés** dans le menu contextuel.

4. Dans la fenêtre **Propriété**, examinez les propriétés de ce contrôle. Notez qu’ils sont identiques aux propriétés exposées par un bouton standard, à ceci près qu’il existe une propriété supplémentaire, ButtonValue.

5. Affectez à la propriété **ButtonValue** la valeur **5**.

6. Dans l’onglet **tous les Windows Forms** de la **boîte à outils**, double-cliquez sur **étiquette** pour ajouter un contrôle de <xref:System.Windows.Forms.Label> à votre formulaire.

7. Déplacez l’étiquette au centre du formulaire.

8. Double-cliquez sur `valueButton1`.

     **L’éditeur de code** s’ouvre à l’événement `valueButton1_Click`.

9. Saisissez la ligne de code suivante.

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test** et sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.

11. Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.

     `Form1` s’affiche.

12. Cliquez sur `valueButton1`.

     Le chiffre « 5 » s’affiche dans `label1`, ce qui prouve que la propriété `ButtonValue` de votre contrôle hérité a été définie sur `label1` via la méthode `valueButton1_Click`. Par conséquent, votre contrôle `ValueButton` hérite de toutes les fonctionnalités du bouton Windows Forms standard, mais expose en outre une propriété personnalisée supplémentaire.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour afficher un contrôle dans la boîte de dialogue Choisir des éléments de boîte à outils](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Procédure pas à pas : création d'un contrôle composite à l'aide de Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
