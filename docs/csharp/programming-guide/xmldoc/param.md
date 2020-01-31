---
title: <param> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789761"
---
# <a name="param-c-programming-guide"></a>\<param > (C# Guide de programmation)

## <a name="syntax"></a>Syntaxe

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parameters

- `name`

  Nom d’un paramètre de méthode. Mettez le nom entre guillemets doubles (" ").

- `description`

  Description du paramètre.

## <a name="remarks"></a>Notes

La balise \<param> doit être utilisée dans le commentaire de la déclaration d’une méthode pour décrire l’un des paramètres de la méthode. Pour documenter plusieurs paramètres, utilisez plusieurs balises \<param>.

Le texte de la balise \<param> s’affiche dans IntelliSense, dans l’Explorateur d’objets et dans le rapport web de commentaire de code.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
