---
title: Commentaires sur la documentation XML - Guide de programmation CMD
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: f5a507bc35b0cc0a679fd055bfc255bb3cb9a090
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76789794"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Commentaires de documentation XML (guide de programmation C)

Dans le code C, vous pouvez créer de la documentation pour votre code en incluant des éléments XML dans des champs de commentaires spéciaux (indiqués par triples barres obliques) dans le code source directement avant le bloc de code auquel les commentaires se réfèrent, par exemple.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

Lorsque vous compilez avec l’option [-doc,](../../language-reference/compiler-options/doc-compiler-option.md) le compilateur recherche toutes les balises XML dans le code source et créera un fichier de documentation XML. Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).

Pour faire référence à des éléments XML (par exemple, votre fonction traite des éléments XML spécifiques que vous souhaitez décrire dans un commentaire de documentation XML), vous pouvez utiliser le mécanisme de citation standard (`<` et `>`).  Pour faire référence aux identificateurs génériques dans les éléments de référence de code (`cref`), vous pouvez utiliser des caractères d’échappement (par exemple, `cref="List&lt;T&gt;"`) ou des accolades (`cref="List{T}"`).  En tant que cas particulier, le compilateur analyse les accolades comme des crochets pointus pour rendre le commentaire de documentation moins fastidieux à créer lorsqu'il s'agit de faire référence aux identificateurs génériques.

> [!NOTE]
> Les commentaires de documentation XML ne sont pas des métadonnées. Ils ne sont pas inclus dans l'assembly compilé et ne sont donc pas accessibles par réflexion.

## <a name="in-this-section"></a>Contenu de cette section

- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)

- [Traitement du fichier XML](./processing-the-xml-file.md)

- [Délimiteurs pour les balises de documentation](./delimiters-for-documentation-tags.md)

- [Comment utiliser les fonctionnalités de la documentation XML](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>Sections connexes

Pour plus d'informations, consultez les pages suivantes :

- [-doc (Commentaires sur la documentation des processus)](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
