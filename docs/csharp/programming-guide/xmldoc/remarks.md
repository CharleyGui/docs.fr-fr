---
title: <remarks> -Guide de programmation C#
description: En savoir plus sur le XML <remarks> balise. Cette balise est utilisée pour ajouter des informations sur un type, en complétant les informations spécifiées avec <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381500"
---
# <a name="remarks-c-programming-guide"></a>\<remarks>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Paramètres

- `Description`

  Description du membre.

## <a name="remarks"></a>Notes

La `<remarks>` balise est utilisée pour ajouter des informations sur un type et compléter les informations spécifiées par [\<summary>](./summary.md) . Ces informations sont affichées dans la fenêtre Explorateur d’objets.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
