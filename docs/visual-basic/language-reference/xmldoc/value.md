---
title: <value>
ms.date: 07/20/2015
helpviewer_keywords:
- <value> XML tag
- value XML tag
ms.assetid: 0b84b02e-9e6d-41b5-a926-0d5dc76dacb5
ms.openlocfilehash: 550f8b63928f80878ba316bfaf09077e14091305
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875175"
---
# <a name="value-visual-basic"></a>\<value> (Visual Basic)

Spécifie la description d’une propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<value>property-description</value>  
```  
  
## <a name="parameters"></a>Paramètres  

 `property-description`  
 Description de la propriété.  
  
## <a name="remarks"></a>Notes  

 Utilisez la `<value>` balise pour décrire une propriété. Notez que lorsque vous ajoutez une propriété à l’aide de l’Assistant code dans l’environnement de développement Visual Studio, elle ajoute une [\<summary>](summary.md) balise pour la nouvelle propriété. Vous devez ensuite ajouter manuellement une `<value>` balise pour décrire la valeur représentée par la propriété.  
  
 Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise la `<value>` balise pour décrire la valeur que la `Counter` propriété contient.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](index.md)
