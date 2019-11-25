---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 2f2bebfd06d4614f05cb66834cc5bef40524ce3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348462"
---
# <a name="include-visual-basic"></a>\<include> (Visual Basic)
Refers to another file that describes the types and members in your source code.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Paramètres  
 `filename`  
 Requis. Nom du fichier contenant la documentation. Le nom de fichier peut être qualifié avec un chemin. Enclose `filename` in double quotation marks (" ").  
  
 `tagpath`  
 Requis. Chemin des balises contenues dans `filename` qui mène à la balise `name`. Enclose the path in double quotation marks (" ").  
  
 `name`  
 Requis. The name specifier in the tag that precedes the comments. `Name` will have an `id`.  
  
 `id`  
 Requis. ID de la balise qui précède les commentaires. Enclose the ID in single quotation marks (' ').  
  
## <a name="remarks"></a>Notes  
 Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code. Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source.  
  
 The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation. For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Exemple  
 This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 The format of the `commentFile.xml` is as follows.  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
