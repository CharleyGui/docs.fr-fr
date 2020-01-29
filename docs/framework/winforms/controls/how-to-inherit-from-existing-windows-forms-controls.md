---
title: Hériter de contrôles existants
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- custom controls [Windows Forms], inheritance
ms.assetid: 1e1fc8ea-c615-4cf0-a356-16d6df7444ab
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d0025ba136698c0a74a73e64a83fa4f526e44843
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736484"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Comment : hériter de contrôles Windows Forms existants

Si vous souhaitez étendre les fonctionnalités d’un contrôle existant, vous pouvez créer un contrôle dérivé d’un contrôle existant par héritage. Lorsque vous héritez d’un contrôle existant, vous héritez de toutes les fonctionnalités et propriétés visuelles de ce contrôle. Par exemple, si vous créez un contrôle hérité de <xref:System.Windows.Forms.Button>, votre nouveau contrôle s’affiche et agit exactement comme un contrôle <xref:System.Windows.Forms.Button> standard. Vous pourrez ensuite étendre ou modifier les fonctionnalités de votre nouveau contrôle en implémentant des méthodes et des propriétés personnalisées. Dans certains contrôles, vous pouvez également modifier l’apparence visuelle de votre contrôle hérité en substituant sa méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.

## <a name="to-create-an-inherited-control"></a>Pour créer un contrôle hérité

1. Dans Visual Studio, créez un projet d' **application de Windows Forms** .

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

    La boîte de dialogue **Ajouter un nouvel élément** s’affiche.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, double-cliquez sur **Contrôle personnalisé**.

    Un contrôle personnalisé est ajouté à votre projet.

1. Si vous utilisez :

    - Visual Basic, en haut de **Explorateur de solutions**, cliquez sur **Afficher tous les fichiers**. Développez CustomControl1.vb, puis ouvrez CustomControl1.Designer.vb dans l’éditeur de code.
    - C#, ouvrez CustomControl1.cs dans l’éditeur de code.

1. Recherchez la déclaration de classe, qui hérite de <xref:System.Windows.Forms.Control>.

1. Remplacez la classe de base par le contrôle dont vous voulez hériter.

     Par exemple, si vous souhaitez hériter de <xref:System.Windows.Forms.Button>, remplacez la déclaration de classe par ce qui suit :

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Si vous utilisez Visual Basic, enregistrez et fermez CustomControl1.Designer.vb. Ouvrez CustomControl1.vb dans l’éditeur de code.

1. Implémentez les méthodes ou propriétés personnalisées que votre contrôle intégrera.

1. Si vous souhaitez modifier l’apparence graphique de votre contrôle, substituez la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>.

    > [!NOTE]
    > Le remplacement de <xref:System.Windows.Forms.Control.OnPaint%2A> ne vous permet pas de modifier l’apparence de tous les contrôles. Les contrôles qui ont tout leur dessin effectué par Windows (par exemple, <xref:System.Windows.Forms.TextBox>) n’appellent jamais leur méthode <xref:System.Windows.Forms.Control.OnPaint%2A> et n’utilisent donc jamais le code personnalisé. Reportez-vous à la documentation d’aide relative au contrôle que vous souhaitez modifier pour déterminer si la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> est disponible. Pour obtenir la liste de tous les contrôles Windows Forms, consultez [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md). Si un contrôle n’a pas de <xref:System.Windows.Forms.Control.OnPaint%2A> listée en tant que méthode membre, vous ne pouvez pas modifier son apparence en substituant cette méthode. Pour plus d’informations sur la peinture personnalisée, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).

    ```vb
    Protected Overrides Sub OnPaint(ByVal e As _
       System.Windows.Forms.PaintEventArgs)
       MyBase.OnPaint(e)
       ' Insert code to do custom painting.
       ' If you want to completely change the appearance of your control,
       ' do not call MyBase.OnPaint(e).
    End Sub
    ```

    ```csharp
    protected override void OnPaint(PaintEventArgs pe)
    {
       base.OnPaint(pe);
       // Insert code to do custom painting.
       // If you want to completely change the appearance of your control,
       // do not call base.OnPaint(pe).
    }
    ```

1. Enregistrez et testez votre contrôle.

## <a name="see-also"></a>Voir aussi

- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
- [Guide pratique pour hériter de la classe du contrôle](how-to-inherit-from-the-control-class.md)
- [Guide pratique pour hériter de la classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Guide pratique pour créer des contrôles pour des Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Dépannage des gestionnaires d’événements hérités en Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Procédure pas à pas : héritage d’un contrôle Windows Forms](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
