---
title: <para> -Guide de programmation C#
description: En savoir plus sur le XML <para> balise. Cette balise vous permet d’ajouter une structure au texte d’une autre balise, telle que <summary>, <remarks>ou <returns>.
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: 146078bcb556b4085724ddcdac561ea868ab0481
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381851"
---
# <a name="para-c-programming-guide"></a>\<para>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<para>content</para>
```

## <a name="parameters"></a>Paramètres

- `content`

  Texte du paragraphe.

## <a name="remarks"></a>Notes

La `<para>` balise est destinée à être utilisée à l’intérieur d’une balise, telle que [\<summary>](./summary.md) , [\<remarks>](./remarks.md) ou [\<returns>](./returns.md) , et vous permet d’ajouter une structure au texte.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[\<summary>](./summary.md)Pour obtenir un exemple d’utilisation de `<para>` , consultez.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
