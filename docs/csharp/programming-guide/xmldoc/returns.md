---
title: <returns> -Guide de programmation C#
description: En savoir plus sur le XML <returns> balise. Cette balise est utilisée dans le commentaire d’une déclaration de méthode pour décrire la valeur de retour.
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: e461d46df619a351048ae7942e59847d39e490f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381396"
---
# <a name="returns-c-programming-guide"></a>\<returns>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<returns>description</returns>
```

## <a name="parameters"></a>Paramètres

- `description`

  Description de la valeur de retour.

## <a name="remarks"></a>Notes

La `<returns>` balise doit être utilisée dans le commentaire pour une déclaration de méthode afin de décrire la valeur de retour.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
