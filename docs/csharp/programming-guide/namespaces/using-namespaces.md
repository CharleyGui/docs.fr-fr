---
title: Utilisation d'espaces de noms - Guide de programmation C#
description: Découvrez comment utiliser des espaces de noms en programmation C#, tels que l’accès aux espaces de noms, les alias d’espaces de noms et l’utilisation d’espaces de noms pour contrôler la portée.
ms.date: 07/20/2015
f1_keywords:
- cs.names
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
ms.openlocfilehash: 86892f50e059c16ee9c133d7ba9f2716e11a8e56
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381695"
---
# <a name="using-namespaces-c-programming-guide"></a>Utilisation d'espaces de noms (Guide de programmation C#)

Les espaces de noms sont largement utilisés dans les programmes C#, et ce de deux façons différentes. Tout d’abord, les classes .NET utilisent des espaces de noms pour organiser ses nombreuses classes. En deuxième lieu, la déclaration de vos propres espaces de noms peut faciliter le contrôle de la portée des noms de classes et de méthodes dans les projets de programmation de plus grande envergure.  
  
## <a name="accessing-namespaces"></a>Accès aux espaces de noms

 La plupart des applications C# commencent par une section de directives `using`. Cette section répertorie les espaces de noms que l’application est appelée à utiliser fréquemment et évite au programmeur de spécifier un nom qualifié complet chaque fois qu’une méthode qu’elle contient est utilisée.  
  
 Par exemple, en incluant la ligne :  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 Au début d’un programme, le programmeur peut utiliser le code :  
  
 [!code-csharp[csProgGuide#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#31)]  
  
 À la place de :  
  
 [!code-csharp[csProgGuide#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/progGuide.cs#30)]  
  
## <a name="namespace-aliases"></a>Alias d'espaces de noms

 Vous pouvez également utiliser la [ `using` directive](../../language-reference/keywords/using-directive.md) pour créer un alias pour un espace de noms. Utilisez le [qualificateur d'alias d’espace de noms`::`](../../language-reference/operators/namespace-alias-qualifier.md) pour accéder aux membres de l'espace de noms avec alias. L'exemple suivant montre comment créer et utiliser un alias d’espace de noms :
  
[!code-csharp[csProgGuideNamespaces#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#5)]
  
## <a name="using-namespaces-to-control-scope"></a>Utilisation d’espaces de noms pour contrôler la portée

 Le mot clé `namespace` est utilisé pour déclarer une portée. La possibilité de créer des portées au sein de votre projet facilite l’organisation du code et vous permet de créer des types globalement uniques. Dans l’exemple suivant, une classe intitulée `SampleClass` est définie dans deux espaces de noms, l’un étant imbriqué à l’intérieur de l’autre. Le [ `.` jeton](../../language-reference/operators/member-access-operators.md#member-access-expression-) est utilisé pour distinguer la méthode qui est appelée.  
  
 [!code-csharp[csProgGuideNamespaces#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#8)]  
  
## <a name="fully-qualified-names"></a>Noms qualifiés complets

 Les espaces de noms et les types portent des titres uniques décrits par des noms qualifiés complets qui indiquent une hiérarchie logique. Par exemple, l’instruction `A.B` implique que `A` est le nom de l’espace de noms ou du type et que `B` est imbriqué en son sein.  
  
 Dans l’exemple suivant, il y a des classes et des espaces de noms imbriqués. Le nom qualifié complet est indiqué sous forme de commentaire à la suite de chaque entité.  
  
 [!code-csharp[csProgGuideNamespaces#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#9)]  
  
 Dans le segment de code précédent :  
  
- L’espace de noms `N1` est un membre de l’espace de noms global. Son nom qualifié complet est `N1`.  
  
- L’espace de noms `N2` est un membre de `N1`. Son nom qualifié complet est `N1.N2`.  
  
- La classe `C1` est un membre de `N1`. Son nom qualifié complet est `N1.C1`.  
  
- Le nom de classe `C2` est utilisé deux fois dans ce code. En revanche, les noms qualifiés complets sont uniques. La première instance de `C2` est déclarée à l’intérieur de `C1` ; par conséquent, son nom complet est : `N1.C1.C2`. La deuxième instance de `C2` est déclarée à l’intérieur d’un espace de noms `N2` ; par conséquent, son nom complet est : `N1.N2.C2`.  
  
 À partir du segment de code précédent, vous pouvez ajouter un nouveau membre de classe (`C3`) à l’espace de noms `N1.N2` comme ceci :  
  
 [!code-csharp[csProgGuideNamespaces#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#10)]  
  
 En règle générale, utilisez le [qualificateur d’alias d’espace de noms `::`](../../language-reference/operators/namespace-alias-qualifier.md) pour référencer un alias d’espace de noms ou `global::` pour référencer l’espace de noms global, et `.` pour qualifier les types ou les membres.  
  
 C’est une erreur d’utiliser `::` avec un alias qui fait référence à un type plutôt qu’à un espace de noms. Par exemple :  
  
 [!code-csharp[csProgGuideNamespaces#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#11)]  
  
 [!code-csharp[csProgGuideNamespaces#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#12)]  
  
 Rappelez-vous que le mot `global` n’est pas un alias prédéfini ; par conséquent, `global.X` n’a pas de signification particulière. Il n’acquiert une signification particulière que lorsqu’il est utilisé avec `::`.  
  
 L’avertissement du compilateur CS0440 est généré si vous définissez un alias nommé global, car `global::` fait toujours référence à l’espace de noms global et non à un alias. Par exemple, la ligne suivante génère l’avertissement :  
  
 [!code-csharp[csProgGuideNamespaces#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces2.cs#13)]  
  
 Il est tout à fait opportun d’utiliser `::` avec des alias et cela vous prémunit contre l’introduction inattendue de types supplémentaires. Par exemple, prenons l’exemple suivant :  
  
 [!code-csharp[csProgGuideNamespaces#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#14)]  
  
 [!code-csharp[csProgGuideNamespaces#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#15)]  
  
 Cela fonctionne, mais si un type nommé `Alias` devait par la suite être introduit, `Alias.` se lierait à ce type. L’utilisation de `Alias::Exception` est l’assurance que `Alias` est considéré comme un alias d’espace de noms et qu’il n’est pas pris à tort pour un type.  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Espaces de noms](./index.md)
- [Expression d’accès au membre](../../language-reference/operators/member-access-operators.md#member-access-expression-)
- [:: (opérateur)](../../language-reference/operators/namespace-alias-qualifier.md)
- [extern alias](../../language-reference/keywords/extern-alias.md)
