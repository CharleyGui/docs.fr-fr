---
title: 'Comment : créer une zone de texte en lecture seule'
description: En savoir plus sur la transformation d’une zone de texte modifiable Windows Forms en une zone de texte Windows Forms en lecture seule.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [Windows Forms], read-only
- read-only text boxes
- text boxes [Windows Forms], read-only
ms.assetid: 60baa9ab-fa57-44ad-bb7c-61b05aa64296
ms.openlocfilehash: 5baa7c66d5f16560a4ea23861d563b099592957f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619362"
---
# <a name="how-to-create-a-read-only-text-box-windows-forms"></a>Comment : créer une zone de texte en lecture seule (Windows Forms)

Vous pouvez transformer une zone de texte modifiable Windows Forms en contrôle en lecture seule. Par exemple, la zone de texte peut afficher une valeur qui est généralement modifiée, mais peut ne pas l’être actuellement, en raison de l’état de l’application.

## <a name="to-create-a-read-only-text-box"></a>Pour créer une zone de texte en lecture seule

1. Affectez <xref:System.Windows.Forms.TextBox> à la propriété du contrôle la valeur <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> `true` . Lorsque la propriété a la valeur `true` , les utilisateurs peuvent toujours faire défiler et mettre en surbrillance du texte dans une zone de texte sans autoriser les modifications. Une commande de **copie** est fonctionnelle dans une zone de texte, contrairement aux commandes **couper** et **coller** .

    > [!NOTE]
    > La <xref:System.Windows.Forms.TextBoxBase.ReadOnly%2A> propriété affecte uniquement l’interaction avec l’utilisateur au moment de l’exécution. Vous pouvez toujours modifier le contenu de la zone de texte par programmation au moment de l’exécution en modifiant la <xref:System.Windows.Forms.TextBox.Text%2A> propriété de la zone de texte.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- [Vue d'ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
- [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Comment : insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Comment : sélectionner du texte dans le contrôle TextBox Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Comment : afficher des lignes multiples dans le contrôle TextBox Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
