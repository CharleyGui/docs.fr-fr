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
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353190"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>Opérateur GetXmlNamespace (Visual Basic)
Obtient l’objet <xref:System.Xml.Linq.XNamespace> qui correspond au préfixe d’espace de noms XML spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Composants  
 `xmlNamespacePrefix`  
 Ce paramètre est facultatif. Chaîne qui identifie le préfixe d’espace de noms XML. S’il est fourni, cette chaîne doit être un identificateur XML valide. Pour plus d’informations, consultez [noms des éléments et attributs XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Si aucun préfixe n’est spécifié, l’espace de noms par défaut est retourné. Si aucun espace de noms par défaut n’est spécifié, l’espace de noms vide est retourné.  
  
## <a name="return-value"></a>Valeur de retour  
 Objet <xref:System.Xml.Linq.XNamespace> qui correspond au préfixe d’espace de noms XML.  
  
## <a name="remarks"></a>Notes  
 L’opérateur `GetXmlNamespace` obtient l’objet <xref:System.Xml.Linq.XNamespace> qui correspond au préfixe d’espace de noms XML `xmlNamespacePrefix`.  
  
 Vous pouvez utiliser des préfixes d’espaces de noms XML directement dans des littéraux XML et des propriétés d’axe XML. Toutefois, vous devez utiliser l’opérateur `GetXmlNamespace` pour convertir un préfixe d’espace de noms en objet <xref:System.Xml.Linq.XNamespace> avant de pouvoir l’utiliser dans votre code. Vous pouvez ajouter un nom d’élément non qualifié à un objet <xref:System.Xml.Linq.XNamespace> pour obtenir un objet <xref:System.Xml.Linq.XName> complet, qui est requis par de nombreuses [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] méthodes.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant importe `ns` sous la forme d’un préfixe d’espace de noms XML. Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder au premier nœud enfant portant le nom qualifié `ns:phone`. Il passe ensuite ce nœud enfant à la sous-routine `ShowName`, qui construit un nom qualifié à l’aide de l’opérateur `GetXmlNamespace`. La sous-routine `ShowName` transmet ensuite le nom qualifié à la méthode <xref:System.Xml.Linq.XNode.Ancestors%2A> pour récupérer le nœud `ns:contact` parent.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Lorsque vous appelez `TestGetXmlNamespace.RunSample()`, il affiche une boîte de message qui contient le texte suivant :  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Voir aussi

- [Imports (instruction) (espace de noms XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Accès au code XML dans Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
