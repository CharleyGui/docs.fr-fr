---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400071"
---
# <a name="para-visual-basic"></a>\<para> (Visual Basic)
Spécifie que le contenu est mis en forme en tant que paragraphe.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a>Paramètres  
 `content`  
 Texte du paragraphe.  
  
## <a name="remarks"></a>Notes  
 La `<para>` balise est destinée à être utilisée à l’intérieur d’une balise, telle que [\<summary>](summary.md) , [\<remarks>](remarks.md) ou [\<returns>](returns.md) , et vous permet d’ajouter une structure au texte.  
  
 Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la `<para>` balise pour fractionner la section Notes de la `UpdateRecord` méthode en deux paragraphes.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](index.md)
