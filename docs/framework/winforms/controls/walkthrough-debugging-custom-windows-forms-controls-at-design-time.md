---
title: Déboguer des contrôles personnalisés au moment du design
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9e292a1219c24571bcb35db2fe357b0197c8812
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740185"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a>Procédure pas à pas : déboguer des contrôles Windows Forms personnalisés au moment du design

Lorsque vous créez un contrôle personnalisé, il est souvent nécessaire de déboguer son comportement au moment du Design. Cela est particulièrement vrai si vous créez un concepteur personnalisé pour votre contrôle personnalisé. Pour plus d’informations, consultez [procédure pas à pas : création d’un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](creating-a-wf-control-design-time-features.md).

Vous pouvez déboguer vos contrôles personnalisés à l’aide de Visual Studio, tout comme vous le feriez pour tout autre .NET Framework classes. La différence réside dans le fait que vous allez déboguer une instance distincte de Visual Studio qui exécute le code de votre contrôle personnalisé.

## <a name="create-the-project"></a>Créer le projet

La première étape consiste à créer le projet d’application. Vous allez utiliser ce projet pour générer l’application qui héberge le contrôle personnalisé.

Dans Visual Studio, créez un projet d’application Windows et nommez-le **DebuggingExample**.

## <a name="create-the-control-library-project"></a>Créer le projet de bibliothèque de contrôles

1. Ajoutez un projet de **bibliothèque de contrôles Windows** à la solution.

2. Ajoutez un nouvel élément **UserControl** au projet DebugControlLibrary. Nommez-le **DebugControl**.

3. Dans **Explorateur de solutions**, supprimez le contrôle par défaut du projet en supprimant le fichier de code portant le nom de base UserControl1.

4. Générez la solution.

## <a name="checkpoint"></a>Point de contrôle

À ce stade, vous serez en mesure de voir votre contrôle personnalisé dans la **boîte à outils**.

Pour vérifier votre progression, recherchez le nouvel onglet appelé le **composant DebugControlLibrary** , puis cliquez dessus pour le sélectionner. Lorsqu’il s’ouvre, votre contrôle est affiché en tant que **DebugControl** avec l’icône par défaut en regard.

## <a name="add-a-property-to-your-custom-control"></a>Ajouter une propriété à votre contrôle personnalisé

Pour montrer que le code de votre contrôle personnalisé est en cours d’exécution au moment de la conception, vous allez ajouter une propriété et définir un point d’arrêt dans le code qui implémente la propriété.

1. Ouvrez **DebugControl** dans l' **éditeur de code**. Ajoutez le code suivant à la définition de classe :

    ```vb
    Private demoStringValue As String = Nothing
    <BrowsableAttribute(true)>
    Public Property DemoString() As String

        Get
            Return Me.demoStringValue
        End Get

        Set(ByVal value As String)
            Me.demoStringValue = value
        End Set

    End Property
    ```

    ```csharp
    private string demoStringValue = null;
    [Browsable(true)]
    public string DemoString
    {
        get
        {
            return this.demoStringValue;
        }
        set
        {
            demoStringValue = value;
        }
    }
    ```

2. Générez la solution.

## <a name="add-your-custom-control-to-the-host-form"></a>Ajouter votre contrôle personnalisé au formulaire hôte

Pour déboguer le comportement au moment du design de votre contrôle personnalisé, vous devez placer une instance de la classe de contrôle personnalisé sur un formulaire hôte.

1. Dans le projet « DebuggingExample », ouvrez Formulaire1 dans le **Concepteur Windows Forms**.

2. Dans la **boîte à outils**, ouvrez l’onglet **Composants DebugControlLibrary** et faites glisser une instance **DebugControl** sur le formulaire.

3. Recherchez la propriété personnalisée `DemoString` dans la fenêtre **Propriétés** . Notez que vous pouvez modifier sa valeur comme n’importe quelle autre propriété. Notez également que lorsque la propriété `DemoString` est sélectionnée, la chaîne de description de la propriété apparaît en bas de la fenêtre **Propriétés** .

## <a name="set-up-the-project-for-design-time-debugging"></a>Configurer le projet pour le débogage au moment du design

Pour déboguer le comportement au moment du design de votre contrôle personnalisé, vous allez déboguer une instance distincte de Visual Studio qui exécute le code de votre contrôle personnalisé.

1. Cliquez avec le bouton droit sur le projet **DebugControlLibrary** dans le **Explorateur de solutions** , puis sélectionnez **Propriétés**.

2. Dans la feuille de propriétés **DebugControlLibrary** , sélectionnez l’onglet **Déboguer** .

     Dans la section **action de démarrage** , sélectionnez Démarrer le **programme externe**. Vous allez déboguer une instance distincte de Visual Studio. par conséquent, cliquez sur les points de suspension (![le bouton de sélection (...) du bouton Fenêtre Propriétés de Visual Studio](./media/visual-studio-ellipsis-button.png)) pour Rechercher l’IDE de Visual Studio. Le nom du fichier exécutable est **devenv. exe**, et si vous avez installé à l’emplacement par défaut, son chemin d’accès est *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE*.

3. Sélectionnez **OK** pour fermer la boîte de dialogue.

4. Cliquez avec le bouton droit sur le projet **DebugControlLibrary** et sélectionnez **définir comme projet de démarrage** pour activer cette configuration de débogage.

## <a name="debug-your-custom-control-at-design-time"></a>Déboguer votre contrôle personnalisé au moment du design

Vous êtes maintenant prêt à déboguer votre contrôle personnalisé lorsqu’il s’exécute en mode création. Quand vous démarrez la session de débogage, une nouvelle instance de Visual Studio est créée. vous l’utiliserez pour charger la solution « DebuggingExample ». Quand vous ouvrez Form1 dans le **Concepteur de formulaires**, une instance de votre contrôle personnalisé est créée et commence à s’exécuter.

1. Ouvrez le fichier source **DebugControl** dans l' **éditeur de code** et placez un point d’arrêt sur l’accesseur `Set` de la propriété `DemoString`.

2. Appuyez sur **F5** pour démarrer la session de débogage. Une nouvelle instance de Visual Studio est créée. Vous pouvez faire la distinction entre les instances de deux manières :

    - Le mot est en **cours d’exécution** dans la barre de titre de l’instance de débogage

    - Le bouton **Démarrer** de la barre d’outils de **débogage de** l’instance de débogage est désactivé

   Votre point d’arrêt est défini dans l’instance de débogage.

3. Dans la nouvelle instance de Visual Studio, ouvrez la solution « DebuggingExample ». Vous pouvez facilement trouver la solution en sélectionnant **projets récents** dans le menu **fichier** . Le fichier solution « DebuggingExample. sln » est listé comme le fichier le plus récemment utilisé.

4. Ouvrez Form1 dans le **Concepteur de formulaires** et sélectionnez le contrôle **DebugControl** .

5. Modifiez la valeur de la propriété `DemoString` . Lorsque vous validez la modification, l’instance de débogage de Visual Studio acquiert le focus et l’exécution s’arrête à votre point d’arrêt. Vous pouvez effectuer un pas à pas détaillé dans l’accesseur de propriété comme pour tout autre code.

6. Pour arrêter le débogage, quittez l’instance hébergée de Visual Studio ou sélectionnez le bouton **arrêter le débogage** dans l’instance de débogage.

## <a name="next-steps"></a>Étapes suivantes :

Maintenant que vous pouvez déboguer vos contrôles personnalisés au moment de la conception, il existe de nombreuses possibilités pour étendre l’interaction de votre contrôle avec l’IDE de Visual Studio.

- Vous pouvez utiliser la propriété <xref:System.ComponentModel.Component.DesignMode%2A> de la classe <xref:System.ComponentModel.Component> pour écrire du code qui s’exécute uniquement au moment du Design. Pour plus d'informations, consultez <xref:System.ComponentModel.Component.DesignMode%2A>.

- Il existe plusieurs attributs que vous pouvez appliquer aux propriétés de votre contrôle pour manipuler l’interaction de votre contrôle personnalisé avec le concepteur. Vous pouvez trouver ces attributs dans l’espace de noms <xref:System.ComponentModel?displayProperty=nameWithType>.

- Vous pouvez écrire un concepteur personnalisé pour votre contrôle personnalisé. Vous bénéficiez ainsi d’un contrôle total sur l’expérience de conception à l’aide de l’infrastructure de concepteur extensible exposée par Visual Studio. Pour plus d’informations, consultez [procédure pas à pas : création d’un contrôle de Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](creating-a-wf-control-design-time-features.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : création d’un contrôle Windows Forms qui tire parti des fonctionnalités au moment du design de Visual Studio](creating-a-wf-control-design-time-features.md)
