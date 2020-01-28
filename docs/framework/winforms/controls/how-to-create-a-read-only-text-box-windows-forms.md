---
title: 'Comment : créer une zone de texte en lecture seule'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 17ae9524009c687cd62fb315f842e188e120ac68
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731269"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Comment : créer une zone de texte en lecture seule (Windows Forms)

Vous pouvez transformer une zone de texte modifiable Windows Forms en contrôle en lecture seule. Par exemple, la zone de texte peut afficher une valeur qui est généralement modifiée, mais peut ne pas l’être actuellement, en raison de l’état de l’application.

## <a name="to-create-a-read-only-text-box"></a>Pour créer une zone de texte en lecture seule

1. Affectez à la propriété <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> du contrôle <xref:System.Windows.Forms.TextBox> la valeur `true`. Lorsque la propriété a la valeur `true`, les utilisateurs peuvent toujours faire défiler le texte et le mettre en surbrillance dans une zone de texte sans autoriser les modifications. Une commande de **copie** est fonctionnelle dans une zone de texte, contrairement aux commandes **couper** et **coller** .

    > [!NOTE]
    > La propriété <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> affecte uniquement l’interaction de l’utilisateur au moment de l’exécution. Vous pouvez toujours modifier le contenu de la zone de texte par programmation au moment de l’exécution en modifiant la propriété <xref:System.Windows.Forms.TextBox.Text%2A> de la zone de texte.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- [Vue d’ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
- [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Guide pratique pour insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
