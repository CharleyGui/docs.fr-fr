---
title: Propriété d’indexeur d’extension (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: 660cebadc78d260350f2849f7f4926f9cef7c8d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582169"
---
# <a name="extension-indexer-property-visual-basic"></a>Propriété d’indexeur d’extension (Visual Basic)
Fournit un accès aux différents éléments d'une collection.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`object`|Requis. Collection interrogeable. Autrement dit, une collection qui implémente <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.|  
|(|Requis. Indique le début de la propriété de l’indexeur.|  
|`index`|Requis. Expression entière qui spécifie la position de base zéro d’un élément de la collection.|  
|)|Requis. Indique la fin de la propriété de l’indexeur.|  
  
## <a name="return-value"></a>Valeur de retour  
 Objet à partir de l’emplacement spécifié dans la collection, ou `Nothing` si l’index est hors limites.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la propriété d’indexeur d’extension pour accéder à des éléments individuels dans une collection. Cette propriété d’indexeur est généralement utilisée sur la sortie des propriétés d’axe XML. Les propriétés de l’axe de descendant XML et de l’enfant XML retournent des collections d’objets <xref:System.Xml.Linq.XElement> ou une valeur d’attribut.  
  
 Le compilateur Visual Basic convertit les propriétés d’indexeur d’extension en appels à la méthode `ElementAtOrDefault`. Contrairement à un indexeur de tableau, la méthode `ElementAtOrDefault` retourne `Nothing` si l’index est hors limites. Ce comportement est utile lorsque vous ne pouvez pas déterminer facilement le nombre d’éléments d’une collection.  
  
 Cette propriété d’indexeur est semblable à une propriété d’extension pour les collections qui implémentent <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601> : elle est utilisée uniquement si la collection n’a pas d’indexeur ou de propriété par défaut.  
  
 Pour accéder à la valeur du premier élément d’une collection d’objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous pouvez utiliser la propriété XML `Value`. Pour plus d’informations, consultez [propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser l’indexeur d’extension pour accéder au deuxième nœud enfant d’une collection d’objets <xref:System.Xml.Linq.XElement>. La collection est accessible à l’aide de la propriété d’axe enfant, qui obtient tous les éléments enfants nommés `phone` dans l’objet `contact`.  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 Ce code affiche le texte suivant :  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
