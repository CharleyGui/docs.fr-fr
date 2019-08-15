---
title: 'Procédure : définir l’ordre de tabulation dans des Windows Forms'
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
ms.openlocfilehash: 5559a3a3e4e62ce9e620de23feef3cbfa0ab8f60
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039856"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Procédure : définir l’ordre de tabulation dans des Windows Forms
L’ordre de tabulation est l’ordre dans lequel un utilisateur déplace le focus d’un contrôle à un autre en appuyant sur la touche TAB. Chaque formulaire possède son propre ordre de tabulation. Par défaut, l’ordre de tabulation est le même que l’ordre dans lequel vous avez créé les contrôles. La numérotation de l’ordre des tabulations commence par zéro.

## <a name="to-set-the-tab-order-of-a-control"></a>Pour définir l’ordre de tabulation d’un contrôle

1. Dans le menu **affichage** , cliquez sur **ordre de tabulation**.

     Cela active le mode de sélection de l’ordre des onglets sur le formulaire. Un nombre (représentant la <xref:System.Windows.Forms.Control.TabIndex%2A> propriété) s’affiche dans l’angle supérieur gauche de chaque contrôle.

2. Cliquez sur les contrôles de façon séquentielle pour définir l’ordre de tabulation souhaité.

    > [!NOTE]
    >  L’emplacement d’un contrôle dans l’ordre de tabulation peut être défini sur n’importe quelle valeur supérieure ou égale à 0. Lorsque des doublons se produisent, l’ordre de plan des deux contrôles est évalué et le contrôle en haut est tabulé à la première. (L’ordre de plan est la superposition visuelle des contrôles sur un formulaire le long de l’axe z [profondeur] du formulaire. L’ordre de plan détermine les contrôles devant d’autres contrôles.) Pour plus d’informations sur l’ordre de plan, consultez [superposition d’objets sur Windows Forms](how-to-layer-objects-on-windows-forms.md).

3. Lorsque vous avez terminé, cliquez à nouveau sur **ordre de tabulation** dans le menu **affichage** pour conserver le mode d’ordre de tabulation.

    > [!NOTE]
    >  Les contrôles qui ne peuvent pas obtenir le focus, ainsi que les contrôles désactivés et invisibles, n’ont pas de <xref:System.Windows.Forms.Control.TabIndex%2A> propriété et ne sont pas inclus dans l’ordre de tabulation. Quand un utilisateur appuie sur la touche TAB, ces contrôles sont ignorés.

 Vous pouvez également définir l’ordre de tabulation dans le fenêtre Propriétés à l' <xref:System.Windows.Forms.Control.TabIndex%2A> aide de la propriété. La <xref:System.Windows.Forms.Control.TabIndex%2A> propriété d’un contrôle détermine où il est positionné dans l’ordre de tabulation. Par défaut, le premier contrôle dessiné a une <xref:System.Windows.Forms.Control.TabIndex%2A> valeur de 0, le deuxième <xref:System.Windows.Forms.Control.TabIndex%2A> a la valeur 1, et ainsi de suite.

 En outre, par défaut, un <xref:System.Windows.Forms.GroupBox> contrôle a sa propre <xref:System.Windows.Forms.Control.TabIndex%2A> valeur, qui est un nombre entier. Un <xref:System.Windows.Forms.GroupBox> contrôle lui-même ne peut pas avoir le focus au moment de l’exécution. Ainsi, chaque contrôle dans un <xref:System.Windows.Forms.GroupBox> a sa propre valeur <xref:System.Windows.Forms.Control.TabIndex%2A> décimale, à partir de. 0. Naturellement, à mesure <xref:System.Windows.Forms.Control.TabIndex%2A> que le <xref:System.Windows.Forms.GroupBox> d’un contrôle est incrémenté, les contrôles qu’il contient seront incrémentés en conséquence. Si vous avez modifié <xref:System.Windows.Forms.Control.TabIndex%2A> une valeur comprise entre 5 <xref:System.Windows.Forms.Control.TabIndex%2A> et 6, la valeur du premier contrôle dans son groupe devient automatiquement 6,0, et ainsi de suite.

 Enfin, n’importe quel contrôle de la plupart de votre formulaire peut être ignoré dans l’ordre de tabulation. En règle générale, le fait d’appuyer sur TAB successivement au moment de l’exécution sélectionne chaque contrôle dans l’ordre de tabulation. En désactivant la <xref:System.Windows.Forms.Control.TabStop%2A> propriété, vous pouvez faire en sorte qu’un contrôle soit passé dans l’ordre de tabulation du formulaire.

## <a name="to-remove-a-control-from-the-tab-order"></a>Pour supprimer un contrôle de l’ordre de tabulation

1. Affectez à `false` la <xref:System.Windows.Forms.Control.TabStop%2A> propriété du contrôle la valeur dans la fenêtre Propriétés.

     Un contrôle dont <xref:System.Windows.Forms.Control.TabStop%2A> la propriété a la valeur `false` continue à conserver sa position dans l’ordre de tabulation, même si le contrôle est ignoré lorsque vous parcourez les contrôles à l’aide de la touche Tab.

    > [!NOTE]
    >  Un groupe de cases d’option a un seul taquet de tabulation au moment de l’exécution. Le bouton sélectionné (autrement dit, le bouton <xref:System.Windows.Forms.RadioButton.Checked%2A> dont la propriété a la `true`valeur) a sa <xref:System.Windows.Forms.Control.TabStop%2A> propriété définie automatiquement `true` <xref:System.Windows.Forms.Control.TabStop%2A> sur, tandis que la propriété des autres boutons `false`a la valeur. Pour plus d’informations sur le <xref:System.Windows.Forms.RadioButton> regroupement de contrôles, consultez [regroupement Windows Forms contrôles RadioButton pour qu’ils fonctionnent comme un ensemble](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Disposition des contrôles dans les Windows Forms](arranging-controls-on-windows-forms.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
