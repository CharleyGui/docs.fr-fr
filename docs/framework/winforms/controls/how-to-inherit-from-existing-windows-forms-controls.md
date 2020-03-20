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
ms.openlocfilehash: b0e0053816efde349c7e4d13d03bef5f8801c667
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849378"
---
# <a name="how-to-inherit-from-existing-windows-forms-controls"></a>Comment : hériter de contrôles Windows Forms existants

Si vous souhaitez étendre les fonctionnalités d’un contrôle existant, vous pouvez créer un contrôle dérivé d’un contrôle existant par héritage. Lorsque vous héritez d’un contrôle existant, vous héritez de toutes les fonctionnalités et propriétés visuelles de ce contrôle. Par exemple, si vous créiez <xref:System.Windows.Forms.Button>un contrôle hérité de , votre <xref:System.Windows.Forms.Button> nouveau contrôle ressemblerait et agirait exactement comme un contrôle standard. Vous pourrez ensuite étendre ou modifier les fonctionnalités de votre nouveau contrôle en implémentant des méthodes et des propriétés personnalisées. Dans certains contrôles, vous pouvez également modifier l’apparence visuelle <xref:System.Windows.Forms.Control.OnPaint%2A> de votre contrôle hérité en dominant sa méthode.

## <a name="to-create-an-inherited-control"></a>Pour créer un contrôle hérité

1. Dans Visual Studio, créez un nouveau projet **d’application Windows Forms.**

1. Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.

    La boîte de dialogue **Ajouter un nouvel élément** s'affiche.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, double-cliquez sur **Contrôle personnalisé**.

    Un contrôle personnalisé est ajouté à votre projet.

1. Si vous utilisez :

    - Visual Basic, en haut de **Solution Explorer**, cliquez sur Afficher tous **les fichiers**. Développez CustomControl1.vb, puis ouvrez CustomControl1.Designer.vb dans l’éditeur de code.
    - C, ouvert CustomControl1.cs dans l’éditeur de code.

1. Localiser la déclaration de classe, qui hérite de <xref:System.Windows.Forms.Control>.

1. Remplacez la classe de base par le contrôle dont vous voulez hériter.

     Par exemple, si vous <xref:System.Windows.Forms.Button>voulez hériter de , changer la déclaration de classe à ce qui suit:

    ```vb
    Partial Class CustomControl1
        Inherits System.Windows.Forms.Button
    ```

    ```csharp
    public partial class CustomControl1 : System.Windows.Forms.Button
    ```

1. Si vous utilisez Visual Basic, enregistrez et fermez CustomControl1.Designer.vb. Ouvrez CustomControl1.vb dans l’éditeur de code.

1. Implémentez les méthodes ou propriétés personnalisées que votre contrôle intégrera.

1. Si vous souhaitez modifier l’apparence graphique de <xref:System.Windows.Forms.Control.OnPaint%2A> votre contrôle, remplacez la méthode.

    > [!NOTE]
    > La prépondérer <xref:System.Windows.Forms.Control.OnPaint%2A> ne vous permettra pas de modifier l’apparence de tous les contrôles. Ces contrôles qui ont toute leur peinture faite <xref:System.Windows.Forms.TextBox>par Windows <xref:System.Windows.Forms.Control.OnPaint%2A> (par exemple, ) n’appellent jamais leur méthode, et donc ne sera jamais utiliser le code personnalisé. Consultez la documentation d’aide pour le contrôle particulier <xref:System.Windows.Forms.Control.OnPaint%2A> que vous souhaitez modifier pour voir si la méthode est disponible. Pour obtenir la liste de tous les contrôles Windows Forms, consultez [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md). Si un contrôle <xref:System.Windows.Forms.Control.OnPaint%2A> n’a pas énuméré comme méthode de membre, vous ne pouvez pas modifier son apparence en l’antidantant cette méthode. Pour plus d’informations sur la peinture personnalisée, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).

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
- [Comment : hériter de la classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Guide pratique pour créer des contrôles pour des Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Dépannage des gestionnaires d'événements hérités dans Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Procédure pas à pas : Hériter d’un contrôle des formulaires Windows](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
