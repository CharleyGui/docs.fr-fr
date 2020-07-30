---
title: <typeparamref>-Guide de programmation C#
description: En savoir plus sur la <typeparamref> balise XML. Cette balise permet aux consommateurs du fichier de documentation de mettre en forme le mot d’une manière distincte, par exemple en italique.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a39e896f1242452c7bcc94faa1e7ef3086ae2149
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380720"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Paramètres

- `name`

  Nom du paramètre de type. Mettez le nom entre guillemets doubles (" ").

## <a name="remarks"></a>Notes

Pour plus d’informations sur les paramètres de type dans les types et méthodes génériques, consultez [Génériques](../generics/index.md).

Utilisez cette balise pour permettre aux consommateurs du fichier de documentation d’appliquer une mise en forme particulière au mot, par exemple l’italique.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
