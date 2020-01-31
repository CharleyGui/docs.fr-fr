---
title: <typeparam> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793365"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam > (C# Guide de programmation)

## <a name="syntax"></a>Syntaxe

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Parameters

- `name`

  Nom du paramètre de type. Mettez le nom entre guillemets doubles (" ").

- `description`

  Description du paramètre de type.

## <a name="remarks"></a>Notes

La balise `<typeparam>` doit être utilisée dans le commentaire d’une déclaration de méthode ou de type générique pour décrire un paramètre de type. Ajoutez une balise pour chaque paramètre de type de la méthode et du type générique.

Pour plus d’informations, consultez [Génériques](../generics/index.md).

Le texte de la balise `<typeparam>` s’affiche dans IntelliSense, dans la [fenêtre Explorateur d’objets](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser) et dans le rapport web de commentaire de code.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../../language-reference/index.md)
- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
