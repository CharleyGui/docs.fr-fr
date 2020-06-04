---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 78a10624107cea349b01f484c641190a945dbd7e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400109"
---
# <a name="include-visual-basic"></a>\<include> (Visual Basic)
Fait référence à un autre fichier qui décrit les types et les membres dans votre code source.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Paramètres  
 `filename`  
 Obligatoire. Nom du fichier contenant la documentation. Le nom de fichier peut être qualifié avec un chemin. Mettez `filename` entre guillemets doubles ("").  
  
 `tagpath`  
 Obligatoire. Chemin des balises contenues dans `filename` qui mène à la balise `name`. Placez le chemin d’accès entre guillemets doubles ("").  
  
 `name`  
 Obligatoire. Spécificateur de nom dans la balise qui précède les commentaires. `Name`aura un `id` .  
  
 `id`  
 Obligatoire. ID de la balise qui précède les commentaires. Mettez l’ID entre guillemets simples (' ').  
  
## <a name="remarks"></a>Notes  
 Utilisez la `<include>` balise pour faire référence aux commentaires d’un autre fichier qui décrivent les types et les membres dans votre code source. Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source.  
  
 La `<include>` balise utilise la recommandation W3C XML Path Language (XPath) Version 1,0. Pour plus d’informations sur les méthodes de personnalisation de votre `<include>` utilisation, consultez <https://www.w3.org/TR/xpath> .  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la `<include>` balise pour importer des commentaires de documentation de membre à partir d’un fichier appelé `commentFile.xml` .  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 Le format de `commentFile.xml` est le suivant.  
  
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

- [Étiquettes XML pour les commentaires](index.md)
