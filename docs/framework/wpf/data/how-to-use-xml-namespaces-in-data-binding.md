---
title: 'Comment : utiliser des espaces de noms XML dans la liaison de données'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740572"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a><span data-ttu-id="e6fb4-102">Comment : utiliser des espaces de noms XML dans la liaison de données</span><span class="sxs-lookup"><span data-stu-id="e6fb4-102">How to: Use XML Namespaces in Data Binding</span></span>
## <a name="example"></a><span data-ttu-id="e6fb4-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="e6fb4-103">Example</span></span>
 <span data-ttu-id="e6fb4-104">Cet exemple montre comment gérer les espaces de noms spécifiés dans votre source de liaison XML.</span><span class="sxs-lookup"><span data-stu-id="e6fb4-104">This example shows how to handle namespaces specified in your XML binding source.</span></span>

 <span data-ttu-id="e6fb4-105">Si vos données XML comportent la définition d’espace de noms XML suivante :</span><span class="sxs-lookup"><span data-stu-id="e6fb4-105">If your XML data has the following XML namespace definition:</span></span>

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 <span data-ttu-id="e6fb4-106">Vous pouvez utiliser l’élément <xref:System.Windows.Data.XmlNamespaceMapping> pour mapper l’espace de noms à un <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e6fb4-106">You can use the <xref:System.Windows.Data.XmlNamespaceMapping> element to map the namespace to a <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, as in the following example.</span></span> <span data-ttu-id="e6fb4-107">Vous pouvez ensuite utiliser la <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> pour faire référence à l’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="e6fb4-107">You can then use the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> to refer to the XML namespace.</span></span> <span data-ttu-id="e6fb4-108">L' <xref:System.Windows.Controls.ListBox> dans cet exemple affiche le *titre* et le *DC : date* de chaque *élément*.</span><span class="sxs-lookup"><span data-stu-id="e6fb4-108">The <xref:System.Windows.Controls.ListBox> in this example displays the *title* and *dc:date* of each *item*.</span></span>

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 <span data-ttu-id="e6fb4-109">Notez que le <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> que vous spécifiez ne doit pas nécessairement correspondre à celui utilisé dans la source XML. Si le préfixe change dans la source XML, votre mappage fonctionne toujours.</span><span class="sxs-lookup"><span data-stu-id="e6fb4-109">Note that the <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> you specify does not have to match the one used in the XML source; if the prefix changes in the XML source your mapping still works.</span></span>

 <span data-ttu-id="e6fb4-110">Dans cet exemple particulier, les données XML proviennent d’un service Web, mais l’élément <xref:System.Windows.Data.XmlNamespaceMapping> fonctionne également avec des données XML ou XML inline dans un fichier incorporé.</span><span class="sxs-lookup"><span data-stu-id="e6fb4-110">In this particular example, the XML data comes from a web service, but the <xref:System.Windows.Data.XmlNamespaceMapping> element also works with inline XML or XML data in an embedded file.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6fb4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6fb4-111">See also</span></span>

- [<span data-ttu-id="e6fb4-112">Effectuer une liaison à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath</span><span class="sxs-lookup"><span data-stu-id="e6fb4-112">Bind to XML Data Using an XMLDataProvider and XPath Queries</span></span>](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [<span data-ttu-id="e6fb4-113">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="e6fb4-113">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="e6fb4-114">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="e6fb4-114">How-to Topics</span></span>](data-binding-how-to-topics.md)
