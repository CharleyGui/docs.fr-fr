---
title: <value> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 516ff6ba534478d066b8ca06baee46bdd4b35265
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524605"
---
# <a name="value-visual-basic"></a>> \<value (Visual Basic)
Spécifie la description d’une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Paramètres  
 `property-description`  
 Description de la propriété.  
  
## <a name="remarks"></a>Notes  
 Utilisez la balise `<value>` pour décrire une propriété. Notez que lorsque vous ajoutez une propriété à l’aide de l’Assistant code dans l’environnement de développement Visual Studio, elle ajoute une balise [\<summary >](../../../visual-basic/language-reference/xmldoc/summary.md) pour la nouvelle propriété. Vous devez ensuite ajouter manuellement une balise `<value>` pour décrire la valeur représentée par la propriété.  
  
 Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la balise `<value>` pour décrire la valeur que la propriété `Counter` contient.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
