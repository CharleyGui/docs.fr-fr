---
title: <include> - Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 125ab9476507babae9a707a6c42d24adda632267
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696556"
---
# <a name="include-c-programming-guide"></a>\<include> (Guide de programmation C#)
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
## <a name="parameters"></a>Parameters  
 `filename`  
 Nom du fichier XML contenant la documentation. Le nom de fichier peut être qualifié avec un chemin relatif au fichier de code source. Mettez `filename` entre guillemets simples (' ').  
  
 `tagpath`  
 Chemin des balises contenues dans `filename` qui mène à la balise `name`. Mettez le chemin entre guillemets simples (' ').  
  
 `name`  
 Spécificateur de nom contenu dans la balise qui précède les commentaires ; `name` possède un `id`.  
  
 `id`  
 ID de la balise qui précède les commentaires. Mettez l’ID entre guillemets doubles (" ").  
  
## <a name="remarks"></a>Notes  
 La balise \<include> vous permet de faire référence à des commentaires dans un autre fichier qui décrivent les types et les membres dans votre code source. Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source. En plaçant la documentation dans un fichier distinct, vous pouvez appliquer un contrôle de code source à la documentation indépendamment du code source. Ainsi, une personne peut extraire le fichier de code source et une autre personne peut extraire le fichier de documentation.  
  
 La balise \<include> utilise la syntaxe XML XPath. Reportez-vous à la documentation de XPath pour savoir comment personnaliser votre utilisation de \<include>.  
  
## <a name="example"></a>Exemple  
 Cet exemple comprend plusieurs fichiers. Le premier, qui utilise \<include>, est présenté ci-dessous :  
  
 [!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]  
  
 Le deuxième, xml_include_tag.doc, contient les commentaires de la documentation suivants :  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a>Sortie du programme  
 La sortie suivante est générée quand vous compilez les classes Test et Test2 avec la ligne de commande suivante : `/doc:DocFileName.xml.` Dans Visual Studio, l’option de commentaires de document XML est spécifiée dans le volet de génération du Concepteur de projet. Dès que le compilateur C# trouve la balise \<include>, il recherche des commentaires de la documentation dans xml_include_tag.doc et non dans le fichier source actuel. Le compilateur génère ensuite DocFileName.xml, c’est-à-dire le fichier dont se servent les outils de documentation tels que [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) pour produire la documentation finale.  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
