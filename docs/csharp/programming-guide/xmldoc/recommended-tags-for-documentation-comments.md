---
title: Étiquettes recommandées pour les commentaires de documentation - Guide de programmation C
ms.date: 01/21/2020
helpviewer_keywords:
- XML [C#], tags
- XML documentation [C#], tags
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
ms.openlocfilehash: c746615d0d7a7a3058fbe2f8506a7a7c5c4a8779
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789726"
---
# <a name="recommended-tags-for-documentation-comments-c-programming-guide"></a>Étiquettes recommandées pour les commentaires de documentation (guide de programmation C)

Le compilateur C# traite les commentaires de documentation dans votre code et les met au format XML dans un fichier dont vous spécifiez le nom dans l’option de ligne de commande **/doc**. Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé, ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).

Les balises sont traitées sur les constructions de code telles que les types et les membres de types.

> [!NOTE]
> Il n’est pas possible d’appliquer des commentaires de documentation à un espace de noms.  
  
 Le compilateur traite toute balise représentant du code XML correct. Les balises suivantes fournissent des fonctionnalités fréquemment utilisées dans la documentation utilisateur.  
  
## <a name="tags"></a>Balises  
  
|||||  
|---|---|---|---|
|[\<c>](./code-inline.md)|[\<para>](./para.md)|[\<voir>](./see.md)*|[\<>de valeur](./value.md)  
|[\<>de code](./code.md)|[\<>de param](./param.md)*|[\<>](./seealso.md)*|  
|[\<exemple>](./example.md)|[\<>paramref](./paramref.md)|[\<>résumé](./summary.md)|  
|[\<>d’exception](./exception.md)*|[\<autorisation>](./permission.md)*|[\<typeparam>](./typeparam.md)*|  
|[\<inclure>](./include.md)*|[\<remarques>](./remarks.md)|[\<typeparamref>](./typeparamref.md)|  
|[\<liste>](./list.md)|[\<>héritière](./inheritdoc.md)|[\<retourne>](./returns.md)|
  
(\* dénote que le compilateur vérifie la syntaxe.)

Si vous voulez que des crochets pointus apparaissent dans le texte d’un commentaire de documentation, utilisez le codage HTML de `<` et `>`, respectivement `&lt;` et `&gt;`. Ce codage est indiqué dans l’exemple suivant.

```csharp
/// <summary>
/// This property always returns a value &lt; 1.
/// </summary>
```

## <a name="see-also"></a>Voir aussi

- [Guide de programmation CMD](../index.md)
- [-doc (options de compilateur de C)](../../language-reference/compiler-options/doc-compiler-option.md)
- [Commentaires sur la documentation XML](./index.md)
