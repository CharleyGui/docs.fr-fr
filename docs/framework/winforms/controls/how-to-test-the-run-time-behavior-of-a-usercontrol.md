---
title: 'Procédure : tester le comportement au moment de l’exécution d’un UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015775"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>Procédure : Tester le comportement d’un UserControl au moment de l’exécution

Lorsque vous développez <xref:System.Windows.Forms.UserControl>un, vous devez tester son comportement au moment de l’exécution. Vous pouvez créer un projet d’application Windows distinct et placer votre contrôle sur un formulaire de test, mais cette procédure est peu commode. Un moyen plus rapide et plus simple consiste à utiliser le **conteneur de test UserControl** fourni par Visual Studio. Ce conteneur de test démarre directement à partir de votre projet de bibliothèque de contrôles Windows.

> [!IMPORTANT]
> Pour que le conteneur de test charge <xref:System.Windows.Forms.UserControl>votre, le contrôle doit avoir au moins un constructeur public.

> [!NOTE]
> Un contrôle C++ visuel ne peut pas être testé à l’aide du **conteneur de test UserControl**.

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>Tester le comportement d’un UserControl au moment de l’exécution

1. Dans Visual Studio, créez un projet de bibliothèque de contrôles Windows, puis nommez-le **TestContainerExample**.

2. Dans le **Concepteur Windows Forms**, faites glisser <xref:System.Windows.Forms.Label> un contrôle de la **boîte à outils** vers l’aire de conception du contrôle.

3. Appuyez sur **F5** pour générer le projet et exécuter le **conteneur de test UserControl**. Le conteneur de test s’affiche <xref:System.Windows.Forms.UserControl> avec votre dans le volet de **visualisation** .

4. Sélectionnez la <xref:System.Windows.Forms.Control.BackColor%2A> propriété affichée dans le <xref:System.Windows.Forms.PropertyGrid> contrôle à droite du volet de **visualisation** . Remplacez sa valeur par **ControlDark**. Notez que le contrôle passe à une couleur plus sombre. Essayez de modifier d’autres valeurs de propriété et observez l’effet sur votre contrôle.

5. Activez la case à cocher **ancrer remplir le contrôle utilisateur** sous le volet de **visualisation** . Notez que le contrôle est redimensionné pour remplir le volet. Redimensionnez le conteneur de test et observez que le contrôle est redimensionné avec le volet.

6. Fermez le conteneur de test.

7. Ajoutez un autre contrôle utilisateur au projet **TestContainerExample** .

8. Dans le **Concepteur Windows Forms**, faites glisser <xref:System.Windows.Forms.Button> un contrôle de la **boîte à outils** vers l’aire de conception du contrôle.

9. Appuyez sur **F5** pour générer le projet et exécuter le conteneur de test.

10. Cliquez sur le **contrôle** <xref:System.Windows.Forms.ComboBox> sélectionner un utilisateur pour basculer entre les deux contrôles utilisateur.

## <a name="test-user-controls-from-another-project"></a>Tester des contrôles utilisateur à partir d’un autre projet

Vous pouvez tester des contrôles utilisateur à partir d’autres projets dans le conteneur de test de votre projet actuel.

1. Dans Visual Studio, créez un projet de bibliothèque de contrôles Windows, puis nommez-le **TestContainerExample2**.

2. Dans le **Concepteur Windows Forms**, faites glisser <xref:System.Windows.Forms.RadioButton> un contrôle de la **boîte à outils** vers l’aire de conception du contrôle.

3. Appuyez sur **F5** pour générer le projet et exécuter le conteneur de test. Le conteneur de test s’affiche <xref:System.Windows.Forms.UserControl> avec votre dans le volet de **visualisation** .

4. Cliquez sur le bouton **charger** .

5. Dans la boîte de dialogue **ouvrir** , accédez à **TestContainerExample**. dll, que vous avez créé dans la procédure précédente. Sélectionnez **TestContainerExample**. dll, puis cliquez sur le bouton **ouvrir** pour charger les contrôles utilisateur.

6. Utilisez le **contrôle** <xref:System.Windows.Forms.ComboBox> sélectionner un utilisateur pour basculer entre les deux contrôles utilisateur du projet **TestContainerExample** .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.UserControl>
- [Guide pratique pour Créer des contrôles composites](how-to-author-composite-controls.md)
- [Procédure pas à pas : Création d’un contrôle composite](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [Concepteur de contrôles utilisateur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
