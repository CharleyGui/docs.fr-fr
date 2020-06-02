---
title: <value> -Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287192"
---
# <a name="value-c-programming-guide"></a>\<value>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Paramètres

- `property-description`

  Description de la propriété.

## <a name="remarks"></a>Notes

La `<value>` balise vous permet de décrire la valeur représentée par une propriété. Lorsque vous ajoutez une propriété à l’aide de l’Assistant code dans l’environnement de développement Visual Studio .NET, elle ajoute une [\<summary>](./summary.md) balise pour la nouvelle propriété. Vous devez ensuite ajouter manuellement une `<value>` balise pour décrire la valeur représentée par la propriété.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
