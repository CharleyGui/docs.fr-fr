---
title: <param> -Guide de programmation C#
description: En savoir plus sur le XML <param> balise. Cette balise est utilisée dans le commentaire d’une déclaration de méthode pour décrire l’un des paramètres de la méthode.
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: a9e3b2e86528afcbe1330788e248f0143efb5c1b
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381552"
---
# <a name="param-c-programming-guide"></a>\<param>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Paramètres

- `name`

  Nom d’un paramètre de méthode. Mettez le nom entre guillemets doubles (" ").

- `description`

  Description du paramètre.

## <a name="remarks"></a>Notes

La `<param>` balise doit être utilisée dans le commentaire d’une déclaration de méthode pour décrire l’un des paramètres de la méthode. Pour documenter plusieurs paramètres, utilisez plusieurs `<param>` balises.

Le texte de la `<param>` balise s’affiche dans IntelliSense, dans l’Explorateur d’objets et dans le rapport Web de commentaire de code.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
