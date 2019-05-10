---
title: 'Procédure : développer un contrôle Windows Forms simple'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: a190d86f5ebe258427ac4a73c16c7f271462b69c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753225"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>Procédure : développer un contrôle Windows Forms simple

Cette section vous guide à travers les étapes clés de création d’un contrôle Windows Forms personnalisé. Le contrôle simple développé dans cette procédure pas à pas permet l’alignement de ses <xref:System.Windows.Forms.Control.Text%2A> propriété à modifier. Il ne permet pas de déclencher ni de gérer des événements.

### <a name="to-create-a-simple-custom-control"></a>Pour créer un contrôle personnalisé simple

1. Définissez une classe qui dérive de <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

    ```vb
    Public Class FirstControl
       Inherits Control

    End Class
    ```

    ```csharp
    public class FirstControl:Control {}
    ```

2. Définissez des propriétés. (Vous n'êtes pas obligé définir les propriétés, car un contrôle hérite de nombreuses propriétés à partir de la <xref:System.Windows.Forms.Control> classe, mais la plupart des contrôles personnalisés définissent généralement des propriétés supplémentaires.) Le fragment de code suivant définit une propriété nommée `TextAlignment` qui `FirstControl` utilise pour mettre en forme l’affichage de la <xref:System.Windows.Forms.Control.Text%2A> héritée de la propriété <xref:System.Windows.Forms.Control>. Pour plus d’informations sur la définition des propriétés, consultez [Vue d’ensemble des propriétés](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]

     Lorsque vous définissez une propriété qui modifie l’affichage visuel du contrôle, vous devez appeler la <xref:System.Windows.Forms.Control.Invalidate%2A> méthode doit redessiner le contrôle. <xref:System.Windows.Forms.Control.Invalidate%2A> est défini dans la classe de base <xref:System.Windows.Forms.Control>.

3. Remplacer l’élément protégé <xref:System.Windows.Forms.Control.OnPaint%2A> héritée de la méthode <xref:System.Windows.Forms.Control> pour fournir la logique de rendu à votre contrôle. Si vous ne substituez pas <xref:System.Windows.Forms.Control.OnPaint%2A>, votre contrôle ne sera pas en mesure de se dessiner lui-même. Dans le fragment de code suivant, le <xref:System.Windows.Forms.Control.OnPaint%2A> méthode affiche le <xref:System.Windows.Forms.Control.Text%2A> héritée de la propriété <xref:System.Windows.Forms.Control> avec l’alignement spécifié par le `alignmentValue` champ.

     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]

4. Fournissez des attributs à votre contrôle. Les attributs permettent à un concepteur visuel d’afficher correctement votre contrôle ainsi que ses propriétés et événements au moment du design. Le fragment de code suivant applique des attributs à la propriété `TextAlignment`. Dans un concepteur tel que Visual Studio, le <xref:System.ComponentModel.CategoryAttribute.Category%2A> attribut (indiqué dans le fragment de code), la propriété à afficher sous une catégorie logique. Le <xref:System.ComponentModel.DescriptionAttribute.Description%2A> attribut entraîne une chaîne descriptive à afficher en bas de la **propriétés** fenêtre lorsque le `TextAlignment` propriété est sélectionnée. Pour plus d’informations sur les attributs, consultez [Attributs en mode design pour les composants](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120)).

     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]

5. (facultatif) Fournissez des ressources pour votre contrôle. Vous pouvez fournir une ressource, par exemple une image bitmap, pour votre contrôle en utilisant une option de compilateur (`/res` pour C#) afin d’empaqueter des ressources avec votre contrôle. Au moment de l’exécution, la ressource peut être récupérée à l’aide des méthodes de la <xref:System.Resources.ResourceManager> classe. Pour plus d’informations sur la création et l’utilisation de ressources, consultez [Ressources dans des applications de bureau](../../resources/index.md).

6. Compilez et déployez votre contrôle. Pour compiler et déployer `FirstControl,`, procédez comme suit :

    1. Enregistrez le code de l’exemple suivant dans un fichier source (par exemple, FirstControl.cs ou FirstControl.vb).

    2. Compilez le code source dans un assembly et enregistrez-le dans le répertoire de votre application. Pour ce faire, exécutez la commande suivante à partir du répertoire qui contient le fichier source.

        ```console
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb
        ```

        ```console
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs
        ```

         L’option du compilateur `/t:library` indique au compilateur que l’assembly créé est une bibliothèque (et non un exécutable). L’option `/out` spécifie le chemin d’accès et le nom de l’assembly. L’option `/r` fournit le nom des assemblys référencés par votre code. Dans cet exemple, vous créez un assembly privé que seules vos applications peuvent utiliser. Par conséquent, vous devez l’enregistrer dans le répertoire de votre application. Pour plus d’informations sur l’empaquetage et le déploiement d’un contrôle à des fins de distribution, consultez [Déploiement](../../deployment/index.md).

L’exemple suivant présente le code pour `FirstControl`. Le contrôle est inséré dans l’espace de noms `CustomWinControls`. Un espace de noms fournit un regroupement logique des types connexes. Vous pouvez créer votre contrôle dans un espace de noms nouveau ou existant. En C#, la déclaration `using` (en Visual Basic, `Imports`) autorise l’accès aux types à partir d’un espace de noms sans le nom qualifié complet du type. Dans l’exemple suivant, le `using` déclaration permet au code d’accéder à la classe <xref:System.Windows.Forms.Control> de <xref:System.Windows.Forms?displayProperty=nameWithType> simplement <xref:System.Windows.Forms.Control> au lieu de devoir utiliser le nom qualifié complet <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.

[!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
[!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]

## <a name="using-the-custom-control-on-a-form"></a>Utilisation du contrôle personnalisé dans un formulaire

L’exemple suivant montre un formulaire simple qui utilise `FirstControl`. Il crée trois instances de `FirstControl`, chacune présentant une valeur différente pour la propriété `TextAlignment`.

#### <a name="to-compile-and-run-this-sample"></a>Pour compiler et exécuter cet exemple

1. Enregistrez le code de l’exemple suivant dans un fichier source (SimpleForm.cs ou SimpleForms.vb).

2. Compilez le code source dans un assembly exécutable en exécutant la commande suivante à partir du répertoire contenant le fichier source.

    ```console
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb
    ```

    ```console
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs
    ```

     CustomWinControls.dll est l’assembly qui contient la classe `FirstControl`. Cet assembly doit se trouver dans le même répertoire que le fichier source pour le formulaire qui y accède (SimpleForm.cs ou SimpleForms.vb).

3. Exécutez SimpleForm.exe à l’aide de la commande suivante.

    ```console
    SimpleForm
    ```

[!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
[!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]

## <a name="see-also"></a>Voir aussi

- [Propriétés dans les contrôles Windows Forms](properties-in-windows-forms-controls.md)
- [Événements dans les contrôles Windows Forms](events-in-windows-forms-controls.md)
