---
title: Balises recommandées pour les C# commentaires de documentation-Guide de programmation
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789726"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Balises recommandées pour lesC# commentaires de documentation (Guide de programmation)

Le compilateur C# traite les commentaires de documentation dans votre code et les met au format XML dans un fichier dont vous spécifiez le nom dans l’option de ligne de commande **/doc**. Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).

Les balises sont traitées sur les constructions de code telles que les types et les membres de types.

> [!NOTE]
> Il n’est pas possible d’appliquer des commentaires de documentation à un espace de noms.  
  
 Le compilateur traite toute balise représentant du code XML correct. Les balises suivantes fournissent des fonctionnalités fréquemment utilisées dans la documentation utilisateur.  
  
## <a name="tags"></a>Balises  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<see>](./see.md)*|[\<value>](./value.md)  
|[\<code>](./code.md)|[\<param>](./param.md)*|[\<seealso>](./seealso.md)*|  
|[\<example>](./example.md)|[\<paramref>](./paramref.md)|[\<summary>](./summary.md)|  
|[\<exception>](./exception.md)*|[\<permission>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<include>](./include.md)*|[\<remarks>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<list>](./list.md)|[\<inheritdoc >](./inheritdoc.md)|[\<returns>](./returns.md)|
  
(\* indique que le compilateur vérifie la syntaxe.)

Si vous voulez que des crochets pointus apparaissent dans le texte d’un commentaire de documentation, utilisez le codage HTML de `<` et `>`, respectivement `&lt;` et `&gt;`. Cet encodage est illustré dans l’exemple suivant.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [-doc (C# options du compilateur)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Commentaires de documentation XML](./index.md)
