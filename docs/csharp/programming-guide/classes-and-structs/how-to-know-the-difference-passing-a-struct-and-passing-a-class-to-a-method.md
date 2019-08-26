---
title: "Procédure : Différencier le passage d'un struct et le passage d'une référence de classe à une méthode - Guide de programmation C#"
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], passing as method parameter
- passing parameters [C#], structs vs. classes
- methods [C#], passing classes vs. structs
ms.assetid: 9c1313a6-32a8-4ea7-a59f-450f66af628b
ms.openlocfilehash: 889e1f5719e094d02f0cc27256e1c430ffce0b8e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596785"
---
# <a name="how-to-know-the-difference-between-passing-a-struct-and-passing-a-class-reference-to-a-method-c-programming-guide"></a>Procédure : Différencier le passage d'un struct et le passage d'une référence de classe à une méthode (Guide de programmation C#)
L’exemple suivant montre comment le passage d’un [struct](../../language-reference/keywords/struct.md) à une méthode diffère du passage d’une instance de [classe](../../language-reference/keywords/class.md) à une méthode. Dans l’exemple, les deux arguments (struct et instance de classe) sont passés par valeur, tandis que les deux méthodes changent la valeur d’un champ de l’argument. Toutefois, les résultats des deux méthodes ne sont pas identiques, car ce qui est passé quand vous passez un struct diffère de ce qui est passé quand vous passez une instance d’une classe.  
  
 Étant donné qu’un struct est un [type valeur](../../language-reference/keywords/value-types.md), quand vous [passez un struct par valeur](./passing-value-type-parameters.md) à une méthode, la méthode reçoit et traite une copie de l’argument struct. La méthode n’a pas accès au struct d’origine dans la méthode d’appel, et ne peut donc pas le modifier de quelque manière que ce soit. La méthode peut modifier uniquement la copie.  
  
 Une instance de classe est un [type référence](../../language-reference/keywords/reference-types.md), pas un type valeur. Quand [un type référence est passé par valeur](./passing-reference-type-parameters.md) à une méthode, celle-ci reçoit une copie de la référence à l’instance de classe. Autrement dit, la méthode reçoit une copie de l’adresse de l’instance, et non pas une copie de l’instance elle-même. L’instance de classe dans la méthode d’appel a une adresse, le paramètre dans la méthode appelée a une copie de l’adresse, et les deux adresses font référence au même objet. Étant donné que le paramètre contient uniquement une copie de l’adresse, la méthode appelée ne peut pas modifier l’adresse de l’instance de la classe dans la méthode. Toutefois, la méthode appelée peut utiliser l’adresse pour accéder aux membres de classe qui font à la fois référence à l’adresse d’origine et à la copie. Si la méthode appelée modifie un membre de classe, l’instance de classe d’origine dans la méthode d’appel change également.  
  
 La sortie de l’exemple suivant illustre la différence. La valeur du champ `willIChange` de l’instance de classe est changée par l’appel à la méthode `ClassTaker`, car la méthode utilise l’adresse mentionnée dans le paramètre pour rechercher le champ spécifié de l’instance de classe. Le champ `willIChange` du struct de la méthode d’appel n’est pas changé par l’appel à la méthode `StructTaker`, car la valeur de l’argument est une copie du struct lui-même, et non pas une copie de son adresse. `StructTaker` change la copie, et cette dernière est perdue quand l’appel à `StructTaker` est terminé.  
  
## <a name="example"></a>Exemples  
 [!code-csharp[csProgGuideObjects#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#32)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes](./classes.md)
- [Structs](./structs.md)
- [Passage de paramètres](./passing-parameters.md)
