---
title: Créer un contrôle qui tire parti des fonctionnalités au moment du design de Visual Studio
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms controls, creating
- design-time functionality [Windows Forms], Windows Forms
- DocumentDesigner class [Windows Forms]
- walkthroughs [Windows Forms], controls
ms.assetid: 6f487c59-cb38-4afa-ad2e-95edacb1d626
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7166b4203c54ab31f1d929c85cf1e6481ff120f8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744080"
---
# <a name="walkthrough-create-a-control-that-takes-advantage-of-design-time-features"></a>Procédure pas à pas : création d’un contrôle qui tire parti des fonctionnalités au moment du design

L’expérience au moment du design pour un contrôle personnalisé peut être améliorée en créant un concepteur personnalisé associé.

Cet article explique comment créer un concepteur personnalisé pour un contrôle personnalisé. Vous allez implémenter un type de `MarqueeControl` et une classe de concepteur associée appelée `MarqueeControlRootDesigner`.

Le type de `MarqueeControl` implémente un affichage similaire à un cadre de sélection de théâtre avec des lumières animées et du texte clignotant.

Le concepteur de ce contrôle interagit avec l’environnement de conception pour fournir une expérience personnalisée au moment du Design. Avec le concepteur personnalisé, vous pouvez assembler une implémentation de `MarqueeControl` personnalisée avec des lumières animées et du texte clignotant dans de nombreuses combinaisons. Vous pouvez utiliser le contrôle assemblé sur un formulaire comme tout autre contrôle de Windows Forms.

Une fois que vous avez terminé cette procédure pas à pas, votre contrôle personnalisé ressemble à ce qui suit :

![Application présentant un texte défilant indiquant le texte et les boutons de démarrage et d’arrêt.](./media/creating-a-wf-control-design-time-features/demo-marquee-control.gif)

Pour obtenir la liste complète du code, consultez [Comment : créer un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120)).

## <a name="prerequisites"></a>Composants requis

Pour effectuer cette procédure pas à pas, vous avez besoin de Visual Studio.

## <a name="create-the-project"></a>Créer le projet

La première étape consiste à créer le projet d’application. Vous allez utiliser ce projet pour générer l’application qui héberge le contrôle personnalisé.

Dans Visual Studio, créez un projet d’application de Windows Forms, puis nommez-le **MarqueeControlTest**.

## <a name="create-the-control-library-project"></a>Créer le projet de bibliothèque de contrôles

1. Ajoutez un projet de bibliothèque de contrôles Windows Forms à la solution. Nommez le projet **MarqueeControlLibrary**.

2. À l’aide de **Explorateur de solutions**, supprimez le contrôle par défaut du projet en supprimant le fichier source nommé « UserControl1.cs » ou « UserControl1. vb », selon le langage de votre choix.

3. Ajoutez un nouvel élément <xref:System.Windows.Forms.UserControl> au projet `MarqueeControlLibrary`. Donnez au nouveau fichier source un nom de base de **MarqueeControl**.

4. À l’aide de **Explorateur de solutions**, créez un nouveau dossier dans le projet `MarqueeControlLibrary`.

5. Cliquez avec le bouton droit sur le dossier **Design** et ajoutez une nouvelle classe. Nommez-le **MarqueeControlRootDesigner**.

6. Vous devez utiliser des types de l’assembly System. Design. Ajoutez cette référence au projet `MarqueeControlLibrary`.

## <a name="reference-the-custom-control-project"></a>Référencer le projet de contrôle personnalisé

Vous allez utiliser le projet `MarqueeControlTest` pour tester le contrôle personnalisé. Le projet de test prend connaissance du contrôle personnalisé lorsque vous ajoutez une référence de projet à l’assembly `MarqueeControlLibrary`.

Dans le projet `MarqueeControlTest`, ajoutez une référence de projet à l’assembly `MarqueeControlLibrary`. Veillez à utiliser l’onglet **projets** de la boîte de dialogue **Ajouter une référence** au lieu de référencer directement l’assembly de `MarqueeControlLibrary`.

## <a name="define-a-custom-control-and-its-custom-designer"></a>Définir un contrôle personnalisé et son concepteur personnalisé

Votre contrôle personnalisé dérive de la classe <xref:System.Windows.Forms.UserControl>. Cela permet à votre contrôle de contenir d’autres contrôles et donne à votre contrôle une grande quantité de fonctionnalités par défaut.

Votre contrôle personnalisé aura un concepteur personnalisé associé. Cela vous permet de créer une expérience de conception unique adaptée à votre contrôle personnalisé.

Vous associez le contrôle à son concepteur à l’aide de la classe <xref:System.ComponentModel.DesignerAttribute>. Étant donné que vous développez l’ensemble du comportement au moment du design de votre contrôle personnalisé, le concepteur personnalisé implémente l’interface <xref:System.ComponentModel.Design.IRootDesigner>.

### <a name="to-define-a-custom-control-and-its-custom-designer"></a>Pour définir un contrôle personnalisé et son concepteur personnalisé

1. Ouvrez le `MarqueeControl` fichier source dans l' **éditeur de code**. En haut du fichier, importez les espaces de noms suivants :

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#220)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#220](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#220)]

2. Ajoutez le <xref:System.ComponentModel.DesignerAttribute> à la déclaration de classe `MarqueeControl`. Cela associe le contrôle personnalisé à son concepteur.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#240)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#240](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#240)]

3. Ouvrez le `MarqueeControlRootDesigner` fichier source dans l' **éditeur de code**. En haut du fichier, importez les espaces de noms suivants :

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#520)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#520](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#520)]

4. Modifiez la déclaration de `MarqueeControlRootDesigner` pour qu’elle hérite de la classe <xref:System.Windows.Forms.Design.DocumentDesigner>. Appliquez la <xref:System.ComponentModel.ToolboxItemFilterAttribute> pour spécifier l’interaction du concepteur avec la **boîte à outils**.

   > [!NOTE]
   > La définition de la classe `MarqueeControlRootDesigner` a été placée dans un espace de noms appelé MarqueeControlLibrary. Design. Cette déclaration place le concepteur dans un espace de noms spécial réservé aux types liés à la conception.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#530)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#530](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#530)]

5. Définissez le constructeur pour la classe `MarqueeControlRootDesigner`. Insérez une instruction <xref:System.Diagnostics.Trace.WriteLine%2A> dans le corps du constructeur. Cela sera utile pour le débogage.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#540)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#540](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#540)]

## <a name="create-an-instance-of-your-custom-control"></a>Créer une instance de votre contrôle personnalisé

1. Ajoutez un nouvel élément <xref:System.Windows.Forms.UserControl> au projet `MarqueeControlTest`. Donnez au nouveau fichier source un nom de base de **DemoMarqueeControl**.

2. Ouvrez le fichier `DemoMarqueeControl` dans l' **éditeur de code**. En haut du fichier, importez l’espace de noms `MarqueeControlLibrary` :

   ```vb
   Imports MarqueeControlLibrary
   ```

   ```csharp
   using MarqueeControlLibrary;
   ```

3. Modifiez la déclaration de `DemoMarqueeControl` pour qu’elle hérite de la classe `MarqueeControl`.

4. créer le projet ;

5. Ouvrez Form1 dans le Concepteur Windows Forms.

6. Recherchez l’onglet **Composants MarqueeControlTest** dans la **boîte à outils** et ouvrez-le. Faites glisser un `DemoMarqueeControl` de la **boîte à outils** vers votre formulaire.

7. créer le projet ;

## <a name="set-up-the-project-for-design-time-debugging"></a>Configurer le projet pour le débogage au moment du design

Lorsque vous développez une expérience personnalisée au moment de la conception, il est nécessaire de déboguer vos contrôles et composants. Il existe un moyen simple de configurer votre projet pour autoriser le débogage au moment de la conception. Pour plus d’informations, consultez [procédure pas à pas : débogage de contrôles Windows Forms personnalisés au moment du design](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).

1. Cliquez avec le bouton droit sur le projet `MarqueeControlLibrary`, puis sélectionnez **Propriétés**.

2. Dans la boîte de dialogue **pages de propriétés de MarqueeControlLibrary** , sélectionnez la page **Déboguer** .

3. Dans la section **action de démarrage** , sélectionnez Démarrer le **programme externe**. Vous allez déboguer une instance distincte de Visual Studio. par conséquent, cliquez sur les points de suspension (![le bouton de sélection (...) du bouton Fenêtre Propriétés de Visual Studio](./media/visual-studio-ellipsis-button.png)) pour Rechercher l’IDE de Visual Studio. Le nom du fichier exécutable est devenv. exe, et si vous avez installé à l’emplacement par défaut, son chemin d’accès est *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<edition > \Common7\IDE\devenv.exe*.

4. Sélectionnez **OK** pour fermer la boîte de dialogue.

5. Cliquez avec le bouton droit sur le projet MarqueeControlLibrary et sélectionnez **définir comme projet de démarrage** pour activer cette configuration de débogage.

## <a name="checkpoint"></a>Point de contrôle

Vous êtes maintenant prêt à déboguer le comportement au moment du design de votre contrôle personnalisé. Une fois que vous avez déterminé que l’environnement de débogage est correctement configuré, vous allez tester l’association entre le contrôle personnalisé et le concepteur personnalisé.

### <a name="to-test-the-debugging-environment-and-the-designer-association"></a>Pour tester l’environnement de débogage et l’Association du concepteur

1. Ouvrez le fichier source MarqueeControlRootDesigner dans l' **éditeur de code** et placez un point d’arrêt sur l’instruction <xref:System.Diagnostics.Trace.WriteLine%2A>.

2. Appuyez sur **F5** pour démarrer la session de débogage.

   Une nouvelle instance de Visual Studio est créée.

3. Dans la nouvelle instance de Visual Studio, ouvrez la solution MarqueeControlTest. Vous pouvez facilement trouver la solution en sélectionnant **projets récents** dans le menu **fichier** . Le fichier de solution MarqueeControlTest. sln sera listé comme le fichier le plus récemment utilisé.

4. Ouvrez le `DemoMarqueeControl` dans le concepteur.

   L’instance de débogage de Visual Studio obtient le focus et l’exécution s’arrête à votre point d’arrêt. Appuyez sur **F5** pour continuer la session de débogage.

À ce stade, tout est en place pour vous permettant de développer et de déboguer votre contrôle personnalisé et son concepteur personnalisé associé. Le reste de cet article se concentre sur les détails de l’implémentation des fonctionnalités du contrôle et du concepteur.

## <a name="implement-the-custom-control"></a>Implémenter le contrôle personnalisé

Le `MarqueeControl` est un <xref:System.Windows.Forms.UserControl> avec un peu de personnalisation. Il expose deux méthodes : `Start`, qui démarre l’animation de texte défilant et `Stop`, qui arrête l’animation. Étant donné que le `MarqueeControl` contient des contrôles enfants qui implémentent l’interface `IMarqueeWidget`, `Start` et `Stop` énumérer chaque contrôle enfant et appeler les méthodes `StartMarquee` et `StopMarquee`, respectivement, sur chaque contrôle enfant qui implémente `IMarqueeWidget`.

L’apparence des contrôles `MarqueeBorder` et `MarqueeText` dépend de la disposition, donc `MarqueeControl` substitue la méthode <xref:System.Windows.Forms.Control.OnLayout%2A> et appelle <xref:System.Windows.Forms.Control.PerformLayout%2A> sur les contrôles enfants de ce type.

Il s’agit de l’étendue des personnalisations de `MarqueeControl`. Les fonctionnalités d’exécution sont implémentées par les contrôles `MarqueeBorder` et `MarqueeText`, et les fonctionnalités au moment du design sont implémentées par les classes `MarqueeBorderDesigner` et `MarqueeControlRootDesigner`.

### <a name="to-implement-your-custom-control"></a>Pour implémenter votre contrôle personnalisé

1. Ouvrez le `MarqueeControl` fichier source dans l' **éditeur de code**. Implémentez les méthodes `Start` et `Stop`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#260)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#260](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#260)]

2. Remplacez la méthode <xref:System.Windows.Forms.Control.OnLayout%2A> .

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrol.cs#270)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#270](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrol.vb#270)]

## <a name="create-a-child-control-for-your-custom-control"></a>Créer un contrôle enfant pour votre contrôle personnalisé

Le `MarqueeControl` hébergera deux genres de contrôles enfants : le contrôle `MarqueeBorder` et le contrôle `MarqueeText`.

- `MarqueeBorder`: ce contrôle peint une bordure de « lumières » autour de ses bords. Les voyants clignotent en séquence. ils semblent donc se déplacer autour de la bordure. La vitesse à laquelle le flash lumineux clignote est contrôlée par une propriété appelée `UpdatePeriod`. Plusieurs autres propriétés personnalisées déterminent d’autres aspects de l’apparence du contrôle. Deux méthodes, appelées `StartMarquee` et `StopMarquee`, contrôlent le moment où l’animation démarre et s’arrête.

- `MarqueeText`: ce contrôle peint une chaîne clignotante. À l’instar du contrôle `MarqueeBorder`, la vitesse à laquelle le texte clignote est contrôlée par la propriété `UpdatePeriod`. Le contrôle `MarqueeText` possède également les méthodes `StartMarquee` et `StopMarquee` en commun avec le contrôle `MarqueeBorder`.

Au moment du design, le `MarqueeControlRootDesigner` permet d’ajouter ces deux types de contrôle à une `MarqueeControl` dans n’importe quelle combinaison.

Les fonctionnalités communes des deux contrôles sont factorisées dans une interface appelée `IMarqueeWidget`. Cela permet à l' `MarqueeControl` de découvrir les contrôles enfants liés à un texte défilant et de leur accorder un traitement spécial.

Pour implémenter la fonctionnalité d’animation périodique, vous allez utiliser <xref:System.ComponentModel.BackgroundWorker> objets de l’espace de noms <xref:System.ComponentModel?displayProperty=nameWithType>. Vous pouvez utiliser des objets <xref:System.Windows.Forms.Timer>, mais lorsque de nombreux objets `IMarqueeWidget` sont présents, le thread d’interface utilisateur unique peut ne pas être en mesure de suivre l’animation.

### <a name="to-create-a-child-control-for-your-custom-control"></a>Pour créer un contrôle enfant pour votre contrôle personnalisé

1. Ajoutez un nouvel élément de classe au projet `MarqueeControlLibrary`. Donnez au nouveau fichier source le nom de base « IMarqueeWidget ».

2. Ouvrez le `IMarqueeWidget` fichier source dans l' **éditeur de code** et modifiez la déclaration de `class` en `interface`:

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#2)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#2)]

3. Ajoutez le code suivant à l’interface `IMarqueeWidget` pour exposer deux méthodes et une propriété qui manipulent l’animation de texte défilant :

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/imarqueewidget.cs#3)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/imarqueewidget.vb#3)]

4. Ajoutez un nouvel élément de **contrôle personnalisé** au projet `MarqueeControlLibrary`. Donnez au nouveau fichier source le nom de base « MarqueeText ».

5. Faites glisser un composant <xref:System.ComponentModel.BackgroundWorker> de la **boîte à outils** vers votre contrôle `MarqueeText`. Ce composant permettra au contrôle `MarqueeText` de se mettre à jour de façon asynchrone.

6. Dans la fenêtre **Propriétés** , définissez les propriétés `WorkerReportsProgress` et <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> du composant <xref:System.ComponentModel.BackgroundWorker> sur **true**. Ces paramètres permettent au composant <xref:System.ComponentModel.BackgroundWorker> de déclencher régulièrement l’événement <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> et d’annuler les mises à jour asynchrones.

   Pour plus d’informations, consultez [composant BackgroundWorker](backgroundworker-component.md).

7. Ouvrez le `MarqueeText` fichier source dans l' **éditeur de code**. En haut du fichier, importez les espaces de noms suivants :

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#120)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#120)]

8. Modifiez la déclaration de `MarqueeText` pour qu’elle hérite de <xref:System.Windows.Forms.Label> et pour implémenter l’interface `IMarqueeWidget` :

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#130)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#130)]

9. Déclarez les variables d’instance qui correspondent aux propriétés exposées et initialisez-les dans le constructeur. Le champ `isLit` détermine si le texte doit être peint dans la couleur donnée par la propriété `LightColor`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#140)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#140)]

10. Implémentez l'interface `IMarqueeWidget`.

    Les méthodes `StartMarquee` et `StopMarquee` appellent les méthodes <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> et <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> du composant <xref:System.ComponentModel.BackgroundWorker> pour démarrer et arrêter l’animation.

    Les attributs <xref:System.ComponentModel.CategoryAttribute.Category%2A> et <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> sont appliqués à la propriété `UpdatePeriod`, de sorte qu’elle apparaît dans une section personnalisée de l’Fenêtre Propriétés appelée « texte défilant ».

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#150)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#150)]

11. Implémentez les accesseurs de propriété. Vous exposerez deux propriétés aux clients : `LightColor` et `DarkColor`. Les attributs <xref:System.ComponentModel.CategoryAttribute.Category%2A> et <xref:System.ComponentModel.BrowsableAttribute.Browsable%2A> sont appliqués à ces propriétés, de sorte que les propriétés s’affichent dans une section personnalisée du Fenêtre Propriétés appelée « texte défilant ».

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#160)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#160)]

12. Implémentez les gestionnaires pour les événements <xref:System.ComponentModel.BackgroundWorker.DoWork> et <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> du composant <xref:System.ComponentModel.BackgroundWorker>.

    Le gestionnaire d’événements <xref:System.ComponentModel.BackgroundWorker.DoWork> se met en veille pendant le nombre de millisecondes spécifié par `UpdatePeriod` puis déclenche l’événement <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, jusqu’à ce que votre code arrête l’animation en appelant <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.

    Le gestionnaire d’événements <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> fait basculer le texte entre son état clair et sombre pour obtenir l’apparence d’un clignotement.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#180)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#180)]

13. Substituez la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> pour activer l’animation.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueetext.cs#170)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueetext.vb#170)]

14. Appuyez sur **F6** pour générer la solution.

## <a name="create-the-marqueeborder-child-control"></a>Créer le contrôle enfant MarqueeBorder

Le contrôle `MarqueeBorder` est légèrement plus sophistiqué que le contrôle `MarqueeText`. Il a plus de propriétés et l’animation dans la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> est plus complexe. En principe, il est assez similaire au contrôle `MarqueeText`.

Étant donné que le contrôle `MarqueeBorder` peut avoir des contrôles enfants, il doit être conscient des événements <xref:System.Windows.Forms.Control.Layout>.

### <a name="to-create-the-marqueeborder-control"></a>Pour créer le contrôle MarqueeBorder

1. Ajoutez un nouvel élément de **contrôle personnalisé** au projet `MarqueeControlLibrary`. Donnez au nouveau fichier source le nom de base « MarqueeBorder ».

2. Faites glisser un composant <xref:System.ComponentModel.BackgroundWorker> de la **boîte à outils** vers votre contrôle `MarqueeBorder`. Ce composant permettra au contrôle `MarqueeBorder` de se mettre à jour de façon asynchrone.

3. Dans la fenêtre **Propriétés** , définissez les propriétés `WorkerReportsProgress` et <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> du composant <xref:System.ComponentModel.BackgroundWorker> sur **true**. Ces paramètres permettent au composant <xref:System.ComponentModel.BackgroundWorker> de déclencher régulièrement l’événement <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> et d’annuler les mises à jour asynchrones. Pour plus d’informations, consultez [composant BackgroundWorker](backgroundworker-component.md).

4. Dans la fenêtre **Propriétés** , sélectionnez le bouton **événements** . Attacher des gestionnaires pour les événements <xref:System.ComponentModel.BackgroundWorker.DoWork> et <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>.

5. Ouvrez le `MarqueeBorder` fichier source dans l' **éditeur de code**. En haut du fichier, importez les espaces de noms suivants :

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#20)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#20)]

6. Modifiez la déclaration de `MarqueeBorder` pour qu’elle hérite de <xref:System.Windows.Forms.Panel> et pour implémenter l’interface `IMarqueeWidget`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#30)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#30)]

7. Déclarez deux énumérations pour gérer l’état du contrôle `MarqueeBorder` : `MarqueeSpinDirection`, qui détermine la direction dans laquelle les lumières « tournent » autour de la bordure, et `MarqueeLightShape`, qui détermine la forme des lumières (carré ou circulaire). Placez ces déclarations avant la déclaration de classe `MarqueeBorder`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#97)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#97](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#97)]

8. Déclarez les variables d’instance qui correspondent aux propriétés exposées et initialisez-les dans le constructeur.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#40)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#40)]

9. Implémentez l'interface `IMarqueeWidget`.

    Les méthodes `StartMarquee` et `StopMarquee` appellent les méthodes <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> et <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> du composant <xref:System.ComponentModel.BackgroundWorker> pour démarrer et arrêter l’animation.

    Étant donné que le contrôle `MarqueeBorder` peut contenir des contrôles enfants, la méthode `StartMarquee` énumère tous les contrôles enfants et les appels `StartMarquee` sur ceux qui implémentent `IMarqueeWidget`. La méthode `StopMarquee` a une implémentation similaire.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#50)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#50)]

10. Implémentez les accesseurs de propriété. Le contrôle `MarqueeBorder` possède plusieurs propriétés pour contrôler son apparence.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#60)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#60)]

11. Implémentez les gestionnaires pour les événements <xref:System.ComponentModel.BackgroundWorker.DoWork> et <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> du composant <xref:System.ComponentModel.BackgroundWorker>.

    Le gestionnaire d’événements <xref:System.ComponentModel.BackgroundWorker.DoWork> se met en veille pendant le nombre de millisecondes spécifié par `UpdatePeriod` puis déclenche l’événement <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>, jusqu’à ce que votre code arrête l’animation en appelant <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>.

    Le gestionnaire d’événements <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> incrémente la position de la lumière « base », à partir de laquelle l’État clair/sombre des autres lumières est déterminé, et appelle la méthode <xref:System.Windows.Forms.Control.Refresh%2A> pour faire en sorte que le contrôle se redessine lui-même.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#90)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#90](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#90)]

12. Implémentez les méthodes d’assistance, les `IsLit` et les `DrawLight`.

    La méthode `IsLit` détermine la couleur d’une lumière à une position donnée. Les lumières qui sont « allumées » sont dessinées dans la couleur donnée par la propriété `LightColor`, tandis que celles qui sont « sombres » sont dessinées dans la couleur donnée par la propriété `DarkColor`.

    La méthode `DrawLight` dessine une lumière à l’aide de la couleur, de la forme et de la position appropriées.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#80)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#80](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#80)]

13. Substituez les méthodes <xref:System.Windows.Forms.Control.OnLayout%2A> et <xref:System.Windows.Forms.Control.OnPaint%2A>.

    La méthode <xref:System.Windows.Forms.Control.OnPaint%2A> dessine les lumières le long des bords du contrôle `MarqueeBorder`.

    Étant donné que la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> dépend des dimensions du contrôle `MarqueeBorder`, vous devez l’appeler à chaque modification de la disposition. Pour ce faire, remplacez <xref:System.Windows.Forms.Control.OnLayout%2A> et appelez <xref:System.Windows.Forms.Control.Refresh%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#70)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#70](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#70)]

## <a name="create-a-custom-designer-to-shadow-and-filter-properties"></a>Créer un concepteur personnalisé pour masquer et filtrer les propriétés

La classe `MarqueeControlRootDesigner` fournit l’implémentation du concepteur racine. En plus de ce concepteur, qui s’exécute sur le `MarqueeControl`, vous avez besoin d’un concepteur personnalisé qui est spécifiquement associé au contrôle `MarqueeBorder`. Ce concepteur fournit un comportement personnalisé approprié dans le contexte du concepteur racine personnalisé.

Plus précisément, le `MarqueeBorderDesigner` « occulte » et filtre certaines propriétés sur le contrôle `MarqueeBorder`, en modifiant leur interaction avec l’environnement de conception.

L’interception des appels à l’accesseur de propriété d’un composant est appelée « occultation ». Il permet à un concepteur de suivre la valeur définie par l’utilisateur et de passer éventuellement cette valeur au composant en cours de conception.

Pour cet exemple, les propriétés <xref:System.Windows.Forms.Control.Visible%2A> et <xref:System.Windows.Forms.Control.Enabled%2A> seront occultées par le `MarqueeBorderDesigner`, ce qui empêche l’utilisateur de rendre le contrôle `MarqueeBorder` invisible ou désactivé au moment de la conception.

Les concepteurs peuvent également ajouter et supprimer des propriétés. Pour cet exemple, la propriété <xref:System.Windows.Forms.Control.Padding%2A> sera supprimée au moment de la conception, car le contrôle `MarqueeBorder` définit par programmation le remplissage en fonction de la taille des lumières spécifiées par la propriété `LightSize`.

La classe de base pour `MarqueeBorderDesigner` est <xref:System.ComponentModel.Design.ComponentDesigner>, qui a des méthodes qui peuvent modifier les attributs, les propriétés et les événements exposés par un contrôle au moment du design :

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterProperties%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterAttributes%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterEvents%2A>

- <xref:System.ComponentModel.Design.ComponentDesigner.PostFilterEvents%2A>

Lors de la modification de l’interface publique d’un composant à l’aide de ces méthodes, procédez comme suit :

- Ajouter ou supprimer des éléments uniquement dans les méthodes `PreFilter`

- Modifier uniquement les éléments existants dans les méthodes `PostFilter`

- Appelez toujours l’implémentation de base en premier dans les méthodes `PreFilter`

- Appelez toujours l’implémentation de base en dernier dans les méthodes `PostFilter`

L’adhésion à ces règles garantit que tous les concepteurs dans l’environnement au moment du design disposent d’une vue cohérente de tous les composants en cours de conception.

La classe <xref:System.ComponentModel.Design.ComponentDesigner> fournit un dictionnaire pour gérer les valeurs des propriétés occultées, ce qui vous évite d’avoir à créer des variables d’instance spécifiques.

### <a name="to-create-a-custom-designer-to-shadow-and-filter-properties"></a>Pour créer un concepteur personnalisé pour masquer et filtrer les propriétés

1. Cliquez avec le bouton droit sur le dossier **Design** et ajoutez une nouvelle classe. Donnez au fichier source un nom de base **MarqueeBorderDesigner**.

2. Ouvrez le fichier source MarqueeBorderDesigner dans l' **éditeur de code**. En haut du fichier, importez les espaces de noms suivants :

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#420)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#420](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#420)]

3. Modifiez la déclaration de `MarqueeBorderDesigner` pour qu’elle hérite de <xref:System.Windows.Forms.Design.ParentControlDesigner>.

    Étant donné que le contrôle `MarqueeBorder` peut contenir des contrôles enfants, `MarqueeBorderDesigner` hérite de <xref:System.Windows.Forms.Design.ParentControlDesigner>, qui gère l’interaction parent-enfant.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#430)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#430](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#430)]

4. Substituez l’implémentation de base de <xref:System.ComponentModel.Design.ComponentDesigner.PreFilterProperties%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#450)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#450](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#450)]

5. Implémentez les propriétés <xref:System.Windows.Forms.Control.Enabled%2A> et <xref:System.Windows.Forms.Control.Visible%2A>. Ces implémentations occultent les propriétés du contrôle.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborderdesigner.cs#440)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#440](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborderdesigner.vb#440)]

## <a name="handle-component-changes"></a>Gérer les modifications des composants

La classe `MarqueeControlRootDesigner` fournit l’expérience au moment du design personnalisée pour vos instances de `MarqueeControl`. La plupart des fonctionnalités au moment du design sont héritées de la classe <xref:System.Windows.Forms.Design.DocumentDesigner>. Votre code implémentera deux personnalisations spécifiques : la gestion des modifications de composants et l’ajout de verbes de concepteur.

À mesure que les utilisateurs conçoivent leurs instances `MarqueeControl`, votre concepteur racine effectue le suivi des modifications apportées au `MarqueeControl` et à ses contrôles enfants. L’environnement au moment du design offre un service pratique, <xref:System.ComponentModel.Design.IComponentChangeService>, pour le suivi des modifications apportées à l’état du composant.

Vous obtenez une référence à ce service en interrogeant l’environnement avec la méthode <xref:System.ComponentModel.Design.ComponentDesigner.GetService%2A>. Si la requête réussit, votre concepteur peut attacher un gestionnaire pour l’événement <xref:System.ComponentModel.Design.IComponentChangeService.ComponentChanged> et effectuer toutes les tâches requises pour maintenir un état cohérent au moment de la conception.

Dans le cas de la classe `MarqueeControlRootDesigner`, vous devez appeler la méthode <xref:System.Windows.Forms.Control.Refresh%2A> sur chaque objet `IMarqueeWidget` contenu dans le `MarqueeControl`. L’objet `IMarqueeWidget` se redessine ainsi de manière appropriée lorsque des propriétés telles que les <xref:System.Windows.Forms.Control.Size%2A> de son parent sont modifiées.

### <a name="to-handle-component-changes"></a>Pour gérer les modifications de composants

1. Ouvrez le `MarqueeControlRootDesigner` fichier source dans l' **éditeur de code** et remplacez la méthode <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>. Appelez l’implémentation de base de <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A> et recherchez la <xref:System.ComponentModel.Design.IComponentChangeService>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#580)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#580](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#580)]

2. Implémentez le gestionnaire d’événements <xref:System.ComponentModel.Design.IComponentChangeService.OnComponentChanged%2A>. Testez le type du composant d’envoi et, s’il s’agit d’un `IMarqueeWidget`, appelez sa méthode <xref:System.Windows.Forms.Control.Refresh%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#560)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#560](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#560)]

## <a name="add-designer-verbs-to-your-custom-designer"></a>Ajouter des verbes de concepteur à votre concepteur personnalisé

Un verbe de concepteur est une commande de menu liée à un gestionnaire d'événements. Les verbes de concepteur sont ajoutés au menu contextuel d’un composant au moment du Design. Pour plus d'informations, consultez <xref:System.ComponentModel.Design.DesignerVerb>.

Vous allez ajouter deux verbes de concepteur à vos concepteurs : **exécuter le test** et **arrêter le test**. Ces verbes vous permettent d’afficher le comportement au moment de l’exécution du `MarqueeControl` au moment de la conception. Ces verbes seront ajoutés à `MarqueeControlRootDesigner`.

Lorsque l’exécution d’un **test** est appelée, le gestionnaire d’événements de verbe appelle la méthode `StartMarquee` sur l' `MarqueeControl`. Lorsque l’opération **arrêter le test** est appelée, le gestionnaire d’événements de verbe appelle la méthode `StopMarquee` sur l' `MarqueeControl`. L’implémentation des méthodes `StartMarquee` et `StopMarquee` appelle ces méthodes sur les contrôles contenus qui implémentent `IMarqueeWidget`, donc tous les contrôles `IMarqueeWidget` contenus participent également au test.

### <a name="to-add-designer-verbs-to-your-custom-designers"></a>Pour ajouter des verbes de concepteur à vos concepteurs personnalisés

1. Dans la classe `MarqueeControlRootDesigner`, ajoutez des gestionnaires d’événements nommés `OnVerbRunTest` et `OnVerbStopTest`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#570)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#570](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#570)]

2. Connectez ces gestionnaires d’événements à leurs verbes de concepteur correspondants. `MarqueeControlRootDesigner` hérite d’une <xref:System.ComponentModel.Design.DesignerVerbCollection> de sa classe de base. Vous allez créer deux nouveaux objets <xref:System.ComponentModel.Design.DesignerVerb> et les ajouter à cette collection dans la méthode <xref:System.Windows.Forms.Design.DocumentDesigner.Initialize%2A>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueecontrolrootdesigner.cs#590)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#590](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueecontrolrootdesigner.vb#590)]

## <a name="create-a-custom-uitypeeditor"></a>Créer un UITypeEditor personnalisé

Quand vous créez une expérience personnalisée au moment de la conception pour les utilisateurs, il est souvent préférable de créer une interaction personnalisée avec l’Fenêtre Propriétés. Pour ce faire, vous pouvez créer un <xref:System.Drawing.Design.UITypeEditor>.

Le contrôle `MarqueeBorder` expose plusieurs propriétés dans le Fenêtre Propriétés. Deux de ces propriétés, `MarqueeSpinDirection` et `MarqueeLightShape` sont représentées par des énumérations. Pour illustrer l’utilisation d’un éditeur de type d’interface utilisateur, la propriété `MarqueeLightShape` est associée à une classe <xref:System.Drawing.Design.UITypeEditor>.

### <a name="to-create-a-custom-ui-type-editor"></a>Pour créer un éditeur de types d’interface utilisateur personnalisé

1. Ouvrez le `MarqueeBorder` fichier source dans l' **éditeur de code**.

2. Dans la définition de la classe `MarqueeBorder`, déclarez une classe appelée `LightShapeEditor` qui dérive de <xref:System.Drawing.Design.UITypeEditor>.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#96)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#96](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#96)]

3. Déclarez une variable d’instance <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> appelée `editorService`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#92)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#92](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#92)]

4. Remplacez la méthode <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A> . Cette implémentation retourne <xref:System.Drawing.Design.UITypeEditorEditStyle.DropDown>, qui indique à l’environnement de conception comment afficher les `LightShapeEditor`.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#93)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#93](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#93)]

5. Remplacez la méthode <xref:System.Drawing.Design.UITypeEditor.EditValue%2A> . Cette implémentation interroge l’environnement de conception pour un objet <xref:System.Windows.Forms.Design.IWindowsFormsEditorService>. En cas de réussite, elle crée un `LightShapeSelectionControl`. La méthode <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.DropDownControl%2A> est appelée pour démarrer le `LightShapeEditor`. La valeur de retour de cet appel est retournée à l’environnement de conception.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/marqueeborder.cs#94)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#94](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/marqueeborder.vb#94)]

## <a name="create-a-view-control-for-your-custom-uitypeeditor"></a>Créer un contrôle d’affichage pour votre UITypeEditor personnalisé

La propriété `MarqueeLightShape` prend en charge deux types de formes d’éclairage : `Square` et `Circle`. Vous allez créer un contrôle personnalisé utilisé uniquement dans le cadre de l’affichage graphique de ces valeurs dans la Fenêtre Propriétés. Ce contrôle personnalisé sera utilisé par votre <xref:System.Drawing.Design.UITypeEditor> pour interagir avec le Fenêtre Propriétés.

### <a name="to-create-a-view-control-for-your-custom-ui-type-editor"></a>Pour créer un contrôle d’affichage pour votre éditeur de type d’interface utilisateur personnalisé

1. Ajoutez un nouvel élément <xref:System.Windows.Forms.UserControl> au projet `MarqueeControlLibrary`. Donnez au nouveau fichier source un nom de base de **LightShapeSelectionControl**.

2. Faites glisser deux contrôles <xref:System.Windows.Forms.Panel> de la **boîte à outils** vers le `LightShapeSelectionControl`. Nommez-les `squarePanel` et `circlePanel`. Organisez-les côte à côte. Affectez à la propriété <xref:System.Windows.Forms.Control.Size%2A> des deux contrôles <xref:System.Windows.Forms.Panel> la valeur **(60, 60)** . Affectez à la propriété <xref:System.Windows.Forms.Control.Location%2A> du contrôle `squarePanel` la valeur **(8, 10)** . Affectez à la propriété <xref:System.Windows.Forms.Control.Location%2A> du contrôle `circlePanel` la valeur **(80, 10)** . Enfin, affectez à la propriété <xref:System.Windows.Forms.Control.Size%2A> du `LightShapeSelectionControl` la valeur **(150, 80)** .

3. Ouvrez le `LightShapeSelectionControl` fichier source dans l' **éditeur de code**. En haut du fichier, importez l’espace de noms <xref:System.Windows.Forms.Design?displayProperty=nameWithType> :

   ```vb
   Imports System.Windows.Forms.Design
   ```

   ```csharp
   using System.Windows.Forms.Design;
   ```

4. Implémentez <xref:System.Windows.Forms.Control.Click> gestionnaires d’événements pour les contrôles `squarePanel` et `circlePanel`. Ces méthodes appellent <xref:System.Windows.Forms.Design.IWindowsFormsEditorService.CloseDropDown%2A> pour mettre fin à la session de modification <xref:System.Drawing.Design.UITypeEditor> personnalisée.

    [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#390)]
    [!code-vb[System.Windows.Forms.Design.DocumentDesigner#390](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#390)]

5. Déclarez une variable d’instance <xref:System.Windows.Forms.Design.IWindowsFormsEditorService> appelée `editorService`.

   ```vb
   Private editorService As IWindowsFormsEditorService
   ```

   ```csharp
   private IWindowsFormsEditorService editorService;
   ```

6. Déclarez une variable d’instance `MarqueeLightShape` appelée `lightShapeValue`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#330)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#330](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#330)]

7. Dans le constructeur `LightShapeSelectionControl`, attachez les gestionnaires d’événements <xref:System.Windows.Forms.Control.Click> à la `squarePanel` et aux événements <xref:System.Windows.Forms.Control.Click> contrôles de `circlePanel`. Définissez également une surcharge de constructeur qui assigne la valeur `MarqueeLightShape` de l’environnement de conception au champ `lightShapeValue`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#340)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#340](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#340)]

8. Dans la méthode <xref:System.ComponentModel.Component.Dispose%2A>, détachez les gestionnaires d’événements <xref:System.Windows.Forms.Control.Click>.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#350)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#350](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#350)]

9. Dans l’**Explorateur de solutions**, cliquez sur le bouton **Afficher tous les fichiers**. Ouvrez le fichier LightShapeSelectionControl.Designer.cs ou LightShapeSelectionControl. Designer. vb, puis supprimez la définition par défaut de la méthode <xref:System.ComponentModel.Component.Dispose%2A>.

10. Implémentez la propriété `LightShape`.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#360)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#360](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#360)]

11. Remplacez la méthode <xref:System.Windows.Forms.Control.OnPaint%2A> . Cette implémentation dessinera un carré rempli et un cercle. Il met également en surbrillance la valeur sélectionnée en dessinant une bordure autour d’une forme ou de l’autre.

     [!code-csharp[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/CS/lightshapeselectioncontrol.cs#380)]
     [!code-vb[System.Windows.Forms.Design.DocumentDesigner#380](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Design.DocumentDesigner/VB/lightshapeselectioncontrol.vb#380)]

## <a name="test-your-custom-control-in-the-designer"></a>Tester votre contrôle personnalisé dans le concepteur

À ce stade, vous pouvez générer le projet `MarqueeControlLibrary`. Testez votre implémentation en créant un contrôle qui hérite de la classe `MarqueeControl` et en l’utilisant sur un formulaire.

### <a name="to-create-a-custom-marqueecontrol-implementation"></a>Pour créer une implémentation de MarqueeControl personnalisée

1. Ouvrez `DemoMarqueeControl` dans le Concepteur Windows Forms. Cela crée une instance du type de `DemoMarqueeControl` et l’affiche dans une instance du type de `MarqueeControlRootDesigner`.

2. Dans la **boîte à outils**, ouvrez l’onglet **composants MarqueeControlLibrary** . Vous verrez les contrôles `MarqueeBorder` et `MarqueeText` disponibles pour la sélection.

3. Faites glisser une instance du contrôle `MarqueeBorder` sur l’aire de conception `DemoMarqueeControl`. Ancrez ce contrôle de `MarqueeBorder` au contrôle parent.

4. Faites glisser une instance du contrôle `MarqueeText` sur l’aire de conception `DemoMarqueeControl`.

5. Générez la solution.

6. Cliquez avec le bouton droit sur le `DemoMarqueeControl` puis, dans le menu contextuel, sélectionnez l’option **exécuter le test** pour démarrer l’animation. Cliquez sur **arrêter le test** pour arrêter l’animation.

7. Ouvrez **Form1** en mode Création.

8. Placez deux contrôles <xref:System.Windows.Forms.Button> sur le formulaire. Nommez-les `startButton` et `stopButton`, puis remplacez les valeurs de propriété <xref:System.Windows.Forms.Control.Text%2A> par **Start** et **Stop**, respectivement.

9. Implémentez <xref:System.Windows.Forms.Control.Click> gestionnaires d’événements pour les deux contrôles <xref:System.Windows.Forms.Button>.

10. Dans la **boîte à outils**, ouvrez l’onglet **composants de MarqueeControlTest** . Vous verrez les `DemoMarqueeControl` disponibles pour la sélection.

11. Faites glisser une instance de `DemoMarqueeControl` sur l’aire de conception de **Form1** .

12. Dans les gestionnaires d’événements <xref:System.Windows.Forms.Control.Click>, appelez les méthodes `Start` et `Stop` sur le `DemoMarqueeControl`.

    ```vb
    Private Sub startButton_Click(sender As Object, e As System.EventArgs)
        Me.demoMarqueeControl1.Start()
    End Sub 'startButton_Click

    Private Sub stopButton_Click(sender As Object, e As System.EventArgs)
    Me.demoMarqueeControl1.Stop()
    End Sub 'stopButton_Click
    ```

    ```csharp
    private void startButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Start();
    }

    private void stopButton_Click(object sender, System.EventArgs e)
    {
        this.demoMarqueeControl1.Stop();
    }
    ```

13. Définissez le projet `MarqueeControlTest` comme projet de démarrage, puis exécutez-le. Le formulaire affichant votre `DemoMarqueeControl`s’affiche. Sélectionnez le bouton **Démarrer** pour démarrer l’animation. Vous devez voir le texte clignotant et les lumières qui se déplacent dans la bordure.

## <a name="next-steps"></a>Étapes suivantes :

Le `MarqueeControlLibrary` illustre une implémentation simple des contrôles personnalisés et des concepteurs associés. Vous pouvez rendre cet exemple plus sophistiqué de plusieurs façons :

- Modifiez les valeurs des propriétés de la `DemoMarqueeControl` dans le concepteur. Ajoutez des contrôles de `MarqueBorder` supplémentaires et ancrez-les dans leurs instances parentes pour créer un effet imbriqué. Expérimentez des paramètres différents pour la `UpdatePeriod` et les propriétés liées à la lumière.

- Créez vos propres implémentations de `IMarqueeWidget`. Vous pouvez, par exemple, créer un « symbole néon » clignotant ou un signe animé avec plusieurs images.

- Personnalisez davantage l’expérience au moment de la conception. Vous pouvez essayer d’occulter plus de propriétés que <xref:System.Windows.Forms.Control.Enabled%2A> et <xref:System.Windows.Forms.Control.Visible%2A>, et vous pouvez ajouter de nouvelles propriétés. Ajoutez de nouveaux verbes de concepteur pour simplifier les tâches courantes, comme l’ancrage des contrôles enfants.

- Licence du `MarqueeControl`.

- Contrôlez la façon dont vos contrôles sont sérialisés et la façon dont le code est généré pour eux. Pour plus d’informations, consultez [génération et compilation de code source dynamique](../../reflection-and-codedom/dynamic-source-code-generation-and-compilation.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Design.ParentControlDesigner>
- <xref:System.Windows.Forms.Design.DocumentDesigner>
- <xref:System.ComponentModel.Design.IRootDesigner>
- <xref:System.ComponentModel.Design.DesignerVerb>
- <xref:System.Drawing.Design.UITypeEditor>
- <xref:System.ComponentModel.BackgroundWorker>
