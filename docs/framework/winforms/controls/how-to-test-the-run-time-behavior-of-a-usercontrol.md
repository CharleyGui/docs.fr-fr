---
title: "Comment : tester le comportement d'un UserControl au moment de l'exécution"
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: be6c913c43e3559806bc9f38a9c3152b544e4c07
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455536"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Comment : tester le comportement d’un UserControl au moment de l’exécution

Lorsque vous développez un <xref:System.Windows.Forms.UserControl>, vous devez tester son comportement au moment de l’exécution. Vous pouvez créer un projet d’application Windows distinct et placer votre contrôle sur un formulaire de test, mais cette procédure est peu commode. Un moyen plus rapide et plus simple consiste à utiliser le **conteneur de test UserControl** fourni par Visual Studio. Ce conteneur de test démarre directement à partir de votre projet de bibliothèque de contrôles Windows.

> [!IMPORTANT]
> Pour que le conteneur de test charge votre <xref:System.Windows.Forms.UserControl>, le contrôle doit avoir au moins un constructeur public.

> [!NOTE]
> Un contrôle C++ visuel ne peut pas être testé à l’aide du **conteneur de test UserControl**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Tester le comportement d’un UserControl au moment de l’exécution

1. Dans Visual Studio, créez un projet de bibliothèque de contrôles Windows, puis nommez-le **TestContainerExample**.

2. Dans le **Concepteur Windows Forms**, faites glisser un contrôle <xref:System.Windows.Forms.Label> de la **boîte à outils** vers l’aire de conception du contrôle.

3. Appuyez sur <kbd>F5</kbd> pour générer le projet et exécuter le **conteneur de test UserControl**. Le conteneur de test s’affiche avec votre <xref:System.Windows.Forms.UserControl> dans le volet de **visualisation** .

4. Sélectionnez la propriété <xref:System.Windows.Forms.Control.BackColor%2A> affichée dans le contrôle <xref:System.Windows.Forms.PropertyGrid> à droite du volet de **visualisation** . Remplacez sa valeur par **ControlDark**. Notez que le contrôle passe à une couleur plus sombre. Essayez de modifier d’autres valeurs de propriété et observez l’effet sur votre contrôle.

5. Activez la case à cocher **ancrer remplir le contrôle utilisateur** sous le volet de **visualisation** . Notez que le contrôle est redimensionné pour remplir le volet. Redimensionnez le conteneur de test et observez que le contrôle est redimensionné avec le volet.

6. Fermez le conteneur de test.

7. Ajoutez un autre contrôle utilisateur au projet **TestContainerExample** .

8. Dans le **Concepteur Windows Forms**, faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers l’aire de conception du contrôle.

9. Appuyez sur <kbd>F5</kbd> pour générer le projet et exécuter le conteneur de test.

10. Cliquez sur l' <xref:System.Windows.Forms.ComboBox> **Sélectionner un contrôle utilisateur** pour basculer entre les deux contrôles utilisateur.

## <a name="test-user-controls-from-another-project"></a>Tester des contrôles utilisateur à partir d’un autre projet

Vous pouvez tester des contrôles utilisateur à partir d’autres projets dans le conteneur de test de votre projet actuel.

1. Dans Visual Studio, créez un projet de bibliothèque de contrôles Windows, puis nommez-le **TestContainerExample2**.

2. Dans le **Concepteur Windows Forms**, faites glisser un contrôle <xref:System.Windows.Forms.RadioButton> de la **boîte à outils** vers l’aire de conception du contrôle.

3. Appuyez sur <kbd>F5</kbd> pour générer le projet et exécuter le conteneur de test. Le conteneur de test s’affiche avec votre <xref:System.Windows.Forms.UserControl> dans le volet de **visualisation** .

4. Cliquez sur le bouton **charger** .

5. Dans la boîte de dialogue **ouvrir** , accédez à *TestContainerExample. dll*, que vous avez créé dans la procédure précédente. Sélectionnez *TestContainerExample. dll* , puis cliquez sur le bouton **ouvrir** pour charger les contrôles utilisateur.

6. Utilisez la <xref:System.Windows.Forms.ComboBox> **Sélectionner un contrôle utilisateur** pour basculer entre les deux contrôles utilisateur du projet **TestContainerExample** .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.UserControl>
- [Guide pratique pour créer des contrôles composites](how-to-author-composite-controls.md)
- [Procédure pas à pas : création d’un contrôle composite](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Concepteur de contrôles utilisateur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
