---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: d058663213cf02f2142bff740aeec1b60791362c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873025"
---
# <a name="code-visual-basic"></a>\<code> (Visual Basic)

Indique que le texte est plusieurs lignes de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<code>content</code>  
```  
  
## <a name="parameters"></a>Paramètres  

 `content`  
 Texte à marquer comme code.  
  
## <a name="remarks"></a>Notes  

 Utilisez la `<code>` balise pour indiquer que plusieurs lignes sont du code. Utilisez [\<c>](c.md) pour indiquer que le texte d’une description doit être marqué comme étant du code.  
  
 Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise la \<code> balise pour inclure un exemple de code pour l’utilisation du `ID` champ.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](index.md)
