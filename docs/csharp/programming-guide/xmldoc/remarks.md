---
title: <remarks> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793370"
---
# <a name="remarks-c-programming-guide"></a>\<notes > (C# Guide de programmation)

## <a name="syntax"></a>Syntaxe

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parameters

- `Description`

  Description du membre.

## <a name="remarks"></a>Notes

La balise \<remarks> permet d’ajouter des informations sur un type en complétant les informations spécifiées par [\<summary>](./summary.md). Ces informations sont affichées dans la fenêtre Explorateur d’objets.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
