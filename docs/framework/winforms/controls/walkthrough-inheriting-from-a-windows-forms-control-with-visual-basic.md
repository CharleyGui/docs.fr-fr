---
title: 'Procédure pas à pas : héritage d’un contrôle Windows Forms avec Visual Basic'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 0891b64fdb26953ab90f3da931f04513ac9e8bcf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040211"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>Procédure pas à pas : héritage d’un contrôle Windows Forms avec Visual Basic
Avec Visual Basic, vous pouvez créer des contrôles personnalisés puissants par le biais de *l’héritage*. L’héritage vous permet de créer des contrôles qui conservent toutes les fonctionnalités inhérentes des contrôles Windows Forms standard, tout en intégrant des fonctionnalités personnalisées. Dans cette procédure pas à pas, vous allez créer un contrôle hérité simple appelé `ValueButton`. Ce bouton hérite des fonctionnalités du contrôle de <xref:System.Windows.Forms.Button> Windows Forms standard et expose une propriété personnalisée appelée `ButtonValue`.

## <a name="creating-the-project"></a>Création du projet
 Lorsque vous créez un nouveau projet, vous spécifiez son nom afin de définir l’espace de noms racine, le nom de l’assembly et le nom de projet, et de vous assurer que le composant par défaut sera placé dans l’espace de noms approprié.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Pour créer la bibliothèque de contrôles ValueButtonLib et le contrôle ValueButton

1. Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.

2. Sélectionnez le modèle de projet **bibliothèque de contrôles Windows Forms** dans la liste des projets Visual Basic, `ValueButtonLib` puis tapez dans la zone **nom** .

     Le nom du projet, `ValueButtonLib`, est également assigné à l’espace de noms racine par défaut. L’espace de noms racine est utilisé pour qualifier les noms des composants dans l’assembly. Par exemple, si deux assemblies contiennent des composants nommés `ValueButton`, vous pouvez spécifier votre composant `ValueButton` à l’aide de `ValueButtonLib.ValueButton`. Pour plus d’informations, consultez l’article [Espaces de noms dans Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).

3. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **UserControl1.vb**, puis sélectionnez **Renommer** dans le menu contextuel. Remplacez le nom de fichier par `ValueButton.vb`. Cliquez sur le bouton **Oui** lorsque l’on vous demande si vous souhaitez renommer toutes les références à l’élément de code « UserControl1 ».

4. Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.

5. Ouvrez le nœud **ValueButton.vb** pour afficher le fichier de code généré par le concepteur, **ValueButton.Designer.vb**. Ouvrez ce fichier dans **l’éditeur de code**.

6. Recherchez l' `Class` instruction, `Partial Public Class ValueButton`et changez le type de <xref:System.Windows.Forms.UserControl> à <xref:System.Windows.Forms.Button>partir duquel ce contrôle hérite de. Cela permet à votre contrôle hérité d’hériter de toutes les <xref:System.Windows.Forms.Button> fonctionnalités du contrôle.

7. Recherchez la `InitializeComponent` méthode et supprimez la ligne qui assigne <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> la propriété. Cette propriété n’existe pas dans le <xref:System.Windows.Forms.Button> contrôle.

8. Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.

     Notez que plus aucun concepteur visuel n’est disponible. Étant donné <xref:System.Windows.Forms.Button> que le contrôle effectue sa propre peinture, vous ne pouvez pas modifier son apparence dans le concepteur. Sa représentation visuelle sera exactement la même que celle de la classe dont elle hérite (autrement dit, <xref:System.Windows.Forms.Button>), sauf si elle est modifiée dans le code.

> [!NOTE]
>  Vous pouvez toujours ajouter sur l’aide de conception des composants n’ayant aucun élément d’interface utilisateur.

## <a name="adding-a-property-to-your-inherited-control"></a>Ajout d’une propriété à votre contrôle hérité
 Les contrôles Windows Forms hérités permettent notamment de créer des contrôles ayant la même apparence et le même comportement (aspect) que les contrôles Windows Forms standard, mais qui exposent des propriétés personnalisées. Dans cette section, vous allez ajouter une propriété appelée `ButtonValue` à votre contrôle.

### <a name="to-add-the-value-property"></a>Pour ajouter la propriété Valeur

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **ValueButton.vb**, puis cliquez sur **Afficher le code** dans le menu contextuel.

2. Recherchez l’instruction `Public Class ValueButton`. Juste en dessous de cette instruction, saisissez le code suivant :

    ```vb
    ' Creates the private variable that will store the value of your
    ' property.
    Private varValue as integer
    ' Declares the property.
    Property ButtonValue() as Integer
    ' Sets the method for retrieving the value of your property.
       Get
          Return varValue
       End Get
    ' Sets the method for setting the value of your property.
       Set(ByVal Value as Integer)
          varValue = Value
       End Set
    End Property
    ```

     Ce code définit les méthodes utilisées pour stocker et récupérer la propriété `ButtonValue`. L’instruction `Get` définit la valeur retournée à la valeur stockée dans la variable privée `varValue`et l’instruction `Set` définit la valeur de la variable privée à l’aide du mot clé `Value`.

3. Dans le menu **Fichier**, sélectionnez **Enregistrer tout** pour enregistrer le projet.

## <a name="testing-your-control"></a>Test de votre contrôle
 Les contrôles ne sont pas des projets autonomes ; ils doivent être hébergés dans un conteneur. Pour tester votre contrôle, vous devez fournir un projet de test dans lequel il sera exécuté. Vous devez également rendre votre contrôle accessible au projet de test en le générant (compilant). Dans cette section, vous allez générer votre contrôle et le tester dans un environnement Windows Form.

### <a name="to-build-your-control"></a>Pour générer votre contrôle

1. Dans le menu **Générer** , cliquez sur **Générer la solution**.

     L’opération doit s’exécuter sans aucun avertissement ou erreur de compilation.

### <a name="to-create-a-test-project"></a>Pour créer un projet de test

1. Dans le menu **Fichier**, pointez vers**Ajouter**, puis cliquez sur **Nouveau projet** pour ouvrir la boîte de dialogue **Ajouter un nouveau projet**.

2. Sélectionnez le nœud projets Visual Basic, puis cliquez sur **Windows Forms application**.

3. Dans la zone **Nom** , tapez `Test`.

4. Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**.

5. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre projet de test, puis sélectionnez **Ajouter une référence** dans le menu contextuel pour afficher la boîte de dialogue **Ajouter une référence**.

6. Cliquez sur l’onglet **Projets**.

7. Cliquez sur l’onglet intitulé **Projets**. Votre projet `ValueButtonLib` s’affiche sous **Nom du projet**. Double-cliquez sur le projet pour ajouter la référence au projet de test.

8. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test**, puis sélectionnez **Générer**.

### <a name="to-add-your-control-to-the-form"></a>Pour ajouter votre contrôle au formulaire

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Form1.vb** et sélectionnez **Concepteur de vues** dans le menu contextuel.

2. Dans la **boîte à outils**, cliquez sur **Composants ValueButtonLib**. Double-cliquez sur **ValueButton**.

     Un élément **ValueButton** apparaît sur le formulaire.

3. Cliquez avec le bouton droit sur l’élément **ValueButton** et sélectionnez **Propriétés** dans le menu contextuel.

4. Dans la fenêtre **Propriété**, examinez les propriétés de ce contrôle. Notez qu’elles sont identiques aux propriétés exposées par un bouton standard, à la différence près qu’il y a une propriété en plus, `ButtonValue`.

5. Affectez à la propriété `ButtonValue` la valeur `5`.

6. Sous l’onglet **tous les Windows Forms** de la **boîte à outils**, double-cliquez sur <xref:System.Windows.Forms.Label> **étiquette** pour ajouter un contrôle à votre formulaire.

7. Déplacez l’étiquette au centre du formulaire.

8. Double-cliquez sur `ValueButton1`.

     **L’éditeur de code** s’ouvre à l’événement `ValueButton1_Click`.

9. Saisissez la ligne de code suivante.

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur **Test** et sélectionnez **Définir comme projet de démarrage** dans le menu contextuel.

11. Dans le menu **Déboguer**, sélectionnez **Démarrer le débogage**.

     `Form1` s’affiche.

12. Cliquez sur `Valuebutton1`.

     Le chiffre « 5 » s’affiche dans `Label1`, ce qui prouve que la propriété `ButtonValue` de votre contrôle hérité a été définie sur `Label1` via la méthode `ValueButton1_Click`. Par conséquent, votre contrôle `ValueButton` hérite de toutes les fonctionnalités du bouton Windows Forms standard, mais expose en outre une propriété personnalisée supplémentaire.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Création d’un contrôle composite avec Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Guide pratique pour Afficher un contrôle dans la boîte de dialogue choisir des éléments de boîte à outils](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](developing-custom-windows-forms-controls.md)
- [Éléments fondamentaux de l’héritage (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
