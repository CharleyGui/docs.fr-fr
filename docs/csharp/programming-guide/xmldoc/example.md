---
title: <example> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 615eccbc427b6a5bbbed061acd0c8b0b9be7f46c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789815"
---
# <a name="example-c-programming-guide"></a>> exemple de \<C# (Guide de programmation)

## <a name="syntax"></a>Syntaxe

```xml
<example>description</example>
```

## <a name="parameters"></a>Parameters

- `description`

  Description de l’exemple de code.

## <a name="remarks"></a>Notes

La balise \<example> vous permet de spécifier un exemple d’utilisation d’une méthode ou de tout autre membre de bibliothèque. Cela implique généralement l’utilisation de la balise [\<code>](./code.md).

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
