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
# <a name="include-visual-basic"></a>\<inclure des > (Visual Basic)
Fait référence à un autre fichier qui décrit les types et les membres dans votre code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Paramètres  
 `filename`  
 Requis. Nom du fichier contenant la documentation. Le nom de fichier peut être qualifié avec un chemin. Placez `filename` entre guillemets doubles ("").  
  
 `tagpath`  
 Requis. Chemin des balises contenues dans `filename` qui mène à la balise `name`. Placez le chemin d’accès entre guillemets doubles ("").  
  
 `name`  
 Requis. Spécificateur de nom dans la balise qui précède les commentaires. `Name` aura une `id`.  
  
 `id`  
 Requis. ID de la balise qui précède les commentaires. Mettez l’ID entre guillemets simples (' ').  
  
## <a name="remarks"></a>Notes  
 Utilisez la balise `<include>` pour faire référence aux commentaires d’un autre fichier qui décrivent les types et les membres de votre code source. Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source.  
  
 La balise `<include>` utilise la recommandation du W3C sur XML Path Language (XPath) version 1,0. Pour plus d’informations sur les façons de personnaliser votre `<include>` utiliser, consultez <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la balise `<include>` pour importer des commentaires de documentation de membre à partir d’un fichier appelé `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 Le format du `commentFile.xml` est le suivant.  
  
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
