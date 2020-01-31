---
title: <permission> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 14abb5bd181f401a4e6834d110e20fa920566580
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789738"
---
# <a name="permission-c-programming-guide"></a>\<> des autorisationsC# (Guide de programmation)

## <a name="syntax"></a>Syntaxe

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Parameters

- cref = " `member`"

  Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie. Le *membre* doit apparaître entre guillemets doubles (" ").

  Pour plus d’informations sur la façon de créer une référence cref à un type générique, consultez [\<see>](./see.md).

- `description`

  Description de l’accès au membre.

## <a name="remarks"></a>Notes

La balise \<permission> vous permet de documenter l’accès d’un membre. La classe <xref:System.Security.PermissionSet> vous permet de spécifier l’accès à un membre.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
