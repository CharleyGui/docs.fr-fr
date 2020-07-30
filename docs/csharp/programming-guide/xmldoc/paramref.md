---
title: <paramref>-Guide de programmation C#
description: En savoir plus sur la <paramref> balise XML. Cette balise vous donne un moyen d’indiquer qu’un mot du code est un paramètre.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 133f43abfaf349806404d6d37fb472e3145c51b7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381838"
---
# <a name="paramref-c-programming-guide"></a>\<paramref>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Paramètres

- `name`

  Nom du paramètre auquel faire référence. Mettez le nom entre guillemets doubles (" ").

## <a name="remarks"></a>Notes

La `<paramref>` balise vous donne un moyen d’indiquer qu’un mot dans les commentaires de code, par exemple dans un `<summary>` `<remarks>` bloc ou fait référence à un paramètre. Le fichier XML peut être traité de manière à mettre en forme ce mot d’une façon particulière, par exemple en gras ou en italique.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
