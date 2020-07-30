---
title: <c>-Guide de programmation C#
description: En savoir plus sur la <c> balise XML. Cette balise marque un texte sur une seule ligne dans une description comme du code, alors que <code>indicates multiple lines.
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
ms.openlocfilehash: 78e59e1df4b096782e0a97b6d12c21c843a1cb21
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382020"
---
# <a name="c-c-programming-guide"></a>\<c>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<c>text</c>
```

## <a name="parameters"></a>Paramètres

- `text`

  Texte que vous souhaitez indiquer comme étant du code.

## <a name="remarks"></a>Notes

La `<c>` balise vous donne un moyen d’indiquer que le texte d’une description doit être marqué comme étant du code. Utilisez [\<code>](./code.md) pour indiquer plusieurs lignes en tant que code.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
