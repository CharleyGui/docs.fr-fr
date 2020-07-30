---
title: <permission> -Guide de programmation C#
description: En savoir plus sur le XML <permission> balise. Cette balise vous permet de documenter l’accès d’un membre, tandis que la classe PermissionSet vous permet de spécifier l’accès à un membre.
ms.date: 07/20/2015
f1_keywords:
- permission
- <permission>
helpviewer_keywords:
- <permission> C# XML tag
- permission C# XML tag
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
ms.openlocfilehash: 38c87505b8b2973875e474ffd296dc02b7fb9de6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381721"
---
# <a name="permission-c-programming-guide"></a>\<permission>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<permission cref="member">description</permission>
```

## <a name="parameters"></a>Paramètres

- cref = " `member`"

  Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie. Le *membre* doit apparaître entre guillemets doubles (" ").

  Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [attribut cref](./cref-attribute.md).

- `description`

  Description de l’accès au membre.

## <a name="remarks"></a>Notes

La `<permission>` balise vous permet de documenter l’accès d’un membre. La classe <xref:System.Security.PermissionSet> vous permet de spécifier l’accès à un membre.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[!code-csharp[csProgGuideDocComments#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#8)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
