---
title: <returns> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: b220c2a9aa544413c3692485f6c1eb2b64e54389
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524683"
---
# <a name="returns-visual-basic"></a>> \<returns (Visual Basic)
Spécifie la valeur de retour de la propriété ou de la fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>Paramètres  
 `description`  
 Description de la valeur de retour.  
  
## <a name="remarks"></a>Notes  
 Utilisez la balise `<returns>` dans le commentaire pour une déclaration de méthode afin de décrire la valeur de retour.  
  
 Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la balise `<returns>` pour expliquer ce que la fonction `DoesRecordExist` retourne.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
