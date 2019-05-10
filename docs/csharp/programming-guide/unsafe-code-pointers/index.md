---
title: Pointeurs et code unsafe - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 9f4e74e1e8fa71d1492a10162191822c1edfb635
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608035"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Pointeurs et code unsafe (Guide de programmation C#)
Pour conserver la sécurité des types, par défaut, C# ne prend pas en charge les opérations arithmétiques sur les pointeurs. Cependant, en utilisant le mot clé [unsafe](../../../csharp/language-reference/keywords/unsafe.md), vous pouvez définir un contexte non sécurisé dans lequel des pointeurs peuvent être utilisés. Pour plus d’informations sur les pointeurs, consultez la rubrique [Types pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  Dans le common language runtime (CLR), le code non sécurisé est appelé « code non vérifiable ». Le code non sécurisé en C# n’est pas nécessairement dangereux : il s’agit simplement de code dont la sécurité ne peut pas être vérifiée par le CLR. Le CLR exécute du code non sécurisé seulement s’il se trouve dans un assembly entièrement fiable. Si vous utilisez du code non sécurisé, il vous incombe de vérifier que votre code n’introduit pas de risques de sécurité ni d’erreurs de pointeur.  
  
## <a name="unsafe-code-overview"></a>Vue d’ensemble du code non sécurisé  
 Le code non sécurisé a les propriétés suivantes :  
  
- Les méthodes, les types et les blocs de code peuvent être définis comme non sécurisés.  
  
- Dans certains cas, le code non sécurisé peut augmenter les performances d’une application en supprimant les vérifications des limites des tableaux.  
  
- Du code non sécurisé est obligatoire quand vous appelez des fonctions natives nécessitant des pointeurs.  
  
- L’utilisation de code non sécurisé introduit des risques pour la sécurité et la stabilité.  
  
- Pour que C# compile du code non sécurisé, l’application doit être compilée avec [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations, voir :  
  
- [Types de pointeur](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
- [Mémoires tampons de taille fixe](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
- [Guide pratique pour utiliser des pointeurs pour copier un tableau d’octets](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../../csharp/programming-guide/index.md)
