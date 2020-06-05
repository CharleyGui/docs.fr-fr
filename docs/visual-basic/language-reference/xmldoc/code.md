---
title: <code>
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: aa65fed863718f1f00b510f82051a13e764e1b23
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400140"
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
