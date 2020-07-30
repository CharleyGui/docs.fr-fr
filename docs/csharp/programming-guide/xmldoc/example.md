---
title: <example> -Guide de programmation C#
description: En savoir plus sur le XML <example> balise. Cette balise vous permet de spécifier un exemple d’utilisation d’une méthode ou d’un autre membre de bibliothèque.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381526"
---
# <a name="example-c-programming-guide"></a>\<example>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<example>description</example>
```

## <a name="parameters"></a>Paramètres

- `description`

  Description de l’exemple de code.

## <a name="remarks"></a>Notes

La `<example>` balise vous permet de spécifier un exemple d’utilisation d’une méthode ou d’un autre membre de bibliothèque. Cela implique généralement l’utilisation de la [\<code>](./code.md) balise.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
