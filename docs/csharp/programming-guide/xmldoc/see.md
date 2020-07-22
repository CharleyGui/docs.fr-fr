---
title: <see>-Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 731e42a6d4d354b043a56dbe150bb03a693a9454
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86863784"
---
# <a name="see-c-programming-guide"></a>\<see>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Paramètres

- CREF = " `member` "

  Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie. Placez le *membre* entre guillemets doubles (" ").

## <a name="remarks"></a>Notes

La `<see>` balise vous permet de spécifier un lien à partir de texte. Utilisez [\<seealso>](./seealso.md) pour indiquer que le texte doit être placé dans une section Voir aussi. Utilisez l’[attribut cref](./cref-attribute.md) pour créer des liens hypertexte internes aux pages de documentation pour les éléments de code. En outre, ``href`` est un attribut valide qui fonctionnera comme un lien hypertexte.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

L’exemple suivant montre une `<see>` balise dans une section Résumé.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
