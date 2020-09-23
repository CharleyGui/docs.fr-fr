---
title: Promotion de type
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: 6c28ca22e96616ff09e147400bfdb2adb922ff0e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085800"
---
# <a name="type-promotion-visual-basic"></a>Promotion de type (Visual Basic)

Quand vous déclarez un élément de programmation dans un module, Visual Basic promeut son étendue vers l’espace de noms contenant le module. C’est ce que l’on appelle la *promotion de type*.  
  
 L’exemple suivant montre une définition squelette d’un module et de deux membres de ce module.  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 Dans `projModule` , les éléments de programmation déclarés au niveau du module sont promus en `projNamespace` . Dans l’exemple précédent, `basicEnum` et `innerClass` sont promus, mais `numberSub` n’est pas, car il n’est pas déclaré au niveau du module.  
  
## <a name="effect-of-type-promotion"></a>Effet de la promotion de type  

 L’effet de la promotion de type est qu’une chaîne de qualification n’a pas besoin d’inclure le nom du module. L’exemple suivant effectue deux appels à la procédure dans l’exemple précédent.  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 Dans l’exemple précédent, le premier appel utilise des chaînes de qualification complètes. Toutefois, cela n’est pas nécessaire en raison de la promotion de type. Le deuxième appel accède également aux membres du module sans inclure `projModule` dans les chaînes de qualification.  
  
## <a name="defeat-of-type-promotion"></a>Invalidation de la promotion de type  

 Si l’espace de noms a déjà un membre portant le même nom qu’un membre de module, la promotion de type est invalidée pour ce membre de module. L’exemple suivant montre une définition squelette d’une énumération et d’un module au sein du même espace de noms.  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 Dans l’exemple précédent, Visual Basic ne peut pas `abc` promouvoir `thisNameSpace` la classe vers, car il existe déjà une énumération portant le même nom au niveau de l’espace de noms. Pour accéder à `abcSub` , vous devez utiliser la chaîne de qualification complète `thisNamespace.thisModule.abc.abcSub` . Toutefois, `xyz` la classe est toujours promue et vous pouvez y accéder `xyzSub` avec la chaîne de qualification plus petite `thisNamespace.xyz.xyzSub` .  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>Non-manipulation de la promotion de type pour les types partiels  

 Si une classe ou une structure à l’intérieur d’un module utilise le mot clé [Partial](../../../language-reference/modifiers/partial.md) , la promotion de type est automatiquement invalidée pour cette classe ou structure, que l’espace de noms ait ou non un membre avec le même nom. D’autres éléments du module sont toujours éligibles pour la promotion de type.  
  
 **Incidences.** L’invalidation de la promotion de type d’une définition partielle peut provoquer des résultats inattendus et même des erreurs du compilateur. L’exemple suivant illustre le squelette des définitions partielles d’une classe, dont l’une est à l’intérieur d’un module.  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 Dans l’exemple précédent, le développeur peut s’attendre à ce que le compilateur fusionne les deux définitions partielles de `sampleClass` . Toutefois, le compilateur ne tient pas compte de la promotion pour la définition partielle à l’intérieur de `sampleModule` . Par conséquent, il tente de compiler deux classes distinctes et distinctes, à la fois nommées, `sampleClass` mais avec des chemins de qualification différents.  
  
 Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.  
  
## <a name="recommendations"></a>Recommandations  

 Les recommandations suivantes représentent une bonne pratique de programmation.  
  
- **Noms uniques.** Lorsque vous avez un contrôle total sur le nom des éléments de programmation, il est toujours judicieux d’utiliser des noms uniques partout. Des noms identiques nécessitent une qualification supplémentaire et peuvent rendre votre code plus difficile à lire. Ils peuvent également entraîner des erreurs subtiles et des résultats inattendus.  
  
- **Qualification complète.** Lorsque vous travaillez avec des modules et d’autres éléments dans le même espace de noms, l’approche la plus sûre consiste à toujours utiliser la qualification complète pour tous les éléments de programmation. Si la promotion de type est invalidée pour un membre de module et que vous ne qualifiez pas complètement ce membre, vous pouvez accéder par inadvertance à un élément de programmation différent.  
  
## <a name="see-also"></a>Voir aussi

- [Module, instruction](../../../language-reference/statements/module-statement.md)
- [Namespace, instruction](../../../language-reference/statements/namespace-statement.md)
- [Partial](../../../language-reference/modifiers/partial.md)
- [Portée dans Visual Basic](scope.md)
- [Comment : contrôler la portée d'une variable](how-to-control-the-scope-of-a-variable.md)
- [References to Declared Elements](references-to-declared-elements.md)
