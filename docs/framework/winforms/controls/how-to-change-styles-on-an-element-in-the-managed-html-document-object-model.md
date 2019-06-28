---
title: 'Procédure : modifier des styles dans un élément du modèle objet de document HTML managé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 728bc77db959e25fe31d2ff37288b2359dca852e
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424590"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>Procédure : modifier des styles dans un élément du modèle objet de document HTML managé

Vous pouvez utiliser des styles HTML pour contrôler l’apparence d’un document et ses éléments. <xref:System.Windows.Forms.HtmlDocument> et <xref:System.Windows.Forms.HtmlElement> prennent en charge <xref:System.Windows.Forms.HtmlElement.Style%2A> propriétés qui acceptent des chaînes de style au format suivant :

`name1:value1;...;nameN:valueN;`

Voici un `DIV` avec une chaîne de style qui définit la police Arial et tout le texte en gras :

```html
<DIV style="font-face:arial;font-weight:bold;">
Hello, world!
</DIV>
```

Le problème de la manipulation de styles à l’aide de la <xref:System.Windows.Forms.HtmlElement.Style%2A> propriété est qu’il peut s’avérer difficile à ajouter à et supprimez les paramètres de style de la chaîne. Par exemple, il devient une procédure complexe vous permettant de restituer le texte précédent en italique chaque fois que l’utilisateur positionne le curseur sur le `DIV`et les caractères en italique lorsque le curseur quitte la `DIV`. Un problème prendrait trop de temps si vous avez besoin manipuler un grand nombre de styles de cette manière.

La procédure suivante contient le code que vous pouvez utiliser pour manipuler facilement des styles sur les éléments et les documents HTML. La procédure requiert que vous savez comment effectuer des tâches de base dans les formulaires Windows, telles que la création d’un projet et l’ajout d’un contrôle à un formulaire.

### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Pour traiter les modifications de style dans une application Windows Forms

1. Créez un projet Windows Forms.

2. Créer un nouveau fichier de classe se terminant par l’extension appropriée pour votre langage de programmation.

3. Copie la `StyleGenerator` classe de code dans la section exemple de cette rubrique dans le fichier de classe et enregistrez le code.

4. Enregistrez le code HTML suivant dans un fichier nommé Test.htm.

    ```html
    <HTML>
        <BODY>

            <DIV style="font-face:arial;font-weight:bold;">
                Hello, world!
            </DIV><P>

            <DIV>
                Hello again, world!
            </DIV><P>

        </BODY>
    </HTML>
    ```

5. Ajouter un <xref:System.Windows.Forms.WebBrowser> contrôle nommé `webBrowser1` au formulaire principal de votre projet.

6. Ajoutez le code suivant au fichier de code de votre projet.

    > [!IMPORTANT]
    > Vérifiez que le `webBrowser1_DocumentCompleted` Gestionnaire d’événements est configuré en tant qu’écouteur pour le <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> événement. Dans Visual Studio, double-cliquez sur le <xref:System.Windows.Forms.WebBrowser> contrôler ; dans un éditeur de texte, configurez l’écouteur par programme.

     [!code-csharp[ManagedDOMStyles#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]

7. Exécuter le projet. Exécutez votre curseur sur la première `DIV` pour observer les effets du code.

## <a name="example"></a>Exemple

L’exemple de code suivant montre le code complet pour le `StyleGenerator` (classe), qui analyse une valeur de style existante, prend en charge l’ajout, modification et suppression de styles et retourne une nouvelle valeur de style avec les modifications demandées.

[!code-csharp[ManagedDOMStyles#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
[!code-vb[ManagedDOMStyles#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.HtmlElement>
