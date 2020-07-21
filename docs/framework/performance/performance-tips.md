---
title: Conseils relatifs aux performances .NET
description: Explorez les conseils en matière de performances pour améliorer la vitesse d’exécution d’un programme dans .NET. Consultez les conseils pour la conversion boxing et unboxing, les chaînes et les destructeurs.
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2b3be8b42b5046e52074236de01ca312a0a9a361
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474265"
---
# <a name="net-performance-tips"></a>Conseils relatifs aux performances .NET
Le terme *performances* désigne généralement la vitesse d’exécution d’un programme. Vous pouvez parfois augmenter la vitesse d’exécution en suivant certaines règles de base dans votre code source. Dans certains programmes, il est important d’examiner attentivement le code et d’utiliser des profileurs pour garantir que le programme s’exécute aussi rapidement que possible. Dans d’autres programmes, vous n’avez pas à effectuer une telle optimisation, car le code, tel qu’il est écrit, est suffisamment rapide. Cet article répertorie les zones dont les performances sont fréquemment impactées, et fournit des conseils d’amélioration, ainsi que des liens vers d’autres rubriques relatives aux performances. Pour plus d’informations sur la planification et la mesure des performances, consultez [Performances](index.md)  
  
## <a name="boxing-and-unboxing"></a>Conversion boxing et unboxing  
 Il est préférable de ne pas utiliser de types valeur lorsque ceux-ci doivent être convertis (boxed) de nombreuses fois, par exemple, dans les classes de collections non génériques comme <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Vous pouvez éviter le boxing des types valeur en utilisant des collections génériques comme <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Le boxing et l’unboxing sont des processus qui coûtent cher en calcul. Lorsqu’un type valeur est converti (boxed), un tout nouvel objet doit être créé. Cela peut être 20 fois plus long qu’une simple assignation de référence. Lors d’une conversion unboxing, le processus de cast peut être quatre fois plus long que celui d’une assignation. Pour plus d’informations, consultez [Conversion boxing et unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Chaînes  
 Lorsque vous concaténez un grand nombre de variables de chaîne, par exemple, dans une boucle serrée, utilisez <xref:System.Text.StringBuilder?displayProperty=nameWithType> au lieu de [l’opérateur +](../../csharp/language-reference/operators/addition-operator.md) C# ou des [opérateurs de concaténation](../../visual-basic/language-reference/operators/concatenation-operators.md) Visual Basic. Pour plus d’informations, consultez [Comment concaténer plusieurs chaînes](../../csharp/how-to/concatenate-multiple-strings.md) et [opérateurs de concaténation dans Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destructeurs  
 Les destructeurs vides ne doivent pas être utilisés. Quand une classe contient un destructeur, une entrée est créée dans la file d’attente Finalize. Quand le destructeur est appelé, le récupérateur de mémoire est appelé pour traiter la file d’attente. Si le destructeur est vide, cela ne fait que dégrader les performances. Pour plus d’informations, consultez [Destructeurs](../../csharp/programming-guide/classes-and-structs/destructors.md) et [Durée de vie d’un objet : création et destruction des objets](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Autres ressources  
  
- [Writing Faster Managed Code: Know What Things Cost](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973852(v=msdn.10))  
  
- [Writing High-Performance Managed Applications: A Primer](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973858(v=msdn.10))  
  
- [Garbage Collector Basics and Performance Hints](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973837(v=msdn.10))  
  
- [Performance Tips and Tricks in .NET Applications](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v=msdn.10))  

- [Rico Mariani’s Performance Tidbits](https://docs.microsoft.com/archive/blogs/ricom/) (Blog de Rico Mariani sur les performances)  

- [Blog de Vance Morrison](https://docs.microsoft.com/archive/blogs/vancem/)
  
## <a name="see-also"></a>Voir aussi

- [Performances](index.md)
- [Guide de programmation Visual Basic](../../visual-basic/programming-guide/index.md)
- [Guide de programmation C#](../../csharp/programming-guide/index.md)
