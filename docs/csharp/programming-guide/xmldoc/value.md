---
title: <value> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793354"
---
# <a name="value-c-programming-guide"></a>> de la valeurC# \<(Guide de programmation)

## <a name="syntax"></a>Syntaxe

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parameters

- `property-description`

  Description de la propriété.

## <a name="remarks"></a>Notes

La balise \<value> vous permet de décrire la valeur représentée par une propriété. Notez que lorsque vous ajoutez une propriété via l’Assistant Code de l’environnement de développement Visual Studio .NET, il ajoute une balise [\<summary>](./summary.md) pour la nouvelle propriété. Vous devez ensuite ajouter manuellement une balise \<value> pour décrire la valeur représentée par la propriété.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
