---
title: <value> -Guide de programmation C#
description: En savoir plus sur le XML <value> balise. Cette balise vous permet de décrire la valeur représentée par une propriété.
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: d8294b477d7067653c71d1ec2047a85a0bfe6d02
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380772"
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
