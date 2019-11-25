---
title: XML Child Axis Property
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 968154908bc6cb62bb221d42a1f71b329aa7096f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349454"
---
# <a name="xml-child-axis-property-visual-basic"></a>Propriété d'axe enfant XML (Visual Basic)
Fournit un accès aux enfants de l'un des éléments suivants : un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d'objets <xref:System.Xml.Linq.XElement> ou une collection d'objets <xref:System.Xml.Linq.XDocument>.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`object`|Requis. Un objet <xref:System.Xml.Linq.XElement>, un objet <xref:System.Xml.Linq.XDocument>, une collection d’objets <xref:System.Xml.Linq.XElement> ou une collection d’objets <xref:System.Xml.Linq.XDocument>.|  
|.<|Requis. Indique le début d'une propriété d'axe enfant.|  
|`child`|Requis. Name of the child nodes to access, of the form [`prefix:]name`.<br /><br /> -   `Prefix` - Optional. Préfixe d'espace de noms XML pour le nœud enfant. Doit être un espace de noms XML global défini avec une instruction `Imports`.<br />-   `Name` - Required. Nom de nœud enfant local. See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Requis. Indique la fin d'une propriété d'axe enfant.|  
  
## <a name="return-value"></a>Valeur de retour  
 Collection d'objets <xref:System.Xml.Linq.XElement>.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser une propriété d'axe enfant XML pour accéder aux nœuds enfants par nom, à partir d'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>, ou à partir d'une collection d'objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>. Utilisez la propriété XML `Value` pour accéder à la valeur du premier nœud enfant dans la collection retournée. For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 The Visual Basic compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Le nom inclus dans une propriété d'axe enfant peut utiliser uniquement des préfixes d'espace de noms XML déclarés globalement à l'aide de l'instruction `Imports`. Il ne peut pas utiliser des préfixes d'espace de noms XML déclarés localement dans des littéraux d'éléments XML. For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment accéder aux nœuds enfants nommés `phone` à partir de l'objet `contact`.  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 Ce code affiche le texte suivant :  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment accéder aux nœuds enfants nommés `phone` à partir de la collection retournée par la propriété d’axe enfant `contact` de l’objet `contacts`.  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 Ce code affiche le texte suivant :  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Exemple  
 L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML. Il utilise ensuite le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 Ce code affiche le texte suivant :  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
