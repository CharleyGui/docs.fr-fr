---
title: <returns>
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: 37b110cc6e12f11196d2a1c5cc6026d87b453626
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866416"
---
# <a name="returns-visual-basic"></a>\<returns> (Visual Basic)

Spécifie la valeur de retour de la propriété ou de la fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<returns>description</returns>  
```  
  
## <a name="parameters"></a>Paramètres  

 `description`  
 Description de la valeur de retour.  
  
## <a name="remarks"></a>Notes  

 Utilisez la `<returns>` balise dans le commentaire pour une déclaration de méthode afin de décrire la valeur de retour.  
  
 Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise la `<returns>` balise pour expliquer ce que la `DoesRecordExist` fonction retourne.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Étiquettes XML pour les commentaires](index.md)
