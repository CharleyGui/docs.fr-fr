---
title: Code source L2DBForm.xaml.cs
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 882699a76eab3c291cd92c298287bc5d28fb08e1
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920859"
---
# <a name="l2dbformxamlcs-source-code"></a><span data-ttu-id="dce11-102">Code source L2DBForm.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="dce11-102">L2DBForm.xaml.cs source code</span></span>

<span data-ttu-id="dce11-103">Cette page contient le contenu et la description du C# code source dans le fichier *L2DBForm.Xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="dce11-103">This page contains the contents and description of the C# source code in the file *L2DBForm.xaml.cs*.</span></span> <span data-ttu-id="dce11-104">La classe partielle L2XDBForm contenue dans ce fichier peut être divisée en trois sections logiques : les membres de données et les gestionnaires d'événements de clic sur le bouton `OnRemove` et `OnAddBook`.</span><span class="sxs-lookup"><span data-stu-id="dce11-104">The L2XDBForm partial class contained in this file can be divided into three logical sections: data members and the `OnRemove` and `OnAddBook` button click event handlers.</span></span>

## <a name="data-members"></a><span data-ttu-id="dce11-105">Membres de données</span><span class="sxs-lookup"><span data-stu-id="dce11-105">Data members</span></span>

<span data-ttu-id="dce11-106">Deux membres de données privés sont utilisés pour associer cette classe aux ressources de fenêtre utilisées dans *L2DBForm.xaml*.</span><span class="sxs-lookup"><span data-stu-id="dce11-106">Two private data members are used to associate this class to the window resources used in *L2DBForm.xaml*.</span></span>

- <span data-ttu-id="dce11-107">La variable d'espace de noms `myBooks` est initialisée à `"http://www.mybooks.com"`.</span><span class="sxs-lookup"><span data-stu-id="dce11-107">The namespace variable `myBooks` is initialized to `"http://www.mybooks.com"`.</span></span>

- <span data-ttu-id="dce11-108">Le membre `bookList` est initialisé dans le constructeur à la chaîne CDATA dans *L2DBForm.xaml* avec la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="dce11-108">The member `bookList` is initialized in the constructor to the CDATA string in *L2DBForm.xaml* with the following line:</span></span>

    ```csharp
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a><span data-ttu-id="dce11-109">Gestionnaire d’événements OnAddBook</span><span class="sxs-lookup"><span data-stu-id="dce11-109">OnAddBook event handler</span></span>

<span data-ttu-id="dce11-110">Cette méthode contient les trois instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="dce11-110">This method contains the following three statements:</span></span>

- <span data-ttu-id="dce11-111">La première instruction conditionnelle est utilisée pour la validation d’entrée.</span><span class="sxs-lookup"><span data-stu-id="dce11-111">The first conditional statement is used for input validation.</span></span>

- <span data-ttu-id="dce11-112">La deuxième instruction crée un nouveau <xref:System.Xml.Linq.XElement> à partir des valeurs de chaîne que l’utilisateur a entrées dans la section d’interface utilisateur **Add New Book**.</span><span class="sxs-lookup"><span data-stu-id="dce11-112">The second statement creates a new <xref:System.Xml.Linq.XElement> from the string values the user entered in the **Add New Book** user interface (UI) section.</span></span>

- <span data-ttu-id="dce11-113">La dernière instruction ajoute ce nouvel élément au fournisseur de données dans *L2DBForm.xaml*.</span><span class="sxs-lookup"><span data-stu-id="dce11-113">The last statement adds this new book element to the data provider in *L2DBForm.xaml*.</span></span> <span data-ttu-id="dce11-114">En conséquence, la liaison de données dynamiques mettra automatiquement à jour l'interface utilisateur avec ce nouvel élément ; aucun code supplémentaire fourni par l'utilisateur n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="dce11-114">Consequently, dynamic data binding will automatically update the UI with this new item; no extra user-supplied code is required.</span></span>

## <a name="onremove-event-handler"></a><span data-ttu-id="dce11-115">Gestionnaire d’événements OnRemove</span><span class="sxs-lookup"><span data-stu-id="dce11-115">OnRemove event handler</span></span>

<span data-ttu-id="dce11-116">Le gestionnaire `OnRemove` est plus complexe que le gestionnaire `OnAddBook` pour deux raisons.</span><span class="sxs-lookup"><span data-stu-id="dce11-116">The `OnRemove` handler is more complicated than the `OnAddBook` handler for two reasons.</span></span> <span data-ttu-id="dce11-117">Tout d'abord, le code XML brut contenant des espaces conservés, les nouvelles lignes correspondantes doivent également être supprimées avec l'entrée de livre.</span><span class="sxs-lookup"><span data-stu-id="dce11-117">First, because the raw XML contains preserved white space, matching newlines must also be removed with the book entry.</span></span> <span data-ttu-id="dce11-118">Ensuite, pour plus de commodité, la sélection (qui était sur l'élément supprimé) est réinitialisée à l'élément précédent dans la liste.</span><span class="sxs-lookup"><span data-stu-id="dce11-118">Second, as a convenience, the selection, which was on the deleted item, is reset to the previous one in the list.</span></span>

<span data-ttu-id="dce11-119">Toutefois, le travail principal lié à la suppression de l’élément de livre sélectionné est effectué par deux instructions uniquement :</span><span class="sxs-lookup"><span data-stu-id="dce11-119">However, the core work of removing the selected book item is accomplished by only two statements:</span></span>

- <span data-ttu-id="dce11-120">Tout d'abord, l'élément de livre associé à l'élément actuellement sélectionné dans la zone de liste est récupéré :</span><span class="sxs-lookup"><span data-stu-id="dce11-120">First, the book element associated with the currently selected item in the list box is retrieved:</span></span>

    ```csharp
    XElement selBook = (XElement)lbBooks.SelectedItem;
    ```

- <span data-ttu-id="dce11-121">Ensuite, cet élément est supprimé du fournisseur de données :</span><span class="sxs-lookup"><span data-stu-id="dce11-121">Then, this element is deleted from the data provider:</span></span>

    ```csharp
    selBook.Remove();
    ```

<span data-ttu-id="dce11-122">Là encore, la liaison de données dynamiques s'assure que l'interface utilisateur du programme est mise à jour automatiquement.</span><span class="sxs-lookup"><span data-stu-id="dce11-122">Again, dynamic data binding assures that the program's UI is automatically updated.</span></span>

## <a name="example"></a><span data-ttu-id="dce11-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="dce11-123">Example</span></span>

### <a name="code"></a><span data-ttu-id="dce11-124">Code</span><span class="sxs-lookup"><span data-stu-id="dce11-124">Code</span></span>

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}
```

### <a name="comments"></a><span data-ttu-id="dce11-125">Comments</span><span class="sxs-lookup"><span data-stu-id="dce11-125">Comments</span></span>

<span data-ttu-id="dce11-126">Pour obtenir la source XAML associée pour ces gestionnaires, consultez [Code source de L2DBForm.xaml](l2dbform-xaml-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="dce11-126">For the associated XAML source for these handlers, see [L2DBForm.xaml source code](l2dbform-xaml-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dce11-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dce11-127">See also</span></span>

- [<span data-ttu-id="dce11-128">Procédure pas à pas : exemple LinqToXmlDataBinding</span><span class="sxs-lookup"><span data-stu-id="dce11-128">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="dce11-129">Code source L2DBForm.xaml</span><span class="sxs-lookup"><span data-stu-id="dce11-129">L2DBForm.xaml source code</span></span>](l2dbform-xaml-source-code.md)
