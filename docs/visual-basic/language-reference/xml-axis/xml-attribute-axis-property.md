---
title: Propriété d'axe d'attribut XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyAttributeAxis
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
ms.openlocfilehash: 896081c3dc7ca9e50b4dc4bd87675e957c34b649
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582160"
---
# <a name="xml-attribute-axis-property-visual-basic"></a>Propriété d'axe d'attribut XML (Visual Basic)
Fournit l’accès à la valeur d’un attribut pour un objet <xref:System.Xml.Linq.XElement> ou au premier élément d’une collection d’objets <xref:System.Xml.Linq.XElement>.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
object.@attribute  
' -or-  
object.@<attribute>  
```  
  
## <a name="parts"></a>Composants  
 `object`  
 Requis. Objet <xref:System.Xml.Linq.XElement> ou collection d’objets <xref:System.Xml.Linq.XElement>.  
  
 .@  
 Requis. Indique le début d’une propriété d’axe d’attribut.  
  
 <  
 Optionnel. Indique le début du nom de l’attribut lorsque `attribute` n’est pas un identificateur valide dans Visual Basic.  
  
 `attribute`  
 Requis. Nom de l’attribut auquel accéder, sous la forme [`prefix` :] `name`.  
  
|Élément|Description|  
|----------|-----------------|  
|`prefix`|Optionnel. Préfixe d’espace de noms XML pour l’attribut. Doit être un espace de noms XML global défini avec une instruction `Imports`.|  
|`name`|Requis. Nom de l’attribut local. Consultez [les noms des éléments et attributs XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Optionnel. Indique la fin du nom de l’attribut lorsque `attribute` n’est pas un identificateur valide dans Visual Basic.  
  
## <a name="return-value"></a>Valeur de retour  
 Chaîne qui contient la valeur de `attribute`. Si le nom de l’attribut n’existe pas, `Nothing` est retourné.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser une propriété d’axe d’attribut XML pour accéder à la valeur d’un attribut par nom à partir d’un objet <xref:System.Xml.Linq.XElement> ou à partir du premier élément d’une collection d’objets <xref:System.Xml.Linq.XElement>. Vous pouvez récupérer une valeur d’attribut par nom ou ajouter un nouvel attribut à un élément en spécifiant un nouveau nom précédé de l’identificateur @.  
  
 Quand vous faites référence à un attribut XML à l’aide de l’identificateur @, la valeur de l’attribut est retournée sous forme de chaîne et vous n’avez pas besoin de spécifier explicitement la propriété <xref:System.Xml.Linq.XAttribute.Value%2A>.  
  
 Les règles d’affectation de noms pour les attributs XML diffèrent des règles d’affectation de noms pour les identificateurs de Visual Basic. Pour accéder à un attribut XML dont le nom n’est pas un identificateur de Visual Basic valide, mettez le nom entre crochets pointus (\< et >).  
  
## <a name="xml-namespaces"></a>Espaces de noms XML  
 Le nom d’une propriété d’axe d’attribut ne peut utiliser que des préfixes d’espaces de noms XML déclarés globalement à l’aide de l’instruction `Imports`. Il ne peut pas utiliser des préfixes d'espace de noms XML déclarés localement dans des littéraux d'éléments XML. Pour plus d’informations, consultez [instructions Imports (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment obtenir les valeurs des attributs XML nommés `type` à partir d’une collection d’éléments XML nommés `phone`.  
  
 [!code-vb[VbXMLSamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#12)]  
  
 Ce code affiche le texte suivant :  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment créer des attributs pour un élément XML de manière déclarative, dans le cadre du XML, et de manière dynamique en ajoutant un attribut à une instance d’un objet <xref:System.Xml.Linq.XElement>. L’attribut `type` est créé de manière déclarative et l’attribut `owner` est créé dynamiquement.  
  
 [!code-vb[VbXMLSamples#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#44)]  
  
 Ce code affiche le texte suivant :  
  
```xml  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la syntaxe du Chevron pour obtenir la valeur de l’attribut XML nommé `number-type`, qui n’est pas un identificateur valide dans Visual Basic.  
  
 [!code-vb[VbXMLSamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples5.vb#13)]  
  
 Ce code affiche le texte suivant :  
  
 `Phone type: work`  
  
## <a name="example"></a>Exemple  
 L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML. Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié « `ns:name` ».  
  
 [!code-vb[VbXMLSamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples6.vb#14)]  
  
 Ce code affiche le texte suivant :  
  
 `Phone type: home`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement>
- [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Création de code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
