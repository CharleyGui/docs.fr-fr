---
title: 'Comment : hériter de la classe du contrôle'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7af7d1fe8f14c71dfc90836d84023b98feb44961
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458386"
---
# <a name="how-to-inherit-from-the-control-class"></a>Comment : hériter de la classe du contrôle

Si vous souhaitez créer un contrôle entièrement personnalisé à utiliser sur un Windows Form, vous devez hériter de la classe <xref:System.Windows.Forms.Control>. Bien qu’hérite de la classe <xref:System.Windows.Forms.Control> nécessite que vous effectuiez davantage de planification et d’implémentation, elle vous fournit également la plus grande variété d’options. Lorsque vous héritez de <xref:System.Windows.Forms.Control>, vous héritez des fonctionnalités de base qui permettent aux contrôles de fonctionner. Les fonctionnalités inhérentes à la classe <xref:System.Windows.Forms.Control> gèrent les entrées d’utilisateur par le biais du clavier et de la souris, définissent les limites et la taille du contrôle, fournissent un handle Windows et assurent la gestion et la sécurité des messages. Elles n’intègrent pas la peinture, qui désigne ici le rendu réel de l’interface graphique du contrôle, ni les fonctionnalités d’interaction utilisateur spécifiques. Vous devez fournir tous ces aspects par le biais de code personnalisé.

## <a name="to-create-a-custom-control"></a>Pour créer un contrôle personnalisé

1. Dans Visual Studio, créez une **application Windows** ou un projet de **bibliothèque de contrôles Windows** .

2. Dans le menu **Projet** , choisissez **Ajouter une classe**.

3. Dans la boîte de dialogue **Ajouter un nouvel élément**, cliquez sur **Contrôle personnalisé**.

   Un contrôle personnalisé est ajouté à votre projet.

4. Appuyez sur **F7** pour ouvrir l' **éditeur de code** de votre contrôle personnalisé.

5. Recherchez la méthode <xref:System.Windows.Forms.Control.OnPaint%2A>, qui sera vide, à l’exception d’un appel à la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> de la classe de base.

6. Modifiez le code afin d’incorporer la peinture personnalisée pour votre contrôle.

   Pour plus d’informations sur l’écriture de code permettant d’afficher des graphiques concernant les contrôles, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).

7. Implémentez les méthodes, les propriétés ou les événements personnalisés que votre contrôle intégrera.

8. Enregistrez et testez votre contrôle.

## <a name="see-also"></a>Voir aussi

- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
- [Comment : hériter de la classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Guide pratique pour hériter de contrôles Windows Forms existants](how-to-inherit-from-existing-windows-forms-controls.md)
- [Guide pratique pour créer des contrôles pour des Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Dépannage des gestionnaires d’événements hérités en Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Développement de contrôles Windows Forms au moment du design](developing-windows-forms-controls-at-design-time.md)
