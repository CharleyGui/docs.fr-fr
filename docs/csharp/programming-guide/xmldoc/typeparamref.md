---
title: Guide de C# programmation de <typeparamref>
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789660"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref > (C# Guide de programmation)

## <a name="syntax"></a>Syntaxe

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parameters

- `name`

  Nom du paramètre de type. Mettez le nom entre guillemets doubles (" ").

## <a name="remarks"></a>Notes

Pour plus d’informations sur les paramètres de type dans les types et méthodes génériques, consultez [Génériques](../generics/index.md).

Utilisez cette balise pour permettre aux consommateurs du fichier de documentation d’appliquer une mise en forme particulière au mot, par exemple l’italique.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
