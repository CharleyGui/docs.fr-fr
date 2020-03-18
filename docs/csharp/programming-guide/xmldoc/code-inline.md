---
title: <c>- Guide de programmation C
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793453"
---
# <a name="c-c-programming-guide"></a>\<c> (guide de programmation de C)

## <a name="syntax"></a>Syntaxe

```xml
<c>text</c>
```

## <a name="parameters"></a>Paramètres

- `text`

  Texte que vous souhaitez indiquer comme étant du code.

## <a name="remarks"></a>Notes 

La balise \<c> vous permet d’indiquer que le texte d’une description doit être marqué comme étant du code. Utilisez [ \<le code>](./code.md) pour indiquer plusieurs lignes sous forme de code.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a> Exemple

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation CMD](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
