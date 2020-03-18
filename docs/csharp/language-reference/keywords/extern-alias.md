---
title: extern alias - Référence C#
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 86202333484933d7449b0c4d8c5a3f1a63cd7775
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713549"
---
# <a name="extern-alias-c-reference"></a>extern alias (référence C#)
Il se peut que vous deviez référencer deux versions d’assemblys qui ont le même nom de type qualifié complet. Par exemple, vous pourriez avoir à utiliser plusieurs versions d’un assembly dans la même application. En utilisant un alias d’assembly externe, vous pouvez encapsuler les espaces de noms de chaque assembly dans des espaces de noms racines nommés par l’alias, ce qui permet de les utiliser dans le même fichier.  
  
> [!NOTE]
> Le mot clé [extern](./extern.md) est également utilisé comme modificateur de méthode, déclarant une méthode écrite en code non managé.  
  
 Pour référencer deux assemblys portant le même nom de type qualifié complet, vous devez spécifier un alias à l’invite de commandes, comme suit :  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Cela crée les alias externes `GridV1` et `GridV2`. Pour utiliser ces alias à partir d’un programme, référencez-les en utilisant le mot clé `extern`. Par exemple :  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Chaque déclaration d’alias externe introduit un espace de noms racine supplémentaire qui est parallèle à l’espace de noms global (mais n’est pas compris dedans). Ainsi, vous pouvez référencer les types de chaque assembly sans ambiguïté en utilisant leur nom qualifié complet, enraciné dans l’alias d’espace de noms approprié.  
  
 Dans l’exemple précédent, `GridV1::Grid` serait le contrôle de grille de `grid.dll`, et `GridV2::Grid` serait le contrôle de grille de `grid20.dll`.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [:: Opérateur](../operators/namespace-alias-qualifier.md)
- [-référence (Options compilateur C)](../compiler-options/reference-compiler-option.md)
