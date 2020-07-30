---
title: <seealso> -Guide de programmation C#
description: Découvrez comment utiliser le XML <seealso> balise. Cette balise vous permet de spécifier le texte que vous souhaitez voir apparaître dans la section « Voir aussi ».
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
ms.openlocfilehash: e8618ef352a4fa7f0fd4c88733c6568b0e12e376
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380642"
---
# <a name="seealso-c-programming-guide"></a>\<seealso>(Guide de programmation C#)

## <a name="syntax"></a>Syntaxe

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Paramètres

- cref = " `member`"

  Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel. Le compilateur vérifie que l’élément de code donné existe, et qu’il passe `member` au nom d’élément dans le code XML de sortie. `member` doit être placé entre guillemets doubles (" ").

  Pour plus d’informations sur la création d’une référence cref à un type générique, consultez [attribut cref](./cref-attribute.md).

## <a name="remarks"></a>Notes

La `<seealso>` balise vous permet de spécifier le texte que vous souhaitez voir apparaître dans une section Voir aussi. Utilisez [\<see>](./see.md) pour spécifier un lien à partir de texte.

Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.

## <a name="example"></a>Exemple

[\<summary>](./summary.md)Pour obtenir un exemple d’utilisation de \<seealso> , consultez.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)
