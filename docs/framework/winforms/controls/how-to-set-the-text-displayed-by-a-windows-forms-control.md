---
title: 'Procédure : définir le texte affiché par un contrôle Windows Forms'
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 887aa5ec9b97770903cd87459d6df5adc3f7ddf0
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666152"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Procédure : Définir le texte affiché par un contrôle Windows Forms

Les contrôles Windows Forms affichent généralement du texte lié à la fonction principale du contrôle. Par exemple, un <xref:System.Windows.Forms.Button> contrôle affiche généralement une légende qui indique l’action qui sera exécutée si l’utilisateur clique sur le bouton. Pour tous les contrôles, vous pouvez définir ou retourner le texte à l'aide de la propriété <xref:System.Windows.Forms.Control.Text%2A>. Vous pouvez modifier la police en utilisant la propriété <xref:System.Windows.Forms.Control.Font%2A>.

Vous pouvez également définir le texte à l’aide du [Concepteur](#designer).

## <a name="programmatic"></a>Par programme

1. Affectez une chaîne comme valeur de la propriété <xref:System.Windows.Forms.Control.Text%2A>.

   Pour créer une clé d’accès soulignée, incluez une esperluette (&) avant la lettre qui sera la touche d’accès.

2. Affectez un objet de type <xref:System.Drawing.Font> comme valeur de la propriété <xref:System.Windows.Forms.Control.Font%2A>.

    ```vb
    Button1.Text = "Click here to save changes"
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)
    ```

    ```csharp
    button1.Text = "Click here to save changes";
    button1.Font = new Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point);
    ```

    ```cpp
    button1->Text = "Click here to save changes";
    button1->Font = new System::Drawing::Font("Arial", 10, FontStyle::Bold, GraphicsUnit::Point);
    ```

    > [!NOTE]
    > Vous pouvez utiliser un caractère d'échappement pour afficher un caractère spécial dans des éléments d'interface utilisateur qui l'interpréteraient normalement différemment, tels que des éléments de menu. Par exemple, la ligne de code suivante définit le texte de l’élément de menu pour qu’il Lise «& Now pour un élément totalement différent»:

    ```vb
    MPMenuItem.Text = "&& Now For Something Completely Different"
    ```

    ```csharp
    mpMenuItem.Text = "&& Now For Something Completely Different";
    ```

    ```cpp
    mpMenuItem->Text = "&& Now For Something Completely Different";
    ```

## <a name="designer"></a>Designer

1. Dans la fenêtre **Propriétés** de Visual Studio, définissez la propriété **Text** du contrôle sur une chaîne appropriée.

   Pour créer une touche de raccourci soulignée, incluez une esperluette (&) avant la lettre qui sera la touche de raccourci.

2. Dans la fenêtre **Propriétés** , sélectionnez le bouton de sélection![(bouton de sélection (...) dans le fenêtre Propriétés de](./media/visual-studio-ellipsis-button.png)Visual Studio) en regard de la propriété **font** .

   Dans la boîte de dialogue police standard, sélectionnez la police, le style de police, la taille, les effets (tels que le barré ou le soulignement) et le script souhaité.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [Guide pratique : Créer des clés d’accès pour les contrôles de Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md)
- [Guide pratique : Répondre à Windows Forms clics de bouton](how-to-respond-to-windows-forms-button-clicks.md)
