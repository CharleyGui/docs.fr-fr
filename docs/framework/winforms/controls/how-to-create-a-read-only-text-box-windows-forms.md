---
title: 'Procédure : Créer une zone de texte en lecture seule (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 18d2f5ed2530957487ac25c3eb6240f8bc50a938
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971942"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Procédure : Créer une zone de texte en lecture seule (Windows Forms)

Vous pouvez transformer une zone de texte modifiable Windows Forms en contrôle en lecture seule. Par exemple, la zone de texte peut afficher une valeur qui est généralement modifiée, mais peut ne pas l’être actuellement, en raison de l’état de l’application.

## <a name="to-create-a-read-only-text-box"></a>Pour créer une zone de texte en lecture seule

1. Affectez <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> à`true`la propriété du contrôle la valeur. Lorsque la propriété a la `true`valeur, les utilisateurs peuvent toujours faire défiler et mettre en surbrillance du texte dans une zone de texte sans autoriser les modifications. Une commande de **copie** est fonctionnelle dans une zone de texte, contrairement aux commandes **couper** et **coller** .

    > [!NOTE]
    > La <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriété affecte uniquement l’interaction avec l’utilisateur au moment de l’exécution. Vous pouvez toujours modifier le contenu de la zone de texte par programmation au moment de <xref:System.Windows.Forms.TextBox.Text%2A> l’exécution en modifiant la propriété de la zone de texte.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- [Vue d’ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
- [Guide pratique pour Contrôler le point d’insertion dans un contrôle de zone de texte Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Guide pratique pour Créer une zone de texte de mot de passe avec le contrôle Windows Forms TextBox](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Guide pratique pour Insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Guide pratique : Sélectionner du texte dans le contrôle Windows Forms TextBox](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Guide pratique pour Afficher plusieurs lignes dans le contrôle de zone de texte Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
