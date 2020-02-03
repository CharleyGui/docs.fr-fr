---
title: Définir l’ordre de tabulation des contrôles
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d53e411bda0279271e4f73e1842c52fd6d9b3a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746830"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Comment : définir l’ordre de tabulation sur Windows Forms

L’ordre de tabulation est l’ordre dans lequel un utilisateur déplace le focus d’un contrôle à un autre en appuyant sur la touche Tab. Chaque formulaire possède son propre ordre de tabulation. Par défaut, l’ordre de tabulation est le même que l’ordre dans lequel vous avez créé les contrôles. La numérotation de l’ordre des tabulations commence par zéro.

## <a name="to-set-the-tab-order-of-a-control"></a>Pour définir l’ordre de tabulation d’un contrôle

1. Dans Visual Studio, dans le menu **affichage** , sélectionnez **ordre de tabulation**.

   Cela active le mode de sélection de l’ordre des onglets sur le formulaire. Un nombre (représentant la propriété <xref:System.Windows.Forms.Control.TabIndex%2A>) s’affiche dans l’angle supérieur gauche de chaque contrôle.

2. Cliquez sur les contrôles de façon séquentielle pour définir l’ordre de tabulation souhaité.

   > [!NOTE]
   > L’emplacement d’un contrôle dans l’ordre de tabulation peut être défini sur n’importe quelle valeur supérieure ou égale à 0. Lorsque des doublons se produisent, l’ordre de plan des deux contrôles est évalué et le contrôle en haut est tabulé à la première. (L’ordre de plan est la superposition visuelle des contrôles sur un formulaire le long de l’axe z [profondeur] du formulaire. L’ordre de plan détermine les contrôles devant d’autres contrôles.) Pour plus d’informations sur l’ordre de plan, consultez [superposition d’objets sur Windows Forms](how-to-layer-objects-on-windows-forms.md).

3. Lorsque vous avez terminé, sélectionnez l' **ordre de tabulation** dans le menu **affichage** pour conserver le mode d’ordre de tabulation.

   > [!NOTE]
   > Les contrôles qui ne peuvent pas obtenir le focus, ainsi que les contrôles désactivés et invisibles, n’ont pas de propriété <xref:System.Windows.Forms.Control.TabIndex%2A> et ne sont pas inclus dans l’ordre de tabulation. Quand un utilisateur appuie sur la touche Tab, ces contrôles sont ignorés.

Vous pouvez également définir l’ordre de tabulation dans le Fenêtre Propriétés à l’aide de la propriété <xref:System.Windows.Forms.Control.TabIndex%2A>. La propriété <xref:System.Windows.Forms.Control.TabIndex%2A> d’un contrôle détermine l’emplacement où il est positionné dans l’ordre de tabulation. Par défaut, le premier contrôle dessiné a une valeur <xref:System.Windows.Forms.Control.TabIndex%2A> égale à 0, le deuxième a un <xref:System.Windows.Forms.Control.TabIndex%2A> de 1, et ainsi de suite.

En outre, par défaut, un contrôle <xref:System.Windows.Forms.GroupBox> possède sa propre valeur <xref:System.Windows.Forms.Control.TabIndex%2A>, qui est un nombre entier. Un contrôle <xref:System.Windows.Forms.GroupBox> lui-même ne peut pas avoir le focus au moment de l’exécution. Ainsi, chaque contrôle dans un <xref:System.Windows.Forms.GroupBox> possède sa propre valeur de <xref:System.Windows.Forms.Control.TabIndex%2A> décimale, à partir de. 0. Naturellement, comme le <xref:System.Windows.Forms.Control.TabIndex%2A> d’un contrôle <xref:System.Windows.Forms.GroupBox> est incrémenté, les contrôles qu’il contient sont incrémentés en conséquence. Si vous avez modifié une valeur de <xref:System.Windows.Forms.Control.TabIndex%2A> comprise entre 5 et 6, la valeur de <xref:System.Windows.Forms.Control.TabIndex%2A> du premier contrôle dans son groupe devient automatiquement 6,0, et ainsi de suite.

Enfin, n’importe quel contrôle de la plupart de votre formulaire peut être ignoré dans l’ordre de tabulation. En règle générale, le fait d’appuyer sur Tab successivement au moment de l’exécution sélectionne chaque contrôle dans l’ordre de tabulation. En désactivant la propriété <xref:System.Windows.Forms.Control.TabStop%2A>, vous pouvez faire en sorte qu’un contrôle soit passé dans l’ordre de tabulation du formulaire.

## <a name="to-remove-a-control-from-the-tab-order"></a>Pour supprimer un contrôle de l’ordre de tabulation

Affectez à la propriété <xref:System.Windows.Forms.Control.TabStop%2A> du contrôle la **valeur false** dans la fenêtre **Propriétés** .

Un contrôle dont la propriété <xref:System.Windows.Forms.Control.TabStop%2A> a été définie sur `false` conserve toujours sa position dans l’ordre de tabulation, même si le contrôle est ignoré lorsque vous parcourez les contrôles à l’aide de la touche Tab.

> [!NOTE]
> Un groupe de cases d’option a un seul taquet de tabulation au moment de l’exécution. Le bouton sélectionné (autrement dit, le bouton dont la propriété <xref:System.Windows.Forms.RadioButton.Checked%2A> a la valeur `true`) a sa propriété <xref:System.Windows.Forms.Control.TabStop%2A> définie automatiquement sur `true`, tandis que les autres boutons ont leur propriété <xref:System.Windows.Forms.Control.TabStop%2A> définie sur `false`. Pour plus d’informations sur le regroupement de contrôles <xref:System.Windows.Forms.RadioButton>, consultez [regroupement Windows Forms contrôles RadioButton pour qu’ils fonctionnent comme un ensemble](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Voir aussi

- [Contrôles Windows Forms](index.md)
- [Contrôles à utiliser dans les Windows Forms](controls-to-use-on-windows-forms.md)
- [Classement par fonction des contrôles Windows Forms](windows-forms-controls-by-function.md)
