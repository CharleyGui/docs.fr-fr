---
title: Types de méthodes de manipulation de chaînes
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a02278abfb71efb2f31f239a89a22ad1c8ee7a18
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346271"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Types de méthodes de manipulation de chaînes en Visual Basic
Il existe différentes façons d’analyser et de manipuler vos chaînes. Certaines méthodes font partie du langage de Visual Basic, tandis que d’autres sont inhérentes à la classe `String`.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic langage et le .NET Framework  
 Les méthodes de Visual Basic sont utilisées comme fonctions inhérentes du langage. Elles peuvent être utilisées sans qualification dans votre code. L’exemple suivant illustre l’utilisation classique d’une commande de manipulation de chaînes Visual Basic :  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 Dans cet exemple, la fonction `Mid` effectue une opération directe sur `aString` et affecte la valeur à `bString`.  
  
 Pour obtenir la liste des Visual Basic méthodes de manipulation de chaînes, consultez Résumé de la [manipulation de chaînes](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Méthodes partagées et méthodes d’instance  
 Vous pouvez également manipuler des chaînes avec les méthodes de la classe `String`. Il existe deux types de méthodes dans `String`: les méthodes *partagées* et les méthodes d' *instance* .  
  
#### <a name="shared-methods"></a>Méthodes partagées  
 Une méthode partagée est une méthode qui provient de la classe `String` elle-même et qui ne requiert pas l’utilisation d’une instance de cette classe. Ces méthodes peuvent être qualifiées avec le nom de la classe (`String`) plutôt qu’avec une instance de la classe `String`. Exemple :  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 Dans l’exemple précédent, la méthode <xref:System.String.Copy%2A?displayProperty=nameWithType> est une méthode statique qui agit sur une expression à laquelle elle est donnée et assigne la valeur résultante à `bString`.  
  
#### <a name="instance-methods"></a>Méthodes d’instance  
 En revanche, les méthodes d’instance proviennent d’une instance particulière de `String` et doivent être qualifiées avec le nom de l’instance. Exemple :  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 Dans cet exemple, la méthode <xref:System.String.Substring%2A?displayProperty=nameWithType> est une méthode de l’instance de `String` (autrement dit, `aString`). Il effectue une opération sur `aString` et assigne cette valeur à `bString`.  
  
 Pour plus d’informations, consultez la documentation de la classe <xref:System.String>.  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
