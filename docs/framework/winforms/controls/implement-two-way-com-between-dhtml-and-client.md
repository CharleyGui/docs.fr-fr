---
title: 'Procédure : implémenter une communication bidirectionnelle entre le code DHTML et le code de l’application cliente'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
ms.openlocfilehash: 45df54b3a590078eff6ddc1197db5b0124663cf5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971920"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Procédure : implémenter une communication bidirectionnelle entre le code DHTML et le code de l’application cliente

Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.WebBrowser> pour ajouter du code d'application web dynamique HTML (DHTML) existant à vos applications clientes Windows Forms. Cela est utile quand vous avez consacré beaucoup de temps de développement à la création de contrôles DHTML et que vous souhaitez tirer parti des fonctionnalités d'interface utilisateur enrichies des Windows Forms sans avoir à réécrire le code existant.

Le contrôle <xref:System.Windows.Forms.WebBrowser> vous permet d'implémenter la communication bidirectionnelle entre votre code d'application cliente et votre code de script de page web par le biais des propriétés <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> et <xref:System.Windows.Forms.WebBrowser.Document%2A>. Vous pouvez aussi configurer le contrôle <xref:System.Windows.Forms.WebBrowser> pour que vos contrôles web fusionnent de façon homogène avec d'autres contrôles sur votre formulaire d'application, en masquant leur implémentation DHTML. Pour fusionner les contrôles de façon homogène, mettez en forme la page affichée pour que sa couleur d'arrière-plan et le style visuel correspondent au reste du formulaire et utilisez les propriétés <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> et <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> pour désactiver les fonctionnalités standard du navigateur.

## <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Pour incorporer du code DHTML dans votre application Windows Forms

1. Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> du contrôle <xref:System.Windows.Forms.WebBrowser> pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'ouvrir les fichiers qui sont déposés dessus.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]

2. Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> du contrôle pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'afficher son menu contextuel quand l'utilisateur clique dessus avec le bouton droit de la souris.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]

3. Affectez la valeur `false` à la propriété <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> du contrôle pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> de répondre aux touches de raccourci.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]

4. Définissez la propriété <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> dans le constructeur du formulaire ou un gestionnaire d'événements <xref:System.Windows.Forms.Form.Load>.

     Le code suivant utilise la classe de formulaire proprement dite pour l'objet de script.

    > [!NOTE]
    >  Le modèle COM (Component Object Model) doit pouvoir accéder à l'objet de script. Pour rendre votre formulaire visible par COM, ajoutez l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> à votre classe de formulaire.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]

5. Implémentez dans votre code d'application des propriétés ou des méthodes publiques que votre code de script utilisera.

     Par exemple, si vous utilisez la classe de formulaire pour l'objet de script, ajoutez le code suivant à votre classe de formulaire.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]

6. Utilisez l'objet `window.external` dans votre code de script pour accéder aux propriétés et aux méthodes publiques de l'objet spécifié.

     Le code HTML suivant montre comment appeler une méthode sur l'objet de script à partir d'un clic de bouton. Copiez ce code dans l'élément BODY d'un document HTML que vous chargez à l'aide de la méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> du contrôle ou que vous affectez à la propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> du contrôle.

    ```html
    <button onclick="window.external.Test('called from script code')">
        call client code from script code
    </button>
    ```

7. Implémentez dans votre code de script des fonctions que votre code d'application utilisera.

     L'élément HTML SCRIPT suivant fournit un exemple de fonction. Copiez ce code dans l'élément HEAD d'un document HTML que vous chargez à l'aide de la méthode <xref:System.Windows.Forms.WebBrowser.Navigate%2A> du contrôle ou que vous affectez à la propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> du contrôle.

    ```html
    <script>
    function test(message) {
        alert(message);
    }
    </script>
    ```

8. Utilisez la propriété <xref:System.Windows.Forms.WebBrowser.Document%2A> pour accéder au code de script à partir de votre code d'application cliente.

     Par exemple, ajoutez le code suivant à un gestionnaire d'événements de bouton <xref:System.Windows.Forms.Control.Click>.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]

9. Quand vous avez terminé de déboguer votre code DHTML, affectez la valeur `true` à la propriété <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> du contrôle pour empêcher le contrôle <xref:System.Windows.Forms.WebBrowser> d'afficher des messages d'erreur pour les problèmes de code de script.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]

## <a name="example"></a>Exemple

L’exemple de code complet suivant fournit une application de démonstration que vous pouvez utiliser pour comprendre cette fonctionnalité. Le code HTML est chargé dans le contrôle <xref:System.Windows.Forms.WebBrowser> via la propriété <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> au lieu d'être chargé à partir d'un fichier HTML distinct.

[!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]

## <a name="compiling-the-code"></a>Compilation du code

Ce code nécessite :

- des références aux assemblys System et System.Windows.Forms ;

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [WebBrowser, contrôle](webbrowser-control-windows-forms.md)
