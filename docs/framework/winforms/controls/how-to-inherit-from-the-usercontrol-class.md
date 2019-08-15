---
title: 'Procédure : hériter de la classe UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 69452f24e5c485ce0aba454648b59c50fb0ce1e3
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037764"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Procédure : hériter de la classe UserControl
Pour combiner les fonctionnalités d’un ou de plusieurs contrôles Windows Forms avec du code personnalisé, vous pouvez créer un *contrôle utilisateur*. Les contrôles utilisateur allient le développement rapide de contrôles, les fonctionnalités des contrôles Windows Forms standard et la polyvalence des propriétés et méthodes personnalisées. Lorsque vous créez un contrôle utilisateur, un concepteur visible, sur lequel vous pouvez placer des contrôles Windows Forms standard, s’affiche. Ces contrôles conservent toutes leurs fonctionnalités inhérentes, ainsi que l’apparence et le comportement de contrôles standard. Une fois que ces contrôles sont générés dans le contrôle utilisateur, ils ne sont toutefois plus disponibles par le biais du code. Le contrôle utilisateur effectue sa propre peinture et gère également toutes les fonctionnalités de base associées aux contrôles.

## <a name="to-create-a-user-control"></a>Pour créer un contrôle utilisateur

1. Créez un projet de **bibliothèque de contrôles Windows**.

     Un projet est créé avec un contrôle utilisateur vide.

2. Faites glisser des contrôles de l’onglet **Windows Forms** de la **boîte à outils** vers votre concepteur.

3. Positionnez et concevez ces contrôles comme vous souhaitez qu’ils apparaissent dans le contrôle utilisateur final. Si vous souhaitez permettre aux développeurs d’accéder aux contrôles constitutifs, vous devez les déclarer publics ou exposer de manière sélective les propriétés du contrôle constitutif. Pour plus d’informations, consultez [Guide pratique pour Exposer les propriétés des contrôles](how-to-expose-properties-of-constituent-controls.md)constitutifs.

4. Implémentez les méthodes ou propriétés personnalisées que votre contrôle intégrera.

5. Appuyez sur F5 pour générer le projet et exécuter votre contrôle dans le **Conteneur de test UserControl**. Pour plus d’informations, consultez [Guide pratique pour Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.

## <a name="see-also"></a>Voir aussi

- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
- [Guide pratique pour Hériter de la classe de contrôle](how-to-inherit-from-the-control-class.md)
- [Guide pratique pour Hériter de contrôles Windows Forms existants](how-to-inherit-from-existing-windows-forms-controls.md)
- [Guide pratique : Créer des contrôles pour Windows Forms](how-to-author-controls-for-windows-forms.md)
- [Dépannage des gestionnaires d’événements hérités en Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Guide pratique : Tester le comportement d’un UserControl au moment de l’exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
