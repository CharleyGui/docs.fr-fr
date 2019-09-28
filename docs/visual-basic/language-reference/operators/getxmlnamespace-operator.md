---
title: Opérateur GetXmlNamespace (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: bfccdcd9b5d35418b206dfa9fefffb5ddab69c66
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592167"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="c3716-102">Opérateur GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3716-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="c3716-103">Obtient l’objet <xref:System.Xml.Linq.XNamespace> qui correspond au préfixe d’espace de noms XML spécifié.</span><span class="sxs-lookup"><span data-stu-id="c3716-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3716-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3716-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="c3716-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c3716-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="c3716-106">facultatif.</span><span class="sxs-lookup"><span data-stu-id="c3716-106">Optional.</span></span> <span data-ttu-id="c3716-107">Chaîne qui identifie le préfixe d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="c3716-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="c3716-108">S’il est fourni, cette chaîne doit être un identificateur XML valide.</span><span class="sxs-lookup"><span data-stu-id="c3716-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="c3716-109">Pour plus d’informations, consultez [noms des éléments et attributs XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="c3716-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="c3716-110">Si aucun préfixe n’est spécifié, l’espace de noms par défaut est retourné.</span><span class="sxs-lookup"><span data-stu-id="c3716-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="c3716-111">Si aucun espace de noms par défaut n’est spécifié, l’espace de noms vide est retourné.</span><span class="sxs-lookup"><span data-stu-id="c3716-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3716-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c3716-112">Return Value</span></span>  
 <span data-ttu-id="c3716-113">Objet <xref:System.Xml.Linq.XNamespace> qui correspond au préfixe d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="c3716-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3716-114">Notes</span><span class="sxs-lookup"><span data-stu-id="c3716-114">Remarks</span></span>  
 <span data-ttu-id="c3716-115">L’opérateur `GetXmlNamespace` obtient l’objet <xref:System.Xml.Linq.XNamespace> qui correspond au préfixe d’espace de noms XML `xmlNamespacePrefix`.</span><span class="sxs-lookup"><span data-stu-id="c3716-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="c3716-116">Vous pouvez utiliser des préfixes d’espaces de noms XML directement dans des littéraux XML et des propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="c3716-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="c3716-117">Toutefois, vous devez utiliser l’opérateur `GetXmlNamespace` pour convertir un préfixe d’espace de noms en objet <xref:System.Xml.Linq.XNamespace> avant de pouvoir l’utiliser dans votre code.</span><span class="sxs-lookup"><span data-stu-id="c3716-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="c3716-118">Vous pouvez ajouter un nom d’élément non qualifié à un objet <xref:System.Xml.Linq.XNamespace> pour obtenir un objet <xref:System.Xml.Linq.XName> complet, que de nombreuses méthodes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] requièrent.</span><span class="sxs-lookup"><span data-stu-id="c3716-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3716-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="c3716-119">Example</span></span>  
 <span data-ttu-id="c3716-120">L’exemple suivant importe `ns` en tant que préfixe d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="c3716-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="c3716-121">Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder au premier nœud enfant portant le nom qualifié `ns:phone`.</span><span class="sxs-lookup"><span data-stu-id="c3716-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="c3716-122">Il passe ensuite ce nœud enfant à la sous-routine `ShowName`, qui construit un nom qualifié à l’aide de l’opérateur `GetXmlNamespace`.</span><span class="sxs-lookup"><span data-stu-id="c3716-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="c3716-123">La sous-routine `ShowName` transmet ensuite le nom qualifié à la méthode <xref:System.Xml.Linq.XNode.Ancestors%2A> pour récupérer le nœud parent `ns:contact`.</span><span class="sxs-lookup"><span data-stu-id="c3716-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="c3716-124">Lorsque vous appelez `TestGetXmlNamespace.RunSample()`, il affiche une boîte de message qui contient le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="c3716-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="c3716-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3716-125">See also</span></span>

- [<span data-ttu-id="c3716-126">Imports (instruction) (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="c3716-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="c3716-127">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c3716-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
