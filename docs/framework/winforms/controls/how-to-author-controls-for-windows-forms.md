---
title: 'Comment : créer des contrôles'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 169104f51898f9bda08efa08685207e50406a7ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746720"
---
# <a name="how-to-author-controls-for-windows-forms"></a>Comment : créer des contrôles pour Windows Forms

Un contrôle désigne un lien graphique entre l’utilisateur et le programme. Un contrôle peut fournir ou traiter des données, accepter des entrées d’utilisateur, répondre à des événements ou effectuer de nombreuses autres fonctions afin de connecter l’utilisateur et l’application. Un contrôle étant essentiellement un composant doté d’une interface graphique, il peut servir n’importe quelle fonction d’un composant, mais aussi fournir une interaction utilisateur. Les contrôles sont utilisés à des fins spécifiques, et la création de contrôles représente simplement une autre tâche de programmation. Dans cette optique, les étapes suivantes constituent une vue d’ensemble du processus de création de contrôle. Les liens renvoient vers des informations supplémentaires concernant les étapes individuelles.

## <a name="to-author-a-control"></a>Pour créer un contrôle

1. Déterminez ce que votre contrôle devra accomplir ou le rôle qu’il jouera dans votre application. Tenez compte des facteurs suivants :

    - De quel type d’interface graphique avez-vous besoin ?

    - Quelles interactions utilisateur spécifiques ce contrôle gérera-t-il ?

    - La fonctionnalité dont vous avez besoin est-elle fournie par des contrôles existants ?

    - Pouvez-vous obtenir la fonctionnalité dont vous avez besoin en combinant plusieurs contrôles Windows Forms ?

2. Si vous avez besoin d’un modèle d’objet pour votre contrôle, déterminez comment la fonctionnalité sera distribuée dans tout le modèle d’objet et répartissez-la entre le contrôle et les éventuels sous-objets. Un modèle d’objet peut être utile si vous prévoyez un contrôle complexe ou si vous souhaitez incorporer plusieurs fonctionnalités.

3. Déterminez le type de contrôle (par exemple, contrôle utilisateur, contrôle personnalisé, contrôle Windows Forms hérité) dont vous avez besoin. Pour plus d’informations, consultez [Recommandations relatives au type du contrôle](control-type-recommendations.md) et [Variétés de contrôles personnalisés](varieties-of-custom-controls.md).

4. Présentez les fonctionnalités en tant que propriétés, méthodes et événements du contrôle et de ses sous-objets ou structures secondaires, et assignez des niveaux d’accès appropriés (par exemple, public, protégé, etc.).

5. Si vous avez besoin d’une peinture personnalisée pour votre contrôle, ajoutez du code. Pour plus d’informations, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).

6. Si votre contrôle hérite de <xref:System.Windows.Forms.UserControl>, vous pouvez tester son comportement d’exécution en générant le projet de contrôle et en l’exécutant dans le **conteneur de test UserControl**. Pour plus d’informations, consultez l’article [Comment : tester le comportement d’un UserControl au moment de l’exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md).

7. Vous pouvez également tester et déboguer votre contrôle en créant un projet, comme une application Windows, et en le plaçant dans un conteneur. Ce processus est illustré dans le cadre de la [procédure pas à pas : création d’un contrôle composite](walkthrough-authoring-a-composite-control-with-visual-csharp.md).

8. À chaque ajout de fonctionnalité, ajoutez des fonctionnalités à votre projet de test pour tester cette nouvelle fonctionnalité.

9. Répétez l’opération en affinant le design.

10. Empaquetez et déployez votre contrôle. Pour plus d’informations, consultez [premier aperçu du déploiement dans Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="see-also"></a>Voir aussi

- [Comment : hériter de la classe UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Guide pratique pour hériter de la classe du contrôle](how-to-inherit-from-the-control-class.md)
- [Guide pratique pour hériter de contrôles Windows Forms existants](how-to-inherit-from-existing-windows-forms-controls.md)
- [Guide pratique pour tester le comportement d'un UserControl au moment de l'exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Variétés de contrôles personnalisés](varieties-of-custom-controls.md)
