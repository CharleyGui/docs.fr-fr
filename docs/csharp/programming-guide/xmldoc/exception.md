---
title: <exception>-Guide de programmation C#
description: En savoir plus sur la <exception> balise XML. Cette balise vous permet de spécifier les exceptions qui peuvent être levées et qui peuvent être appliquées à des méthodes, des propriétés, des événements et des indexeurs.
ms.date: 07/20/2015
f1_keywords:
- exception
- <exception>
helpviewer_keywords:
- <exception> C# XML tag
- exception C# XML tag
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
ms.openlocfilehash: 22a28f3fe6de5a0db9aea0f1fd7963d4e6fcee05
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381734"
---
# <a name="exception-c-programming-guide"></a>\<exception>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<exception cref="member">description</exception>
```

## <a name="parameters"></a>Paramètres

- cref = " `member`"

  Référence à une exception qui est disponible à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’exception donnée existe, et il traduit `member` en nom d’élément canonique dans le fichier XML de sortie. `member` doit apparaître entre guillemets doubles (" ").

  Pour plus d’informations sur la façon de mettre en forme `member` pour référencer un type générique, consultez [Traitement du fichier XML](processing-the-xml-file.md).

- `description`

  Description de l'exception.

## <a name="remarks"></a>Notes

La `<exception>` balise vous permet de spécifier les exceptions qui peuvent être levées. Cette balise peut être appliquée à des définitions de méthodes, de propriétés, d’événements et d’indexeurs.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

Pour plus d’informations sur la gestion des exceptions, consultez [Exceptions et gestion des exceptions](../exceptions/index.md).

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#4)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](recommended-tags-for-documentation-comments.md)
