---
title: Documentation XML
description: 'En savoir plus sur la prise en charge dans F # pour générer la documentation à partir de commentaires.'
ms.date: 05/16/2016
ms.openlocfilehash: 03d14cef910d149f0c7a2f3a49c8cf4606ac5305
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556575"
---
# <a name="xml-documentation"></a>Documentation XML

Vous pouvez produire une documentation à partir de commentaires de code triple barre oblique (///) en F #. Les commentaires XML peuvent précéder des déclarations dans des fichiers de code (. FS) ou des fichiers de signature (. FSI).

## <a name="generating-documentation-from-comments"></a>Génération de la documentation à partir de commentaires

La prise en charge de F # pour générer la documentation à partir de commentaires est identique à celle des autres .NET Framework langages. Comme dans d’autres langages de .NET Framework, l' [option de compilateur-doc](./compiler-options.md) vous permet de produire un fichier XML qui contient des informations que vous pouvez convertir en documentation à l’aide d’un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB). La documentation générée à l’aide d’outils conçus pour être utilisés avec les assemblys écrits dans d’autres .NET Framework langages produit généralement une vue des API basée sur la forme compilée des constructions F #. À moins que les outils ne prennent en charge F # spécifiquement, la documentation générée par ces outils ne correspond pas à la vue F # d’une API.

Pour plus d’informations sur la génération de documentation à partir de XML, consultez [Commentaires sur la documentation xml &#40;Guide de programmation du&#35; C&#41;](../../csharp/programming-guide/xmldoc/index.md).

## <a name="recommended-tags"></a>Étiquettes recommandées

Il existe deux façons d’écrire des commentaires de documentation XML. L’une consiste à écrire simplement la documentation directement dans un commentaire triple barre, sans utiliser de balises XML. Dans ce cas, le texte de commentaire entier est considéré comme la documentation récapitulative de la construction de code qui suit immédiatement. Utilisez cette méthode lorsque vous souhaitez écrire uniquement un bref résumé pour chaque construction. L’autre méthode consiste à utiliser des balises XML pour fournir une documentation plus structurée. La deuxième méthode vous permet de spécifier des remarques distinctes pour un bref résumé, des remarques supplémentaires, de la documentation pour chaque paramètre et paramètre de type et les exceptions levées, ainsi qu’une description de la valeur de retour. Le tableau suivant décrit les balises XML qui sont reconnues dans les commentaires de code XML F #.

|Syntaxe de balise|Description|
|----------|-----------|
|**\<c\>**_financière_**\</c\>**|Spécifie que le *texte* est du code. Cette balise peut être utilisée par les générateurs de documentation pour afficher du texte dans une police appropriée pour le code.|
|**\<summary\>**_financière_**\</summary\>**|Spécifie que le *texte* est une brève description de l’élément de programme. La description correspond généralement à une ou deux phrases.|
|**\<remarks\>**_financière_**\</remarks\>**|Spécifie que le *texte* contient des informations supplémentaires sur l’élément de programme.|
|**\<param name="**_name_**"\>**_descriptive_**\</param\>**|Spécifie le nom et la description d’un paramètre de fonction ou de méthode.|
|**\<typeparam name="**_name_**"\>**_descriptive_**\</typeparam\>**|Spécifie le nom et la description d’un paramètre de type.|
|**\<returns\>**_financière_**\</returns\>**|Spécifie que le *texte* décrit la valeur de retour d’une fonction ou d’une méthode.|
|**\<exception cref="**_type_**"\>**_descriptive_**\</exception\>**|Spécifie le type d’exception qui peut être généré et les circonstances dans lesquelles il est levé.|
|**\<see cref="**_reference_**"\>**_financière_**\</see\>**|Spécifie un lien Inline vers un autre élément de programme. La *référence* est le nom tel qu’il apparaît dans le fichier de documentation XML. Le *texte* est le texte affiché dans le lien.|
|**\<seealso cref="**_reference_**"/\>**|Spécifie un lien Voir également vers la documentation d’un autre type. La *référence* est le nom tel qu’il apparaît dans le fichier de documentation XML. Consultez également les liens qui apparaissent généralement en bas d’une page de documentation.|
|**\<para\>**_financière_**\</para\>**|Spécifie un paragraphe de texte. Il est utilisé pour séparer le texte dans la balise **Notes** .|

## <a name="example"></a> Exemple

### <a name="description"></a>Description

Voici un commentaire de documentation XML standard dans un fichier de signature.

### <a name="code"></a>Code

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="example"></a> Exemple

### <a name="description"></a>Description

L’exemple suivant illustre la méthode alternative, sans balises XML. Dans cet exemple, le texte entier du commentaire est considéré comme un résumé. Notez que si vous ne spécifiez pas explicitement une balise de résumé, vous ne devez pas spécifier d’autres balises, telles que **param** ou **Return** Tags.

### <a name="code"></a>Code

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Options du compilateur](compiler-options.md)
