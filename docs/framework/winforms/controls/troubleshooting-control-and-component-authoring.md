---
title: Dépannage de la création de contrôles et de composants
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2e0b98107ac5f43c80aad6cb5ea61e6f4e1e28d3
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015712"
---
# <a name="troubleshoot-control-and-component-authoring"></a>Résoudre les problèmes de création de contrôles et de composants

Cette rubrique répertorie les problèmes courants suivants qui se produisent lors du développement de composants et de contrôles:

- Impossible d’ajouter le contrôle à la boîte à outils

- Impossible de déboguer le composant ou contrôle utilisateur Windows Forms

- Un événement est généré deux fois dans le composant ou le contrôle hérité

- Erreur au moment de la conception: «Impossible de créer le composant'*nom du composant*'»

- STAThreadAttribute

- L’icône du composant n’apparaît pas dans la boîte à outils

## <a name="cannot-add-control-to-toolbox"></a>Impossible d’ajouter le contrôle à la boîte à outils

Si vous souhaitez ajouter un contrôle personnalisé que vous avez créé dans un autre projet ou un contrôle tiers pour la **boîte à outils**, vous devez le faire manuellement. Si le projet actuel contient votre contrôle ou composant, il doit apparaître automatiquement dans la **boîte à outils**. Pour plus d’informations, consultez [Procédure pas à pas : Remplissage automatique de la boîte à outils](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)avec des composants personnalisés.

### <a name="to-add-a-control-to-the-toolbox"></a>Pour ajouter un contrôle à la boîte à outils

1. Cliquez avec le bouton droit sur la **boîte à outils** et sélectionnez **Choisir les éléments** dans le menu contextuel.

2. Dans la boîte de dialogue **Choisir des éléments de boîte à outils**, ajoutez le composant :

    - Si vous souhaitez ajouter un contrôle ou un composant .NET Framework, cliquez sur l’onglet **Composants .NET Framework**.

         – ou –

    - Si vous souhaitez ajouter un composant COM ou un contrôle ActiveX, cliquez sur l’onglet **Composants COM**.

3. Si votre contrôle est répertorié dans la boîte de dialogue, vérifiez qu’il est sélectionné, puis cliquez sur **OK**.

     Le contrôle est ajouté à la **boîte à outils**.

4. Si votre contrôle n’est pas répertorié dans la boîte de dialogue, procédez comme suit :

    1. Cliquez sur le bouton **Parcourir**.

    2. Accédez au dossier contenant le fichier .dll qui contient votre contrôle.

    3. Sélectionnez le fichier .dll et cliquez sur **Ouvrir**.

         Votre contrôle s’affiche dans la boîte de dialogue.

    4. Vérifiez que votre contrôle est sélectionné, puis cliquez sur **OK**.

         Le contrôle est ajouté à la **boîte à outils**.

## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Impossible de déboguer le composant ou contrôle utilisateur Windows Forms

Si votre contrôle dérive de la <xref:System.Windows.Forms.UserControl> classe, vous pouvez déboguer son comportement au moment de l’exécution avec le conteneur de test. Pour plus d’informations, consultez [Guide pratique pour Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.

Les autres composants et contrôles personnalisés ne sont pas des projets autonomes. Ils doivent être hébergés par une application, telle qu’un projet Windows Forms. Pour déboguer un contrôle ou un composant, vous devez l’ajouter à un projet Windows Forms.

### <a name="to-debug-a-control-or-component"></a>Pour déboguer un contrôle ou un composant

1. Dans le menu **Générer**, cliquez sur **Générer la solution** pour générer votre solution.

2. Dans le menu **Fichier**, choisissez **Ajouter**, puis **Nouveau projet** pour ajouter un projet de test à votre application.

3. Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez **Application Windows** comme type de projet.

4. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre nouveau projet. Dans le menu contextuel, cliquez sur **Ajouter une référence** pour ajouter une référence au projet contenant le contrôle ou le composant.

5. Créez une instance de votre contrôle ou composant dans le projet de test. Si votre composant se trouve dans la **boîte à outils**, vous pouvez le faire glisser vers votre aire de concepteur, ou vous pouvez créer l’instance par programmation, comme illustré dans l’exemple de code suivant.

    ```vb
    Dim Component1 As New MyNeatComponent()
    ```

    ```csharp
    MyNeatComponent Component1 = new MyNeatComponent();
    ```

   Vous pouvez maintenant déboguer votre contrôle ou composant comme vous le faites habituellement.

Pour plus d’informations sur le débogage, consultez débogage [dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) et [procédure pas à pas: Débogage des contrôles de Windows Forms personnalisés au moment](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)du Design.

## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>Un événement est généré deux fois dans le composant ou le contrôle hérité

Cela est probablement dû à une clause `Handles` dupliquée. Pour plus d’informations, consultez l’article [Dépannage des gestionnaires d’événements hérités dans Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).

## <a name="design-time-error-failed-to-create-component-component-name"></a>Erreur au moment de la conception: «Impossible de créer le composant’nom du composant'»

Votre composant ou contrôle doit fournir un constructeur sans paramètre sans paramètres. Lorsque l’environnement de design crée une instance de votre composant ou de votre contrôle, il n’essaie pas de fournir des paramètres aux surcharges de constructeur qui prennent des paramètres.

## <a name="stathreadattribute"></a>STAThreadAttribute

<xref:System.STAThreadAttribute> Informe le Common Language Runtime (CLR) qui Windows Forms utilise le modèle à thread unique cloisonné. Vous pouvez constater un comportement inattendu si vous n’appliquez pas cet attribut à la méthode `Main` de votre application Windows Forms. Par exemple, les images d’arrière-plan peuvent ne <xref:System.Windows.Forms.ListView>pas apparaître pour les contrôles tels que. Certains contrôles peuvent également avoir besoin de cet attribut pour fournir un comportement approprié de saisie semi-automatique et de glisser-déplacer.

## <a name="component-icon-does-not-appear-in-toolbox"></a>L’icône du composant n’apparaît pas dans la boîte à outils

Lorsque vous utilisez <xref:System.Drawing.ToolboxBitmapAttribute> pour associer une icône à votre composant personnalisé, la bitmap n’apparaît pas dans la boîte à outils pour les composants générés automatiquement. Pour afficher l’image bitmap, rechargez le contrôle par le biais de la boîte de dialogue **Choisir des éléments de boîte à outils**. Pour plus d’informations, consultez [Guide pratique pour Fournissez une image bitmap de boîte](how-to-provide-a-toolbox-bitmap-for-a-control.md)à outils pour un contrôle.

## <a name="see-also"></a>Voir aussi

- [Développement de contrôles Windows Forms au moment du design](developing-windows-forms-controls-at-design-time.md)
- [Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [Guide pratique pour Tester le comportement d’un UserControl au moment de l’exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [Procédure pas à pas : Débogage des contrôles Windows Forms personnalisés au moment du design](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
