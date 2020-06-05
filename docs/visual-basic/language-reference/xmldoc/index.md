---
title: Balises XML recommandées pour les commentaires de documentation
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: af57fc7d55c5cfda24a2fd9406b17dedee898760
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400097"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>Balises XML recommandées pour les commentaires de documentation (Visual Basic)
Le compilateur Visual Basic peut traiter les commentaires de documentation dans votre code dans un fichier XML. Vous pouvez utiliser des outils supplémentaires pour traiter le fichier XML dans la documentation.  
  
 Les commentaires XML sont autorisés sur les constructions de code telles que les types et les membres de type. Pour les types partiels, une seule partie du type peut avoir des commentaires XML, bien qu’il n’existe aucune restriction sur les commentaires de ses membres.  
  
> [!NOTE]
> Les commentaires de documentation ne peuvent pas être appliqués aux espaces de noms. La raison en est qu’un espace de noms peut couvrir plusieurs assemblys, et que tous les assemblys ne doivent pas être chargés en même temps.  
  
 Le compilateur traite toute balise qui est du code XML valide. Les balises suivantes fournissent des fonctionnalités couramment utilisées dans la documentation utilisateur.  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|[\<exception>](exception.md)<sup>1</sup>|[\<include>](include.md)<sup>1</sup>|[\<list>](list.md)|  
|[\<para>](para.md)|[\<param>](param.md)<sup>1</sup>|[\<paramref>](paramref.md)|  
|[\<permission>](permission.md)<sup>1</sup>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|[\<see>](see.md)<sup>1</sup>|[\<seealso>](seealso.md)<sup>1</sup>|[\<summary>](summary.md)|  
|[\<typeparam>](typeparam.md)<sup>1</sup>|[\<value>](value.md)||  
  
 (<sup>1</sup> le compilateur vérifie la syntaxe.)  
  
> [!NOTE]
> Si vous souhaitez que les chevrons apparaissent dans le texte d’un commentaire de documentation, utilisez `&lt;` et `&gt;` . Par exemple, la chaîne `"&lt;text in angle brackets&gt;"` s’affiche comme `<text in angle brackets>` .  
  
## <a name="see-also"></a>Voir aussi

- [Documentation de votre code avec le langage XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../reference/command-line-compiler/doc.md)
- [Guide pratique : créer une documentation XML](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
