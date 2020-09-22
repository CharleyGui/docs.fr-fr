---
title: <example>
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 6e9f63e4d31df7790f51ae4d166b606f2c63f14b
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872972"
---
# <a name="example-visual-basic"></a>\<example> (Visual Basic)

Spécifie un exemple pour le membre.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>Paramètres  

 `description`  
 Description de l’exemple de code.  
  
## <a name="remarks"></a>Notes  

 La `<example>` balise vous permet de spécifier un exemple d’utilisation d’une méthode ou d’un autre membre de bibliothèque. Cela implique généralement l’utilisation de la [\<code>](code.md) balise.  
  
 Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise la `<example>` balise pour inclure un exemple d’utilisation du `ID` champ.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](index.md)
