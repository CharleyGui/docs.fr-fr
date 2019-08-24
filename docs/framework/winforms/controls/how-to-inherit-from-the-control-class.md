---
title: 'Procédure : hériter de la classe Control'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02c40e310778bd476742f62ee8b9d8598b084a53
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015851"
---
# <a name="how-to-inherit-from-the-control-class"></a>Procédure : hériter de la classe Control

Si vous souhaitez créer un contrôle entièrement personnalisé à utiliser sur un Windows Form, vous devez hériter de la <xref:System.Windows.Forms.Control> classe. L’héritage de la <xref:System.Windows.Forms.Control> classe nécessite que vous effectuiez davantage de planification et d’implémentation, mais vous offre également la plus grande variété d’options. Lorsque vous héritez <xref:System.Windows.Forms.Control>de, vous héritez des fonctionnalités de base qui permettent aux contrôles de fonctionner. Les fonctionnalités inhérentes à <xref:System.Windows.Forms.Control> la classe gèrent les entrées d’utilisateur par le biais du clavier et de la souris, définissent les limites et la taille du contrôle, fournissent un handle Windows et assurent la gestion et la sécurité des messages. Elles n’intègrent pas la peinture, qui désigne ici le rendu réel de l’interface graphique du contrôle, ni les fonctionnalités d’interaction utilisateur spécifiques. Vous devez fournir tous ces aspects par le biais de code personnalisé.

## <a name="to-create-a-custom-control"></a>Pour créer un contrôle personnalisé

1. Dans Visual Studio, créez une **application Windows** ou un projet de **bibliothèque de contrôles Windows** .

2. Dans le menu **Projet** , choisissez **Ajouter une classe**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Contrôle personnalisé**.

   Un contrôle personnalisé est ajouté à votre projet.

4. Appuyez sur **F7** pour ouvrir l' **éditeur de code** de votre contrôle personnalisé.

5. Recherchez la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode, qui sera vide à l’exception d’un appel à <xref:System.Windows.Forms.Control.OnPaint%2A> la méthode de la classe de base.

6. Modifiez le code afin d’incorporer la peinture personnalisée pour votre contrôle.

   Pour plus d’informations sur l’écriture de code permettant d’afficher des graphiques concernant les contrôles, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).

7. Implémentez les méthodes, les propriétés ou les événements personnalisés que votre contrôle intégrera.

8. Enregistrez et testez votre contrôle.

## <a name="see-also"></a>Voir aussi

- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
- [Guide pratique pour Hériter de la classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Guide pratique pour Hériter de contrôles Windows Forms existants](how-to-inherit-from-existing-windows-forms-controls.md)
- [Guide pratique : Créer des contrôles pour Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Dépannage des gestionnaires d’événements hérités en Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Développement de contrôles Windows Forms au moment du design](developing-windows-forms-controls-at-design-time.md)
