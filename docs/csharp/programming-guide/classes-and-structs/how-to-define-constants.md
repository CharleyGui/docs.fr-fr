---
title: 'Comment : définir des constantes en C#'
description: Découvrez comment définir des constantes en C#, qui sont des champs dont les valeurs sont définies au moment de la compilation. Utilisez des constantes pour fournir des noms explicites pour les valeurs spéciales.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 43f511be-346c-4b8a-995e-aded94542ece
ms.openlocfilehash: 42ea67e9012fd55fbceb8a7bad4c8df8bf6bf6da
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099385"
---
# <a name="how-to-define-constants-in-c"></a>Comment définir des constantes en C\#

Les constantes sont des champs dont les valeurs sont définies au moment de la compilation et ne sont pas modifiables. Utilisez des constantes pour fournir des noms explicites au lieu de littéraux numériques (« nombres magiques ») pour les valeurs spéciales.  
  
> [!NOTE]
> En C#, la directive de préprocesseur [#define](../../language-reference/preprocessor-directives/preprocessor-define.md) ne peut pas être utilisée pour définir des constantes de la manière généralement utilisée en C et C++.  
  
 Pour définir des valeurs constantes de types intégraux (`int`, `byte`, etc.), utilisez un type énuméré. Pour plus d’informations, consultez [enum](../../language-reference/builtin-types/enum.md).  
  
 Pour définir des constantes non intégrales, une approche consiste à les regrouper dans une classe statique unique nommée `Constants`. Cette opération exige que toutes les références aux constantes soient précédées par le nom de classe, comme dans l’exemple suivant.  
  
## <a name="example"></a>Exemple  

 [!code-csharp[csProgGuideObjects#89](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#89)]  
  
 L’utilisation du qualificateur de nom de classe permet de garantir que les personnes qui utilisent la constante, dont vous-même, comprennent qu’il s’agit d’une valeur constante et qu’elle ne peut pas être modifiée.  
  
## <a name="see-also"></a>Voir aussi

- [Classes et structs](./index.md)
