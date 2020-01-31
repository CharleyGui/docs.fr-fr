---
title: <seealso> - C# Guide de programmation
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: ad22b423d085a152f47c4e34d7ee4247ef9836b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789681"
---
# <a name="seealso-c-programming-guide"></a>\<seealso > (C# Guide de programmation)

## <a name="syntax"></a>Syntaxe

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parameters

- cref = " `member`"

  Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie. `member` doit être placé entre guillemets doubles (" ").

  Pour plus d’informations sur la façon de créer une référence cref à un type générique, consultez [\<see>](./see.md).

## <a name="remarks"></a>Notes

La balise \<seealso> vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi. Utilisez [\<see>](./see.md) pour spécifier un lien à partir de l’intérieur du texte.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de \<seealso>, consultez [\<summary>](./summary.md).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
