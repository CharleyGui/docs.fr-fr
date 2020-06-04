---
title: GetXmlNamespace, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 85422fb9e11d78e228577adc25cba746149c645a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371114"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="6a96b-102">Opérateur GetXmlNamespace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6a96b-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="6a96b-103">Obtient l' <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML spécifié.</span><span class="sxs-lookup"><span data-stu-id="6a96b-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a96b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a96b-104">Syntax</span></span>  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="6a96b-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="6a96b-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="6a96b-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="6a96b-106">Optional.</span></span> <span data-ttu-id="6a96b-107">Chaîne qui identifie le préfixe d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="6a96b-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="6a96b-108">S’il est fourni, cette chaîne doit être un identificateur XML valide.</span><span class="sxs-lookup"><span data-stu-id="6a96b-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="6a96b-109">Pour plus d’informations, consultez [noms des éléments et attributs XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6a96b-109">For more information, see [Names of Declared XML Elements and Attributes](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="6a96b-110">Si aucun préfixe n’est spécifié, l’espace de noms par défaut est retourné.</span><span class="sxs-lookup"><span data-stu-id="6a96b-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="6a96b-111">Si aucun espace de noms par défaut n’est spécifié, l’espace de noms vide est retourné.</span><span class="sxs-lookup"><span data-stu-id="6a96b-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a96b-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6a96b-112">Return Value</span></span>  
 <span data-ttu-id="6a96b-113"><xref:System.Xml.Linq.XNamespace>Objet qui correspond au préfixe d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="6a96b-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a96b-114">Notes</span><span class="sxs-lookup"><span data-stu-id="6a96b-114">Remarks</span></span>  
 <span data-ttu-id="6a96b-115">L' `GetXmlNamespace` opérateur obtient l' <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML `xmlNamespacePrefix` .</span><span class="sxs-lookup"><span data-stu-id="6a96b-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="6a96b-116">Vous pouvez utiliser des préfixes d’espaces de noms XML directement dans des littéraux XML et des propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="6a96b-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="6a96b-117">Toutefois, vous devez utiliser l' `GetXmlNamespace` opérateur pour convertir un préfixe d’espace de noms en <xref:System.Xml.Linq.XNamespace> objet avant de pouvoir l’utiliser dans votre code.</span><span class="sxs-lookup"><span data-stu-id="6a96b-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="6a96b-118">Vous pouvez ajouter un nom d’élément non qualifié à un <xref:System.Xml.Linq.XNamespace> objet pour obtenir un <xref:System.Xml.Linq.XName> objet complet, que de nombreuses [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] méthodes requièrent.</span><span class="sxs-lookup"><span data-stu-id="6a96b-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a96b-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="6a96b-119">Example</span></span>  
 <span data-ttu-id="6a96b-120">L’exemple suivant importe `ns` sous la forme d’un préfixe d’espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="6a96b-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="6a96b-121">Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder au premier nœud enfant qui a le nom qualifié `ns:phone` .</span><span class="sxs-lookup"><span data-stu-id="6a96b-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="6a96b-122">Il passe ensuite ce nœud enfant à la `ShowName` sous-routine, qui construit un nom qualifié à l’aide de l' `GetXmlNamespace` opérateur.</span><span class="sxs-lookup"><span data-stu-id="6a96b-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="6a96b-123">La `ShowName` sous-routine passe ensuite le nom qualifié à la <xref:System.Xml.Linq.XNode.Ancestors%2A> méthode pour récupérer le `ns:contact` nœud parent.</span><span class="sxs-lookup"><span data-stu-id="6a96b-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 <span data-ttu-id="6a96b-124">Quand vous appelez `TestGetXmlNamespace.RunSample()` , il affiche une boîte de message qui contient le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="6a96b-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="6a96b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a96b-125">See also</span></span>

- [<span data-ttu-id="6a96b-126">Imports, instruction (espace de noms XML)</span><span class="sxs-lookup"><span data-stu-id="6a96b-126">Imports Statement (XML Namespace)</span></span>](../statements/imports-statement-xml-namespace.md)
- [<span data-ttu-id="6a96b-127">Accès au code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6a96b-127">Accessing XML in Visual Basic</span></span>](../../programming-guide/language-features/xml/accessing-xml.md)
