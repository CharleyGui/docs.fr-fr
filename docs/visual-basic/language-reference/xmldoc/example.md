---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f36ac1337dd0d1400180fbd3deae2bb24ad9c58
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348482"
---
# <a name="example-visual-basic"></a>> exemple de \<(Visual Basic)
Spécifie un exemple pour le membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>Paramètres  
 `description`  
 Description de l’exemple de code.  
  
## <a name="remarks"></a>Notes  
 La balise `<example>` vous permet de spécifier un exemple d’utilisation d’une méthode ou d’un autre membre de bibliothèque. Cela implique généralement l’utilisation de la balise [\<code>](../../../visual-basic/language-reference/xmldoc/code.md).  
  
 Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la balise `<example>` pour inclure un exemple d’utilisation du champ `ID`.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
