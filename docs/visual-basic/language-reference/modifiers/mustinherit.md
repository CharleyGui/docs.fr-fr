---
title: MustOverride
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 30befaaf194d78d26a57f29c59bf0a603e9f07a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351498"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Spécifie qu’une classe peut être utilisée uniquement comme classe de base et que vous ne pouvez pas créer un objet directement à partir de celle-ci.  
  
## <a name="remarks"></a>Notes  
 L’objectif d’une *classe de base* (également appelée *classe abstraite*) est de définir des fonctionnalités communes à toutes les classes qui en sont dérivées. Cela évite aux classes dérivées d’avoir à redéfinir les éléments communs. Dans certains cas, cette fonctionnalité commune n’est pas assez complète pour créer un objet utilisable, et chaque classe dérivée définit les fonctionnalités manquantes. Dans ce cas, vous souhaitez que le code de consommation crée uniquement des objets à partir des classes dérivées. Vous utilisez `MustInherit` sur la classe de base pour appliquer cette.  
  
 Une autre utilisation d’une classe `MustInherit` consiste à limiter une variable à un ensemble de classes connexes. Vous pouvez définir une classe de base et dériver toutes ces classes associées à partir de celle-ci. La classe de base n’a pas besoin de fournir des fonctionnalités communes à toutes les classes dérivées, mais elle peut servir de filtre pour assigner des valeurs à des variables. Si votre code de consommation déclare une variable comme classe de base, Visual Basic vous permet d’assigner uniquement un objet à partir de l’une des classes dérivées de cette variable.  
  
 Le .NET Framework définit plusieurs classes `MustInherit`, entre elles <xref:System.Array>, <xref:System.Enum>et <xref:System.ValueType>. <xref:System.ValueType> est un exemple de classe de base qui restreint une variable. Tous les types valeur dérivent de <xref:System.ValueType>. Si vous déclarez une variable comme <xref:System.ValueType>, vous pouvez assigner uniquement des types valeur à cette variable.  
  
## <a name="rules"></a>Règles  
  
- **Contexte de déclaration.** Vous pouvez utiliser `MustInherit` uniquement dans une instruction `Class`.  
  
- **Modificateurs combinés.** Vous ne pouvez pas spécifier `MustInherit` avec `NotInheritable` dans la même déclaration.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’héritage forcé et le remplacement forcé. La classe de base `shape` définit une variable `acrossLine`. Les classes `circle` et `square` dérivent de `shape`. Ils héritent de la définition de `acrossLine`, mais ils doivent définir la fonction `area`, car ce calcul est différent pour chaque type de forme.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 Vous pouvez déclarer des `shape1` et des `shape2` de type `shape`. Toutefois, vous ne pouvez pas créer un objet à partir de `shape`, car il ne dispose pas de la fonctionnalité de la fonction `area` et est marqué `MustInherit`.  
  
 Étant donné qu’ils sont déclarés comme `shape`, les variables `shape1` et `shape2` sont limitées aux objets des classes dérivées `circle` et `square`. Visual Basic ne vous permet pas d’assigner un autre objet à ces variables, ce qui vous donne un niveau élevé de sécurité de type.  
  
## <a name="usage"></a>Utilisation  
 Le modificateur `MustInherit` peut être utilisé dans ce contexte :  
  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [Mots clés](../../../visual-basic/language-reference/keywords/index.md)
- [Éléments fondamentaux de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
