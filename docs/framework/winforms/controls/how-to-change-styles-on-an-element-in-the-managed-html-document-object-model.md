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
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a><span data-ttu-id="0990f-102">Procédure : modifier des styles dans un élément du modèle objet de document HTML managé</span><span class="sxs-lookup"><span data-stu-id="0990f-102">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>

<span data-ttu-id="0990f-103">Vous pouvez utiliser des styles HTML pour contrôler l’apparence d’un document et ses éléments.</span><span class="sxs-lookup"><span data-stu-id="0990f-103">You can use styles in HTML to control the appearance of a document and its elements.</span></span> <span data-ttu-id="0990f-104"><xref:System.Windows.Forms.HtmlDocument> et <xref:System.Windows.Forms.HtmlElement> prennent en charge <xref:System.Windows.Forms.HtmlElement.Style%2A> propriétés qui acceptent des chaînes de style au format suivant :</span><span class="sxs-lookup"><span data-stu-id="0990f-104"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> support <xref:System.Windows.Forms.HtmlElement.Style%2A> properties that take style strings of the following format:</span></span>

`name1:value1;...;nameN:valueN;`

<span data-ttu-id="0990f-105">Voici un `DIV` avec une chaîne de style qui définit la police Arial et tout le texte en gras :</span><span class="sxs-lookup"><span data-stu-id="0990f-105">Here is a `DIV` with a style string that sets the font to Arial and all text to bold:</span></span>

```html
<DIV style="font-face:arial;font-weight:bold;">
Hello, world!
</DIV>
```

<span data-ttu-id="0990f-106">Le problème de la manipulation de styles à l’aide de la <xref:System.Windows.Forms.HtmlElement.Style%2A> propriété est qu’il peut s’avérer difficile à ajouter à et supprimez les paramètres de style de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="0990f-106">The problem with manipulating styles using the <xref:System.Windows.Forms.HtmlElement.Style%2A> property is that it can prove cumbersome to add to and remove individual style settings from the string.</span></span> <span data-ttu-id="0990f-107">Par exemple, il devient une procédure complexe vous permettant de restituer le texte précédent en italique chaque fois que l’utilisateur positionne le curseur sur le `DIV`et les caractères en italique lorsque le curseur quitte la `DIV`.</span><span class="sxs-lookup"><span data-stu-id="0990f-107">For example, it would become a complex procedure for you to render the previous text in italics whenever the user positions the cursor over the `DIV`, and take italics off when the cursor leaves the `DIV`.</span></span> <span data-ttu-id="0990f-108">Un problème prendrait trop de temps si vous avez besoin manipuler un grand nombre de styles de cette manière.</span><span class="sxs-lookup"><span data-stu-id="0990f-108">Time would become an issue if you need to manipulate a large number of styles in this manner.</span></span>

<span data-ttu-id="0990f-109">La procédure suivante contient le code que vous pouvez utiliser pour manipuler facilement des styles sur les éléments et les documents HTML.</span><span class="sxs-lookup"><span data-stu-id="0990f-109">The following procedure contains code that you can use to easily manipulate styles on HTML documents and elements.</span></span> <span data-ttu-id="0990f-110">La procédure requiert que vous savez comment effectuer des tâches de base dans les formulaires Windows, telles que la création d’un projet et l’ajout d’un contrôle à un formulaire.</span><span class="sxs-lookup"><span data-stu-id="0990f-110">The procedure requires that you know how to perform basic tasks in Windows Forms, such as creating a new project and adding a control to a form.</span></span>

### <a name="to-process-style-changes-in-a-windows-forms-application"></a><span data-ttu-id="0990f-111">Pour traiter les modifications de style dans une application Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0990f-111">To process style changes in a Windows Forms application</span></span>

1. <span data-ttu-id="0990f-112">Créez un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0990f-112">Create a new Windows Forms project.</span></span>

2. <span data-ttu-id="0990f-113">Créer un nouveau fichier de classe se terminant par l’extension appropriée pour votre langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="0990f-113">Create a new class file ending in the extension appropriate for your programming language.</span></span>

3. <span data-ttu-id="0990f-114">Copie la `StyleGenerator` classe de code dans la section exemple de cette rubrique dans le fichier de classe et enregistrez le code.</span><span class="sxs-lookup"><span data-stu-id="0990f-114">Copy the `StyleGenerator` class code in the Example section of this topic into the class file, and save the code.</span></span>

4. <span data-ttu-id="0990f-115">Enregistrez le code HTML suivant dans un fichier nommé Test.htm.</span><span class="sxs-lookup"><span data-stu-id="0990f-115">Save the following HTML to a file named Test.htm.</span></span>

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

5. <span data-ttu-id="0990f-116">Ajouter un <xref:System.Windows.Forms.WebBrowser> contrôle nommé `webBrowser1` au formulaire principal de votre projet.</span><span class="sxs-lookup"><span data-stu-id="0990f-116">Add a <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1` to the main form of your project.</span></span>

6. <span data-ttu-id="0990f-117">Ajoutez le code suivant au fichier de code de votre projet.</span><span class="sxs-lookup"><span data-stu-id="0990f-117">Add the following code to your project's code file.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0990f-118">Vérifiez que le `webBrowser1_DocumentCompleted` Gestionnaire d’événements est configuré en tant qu’écouteur pour le <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> événement.</span><span class="sxs-lookup"><span data-stu-id="0990f-118">Ensure that the `webBrowser1_DocumentCompleted` event handler is configured as a listener for the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="0990f-119">Dans Visual Studio, double-cliquez sur le <xref:System.Windows.Forms.WebBrowser> contrôler ; dans un éditeur de texte, configurez l’écouteur par programme.</span><span class="sxs-lookup"><span data-stu-id="0990f-119">In Visual Studio, double-click on the <xref:System.Windows.Forms.WebBrowser> control; in a text editor, configure the listener programmatically.</span></span>

     [!code-csharp[ManagedDOMStyles#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]

7. <span data-ttu-id="0990f-120">Exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="0990f-120">Run the project.</span></span> <span data-ttu-id="0990f-121">Exécutez votre curseur sur la première `DIV` pour observer les effets du code.</span><span class="sxs-lookup"><span data-stu-id="0990f-121">Run your cursor over the first `DIV` to observe the effects of the code.</span></span>

## <a name="example"></a><span data-ttu-id="0990f-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="0990f-122">Example</span></span>

<span data-ttu-id="0990f-123">L’exemple de code suivant montre le code complet pour le `StyleGenerator` (classe), qui analyse une valeur de style existante, prend en charge l’ajout, modification et suppression de styles et retourne une nouvelle valeur de style avec les modifications demandées.</span><span class="sxs-lookup"><span data-stu-id="0990f-123">The following code example shows the full code for the `StyleGenerator` class, which parses an existing style value, supports adding, changing, and removing styles, and returns a new style value with the requested changes.</span></span>

[!code-csharp[ManagedDOMStyles#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
[!code-vb[ManagedDOMStyles#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]

## <a name="see-also"></a><span data-ttu-id="0990f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0990f-124">See also</span></span>

- <xref:System.Windows.Forms.HtmlElement>
