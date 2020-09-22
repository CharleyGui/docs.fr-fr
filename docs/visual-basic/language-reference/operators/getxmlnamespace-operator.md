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
ms.openlocfilehash: 660474c1193076755889fd885c1b78bec78f0a2c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873474"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>Opérateur GetXmlNamespace (Visual Basic)

Obtient l' <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Éléments  

 `xmlNamespacePrefix`  
 Optionnel. Chaîne qui identifie le préfixe d’espace de noms XML. S’il est fourni, cette chaîne doit être un identificateur XML valide. Pour plus d’informations, consultez [noms des éléments et attributs XML déclarés](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Si aucun préfixe n’est spécifié, l’espace de noms par défaut est retourné. Si aucun espace de noms par défaut n’est spécifié, l’espace de noms vide est retourné.  
  
## <a name="return-value"></a>Valeur de retour  

 <xref:System.Xml.Linq.XNamespace>Objet qui correspond au préfixe d’espace de noms XML.  
  
## <a name="remarks"></a>Notes  

 L' `GetXmlNamespace` opérateur obtient l' <xref:System.Xml.Linq.XNamespace> objet qui correspond au préfixe d’espace de noms XML `xmlNamespacePrefix` .  
  
 Vous pouvez utiliser des préfixes d’espaces de noms XML directement dans des littéraux XML et des propriétés d’axe XML. Toutefois, vous devez utiliser l' `GetXmlNamespace` opérateur pour convertir un préfixe d’espace de noms en <xref:System.Xml.Linq.XNamespace> objet avant de pouvoir l’utiliser dans votre code. Vous pouvez ajouter un nom d’élément non qualifié à un <xref:System.Xml.Linq.XNamespace> objet pour obtenir un <xref:System.Xml.Linq.XName> objet complet, que de nombreuses [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] méthodes requièrent.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant importe `ns` sous la forme d’un préfixe d’espace de noms XML. Il utilise ensuite le préfixe de l’espace de noms pour créer un littéral XML et accéder au premier nœud enfant qui a le nom qualifié `ns:phone` . Il passe ensuite ce nœud enfant à la `ShowName` sous-routine, qui construit un nom qualifié à l’aide de l' `GetXmlNamespace` opérateur. La `ShowName` sous-routine passe ensuite le nom qualifié à la <xref:System.Xml.Linq.XNode.Ancestors%2A> méthode pour récupérer le `ns:contact` nœud parent.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 Quand vous appelez `TestGetXmlNamespace.RunSample()` , il affiche une boîte de message qui contient le texte suivant :  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Voir aussi

- [Imports, instruction (espace de noms XML)](../statements/imports-statement-xml-namespace.md)
- [Accès au code XML dans Visual Basic](../../programming-guide/language-features/xml/accessing-xml.md)
