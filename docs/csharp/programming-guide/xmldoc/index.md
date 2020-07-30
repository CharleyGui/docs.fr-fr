---
title: Commentaires de documentation XML-Guide de programmation C#
description: En savoir plus sur les commentaires de documentation XML. Vous pouvez créer une documentation pour votre code en incluant des éléments XML dans des champs de commentaire spéciaux.
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
ms.openlocfilehash: fbdeb53331d9fc63d24a3322ea13863d7c0a3630
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381877"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Commentaires de documentation XML (Guide de programmation C#)

En C#, vous pouvez créer de la documentation pour votre code en incluant des éléments XML dans des champs de commentaire spéciaux (indiqués par trois barres obliques) dans le code source, juste avant le bloc de code auquel les commentaires font référence, par exemple.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

Quand vous compilez avec l’option [-doc](../../language-reference/compiler-options/doc-compiler-option.md) , le compilateur recherche toutes les balises XML dans le code source et crée un fichier de documentation XML. Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).

Pour faire référence à des éléments XML (par exemple, votre fonction traite des éléments XML spécifiques que vous souhaitez décrire dans un commentaire de documentation XML), vous pouvez utiliser le mécanisme de citation standard (`<` et `>`).  Pour faire référence aux identificateurs génériques dans les éléments de référence de code (`cref`), vous pouvez utiliser des caractères d’échappement (par exemple, `cref="List&lt;T&gt;"`) ou des accolades (`cref="List{T}"`).  En tant que cas particulier, le compilateur analyse les accolades comme des crochets pointus pour rendre le commentaire de documentation moins fastidieux à créer lorsqu'il s'agit de faire référence aux identificateurs génériques.

> [!NOTE]
> Les commentaires de documentation XML ne sont pas des métadonnées. Ils ne sont pas inclus dans l'assembly compilé et ne sont donc pas accessibles par réflexion.

## <a name="in-this-section"></a>Contenu de cette section

- [Balises recommandées pour les commentaires de documentation](./recommended-tags-for-documentation-comments.md)

- [Traitement du fichier XML](./processing-the-xml-file.md)

- [Délimiteurs pour les balises de documentation](./delimiters-for-documentation-tags.md)

- [Comment utiliser les fonctionnalités de la documentation XML](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>Sections connexes

Pour plus d’informations, consultez :

- [-doc (traiter les commentaires de documentation)](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
