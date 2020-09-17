---
title: Documentation XML
description: 'En savoir plus sur la prise en charge dans F # pour générer la documentation à partir de commentaires.'
ms.date: 09/15/2020
ms.openlocfilehash: a5bec20f27c23caee951cda2dc5d17808f69d384
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679401"
---
# <a name="document-your-code-with-xml-comments"></a>Documenter votre code avec des commentaires XML

Vous pouvez produire une documentation à partir de commentaires de code triple barre oblique (///) en F #. Les commentaires XML peuvent précéder des déclarations dans des fichiers de code (. FS) ou des fichiers de signature (. FSI).

Les commentaires de documentation XML sont un genre particulier de commentaire, ajouté au-dessus de la définition d’un type ou d’un membre défini par l’utilisateur.
Ils sont spéciaux, car ils peuvent être traités par le compilateur pour générer un fichier de documentation XML au moment de la compilation.
Le fichier XML généré par le compilateur peut être distribué avec votre assembly .NET afin que les IDE puissent utiliser des info-bulles pour afficher des informations rapides sur les types ou les membres. En outre, le fichier XML peut être exécuté à l’aide d’outils tels que [fsdocs](http://fsprojects.github.io/FSharp.Formatting/) pour générer des sites Web de référence d’API.

Les commentaires de documentation XML, comme tous les autres commentaires, sont ignorés par le compilateur, sauf si les options décrites ci-dessous sont activées pour vérifier la validité et la finalisation des commentaires au moment de la compilation.

Vous pouvez générer le fichier XML au moment de la compilation en procédant comme suit :

- Vous pouvez ajouter un `GenerateDocumentationFile` élément à la `<PropertyGroup>` section de votre `.fsproj` fichier projet, ce qui génère un fichier XML dans le répertoire du projet avec le même nom de fichier racine que l’assembly. Exemple :

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

- Si vous développez une application à l’aide de Visual Studio, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**. Dans la boîte de dialogue des propriétés, sélectionnez l’onglet **Générer**, puis cochez **Fichier de documentation XML**. Vous pouvez également changer l’emplacement dans lequel le compilateur écrit le fichier.

Il existe deux façons d’écrire des commentaires de documentation XML : avec et sans balises XML. Tous deux utilisent des commentaires triple barre.

## <a name="comments-without-xml-tags"></a>Commentaires sans balises XML

Si un `///` commentaire ne commence pas par un `<` , le texte de commentaire entier est pris comme la documentation récapitulative de la construction de code qui suit immédiatement. Utilisez cette méthode lorsque vous souhaitez écrire uniquement un bref résumé pour chaque construction.

Le commentaire est encodé au format XML pendant la préparation de la documentation, ce qui signifie que les caractères tels que `<` `>` et `&` n’ont pas besoin d’être échappés. Si vous ne spécifiez pas explicitement une balise Summary, vous ne devez pas spécifier d’autres balises, telles que **param** ou **Return** Tags.

L’exemple suivant illustre la méthode alternative, sans balises XML. Dans cet exemple, le texte entier du commentaire est considéré comme un résumé.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7102.fs)]

## <a name="comments-with-xml-tags"></a>Commentaires avec des balises XML

Si un corps de commentaire commence par `<` (normalement `<summary>` ), il est traité comme un corps de commentaire au format XML à l’aide de balises XML. Cette seconde vous permet de spécifier des remarques distinctes pour un bref résumé, des remarques supplémentaires, de la documentation pour chaque paramètre et paramètre de type et les exceptions levées, ainsi qu’une description de la valeur de retour.

Voici un commentaire de documentation XML standard dans un fichier de signature :

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7101.fs)]

## <a name="recommended-tags"></a>Étiquettes recommandées

Si vous utilisez des balises XML, le tableau suivant décrit les balises externes reconnues dans les commentaires de code XML F #.

| Syntaxe de balise                                  | Description |
|---------------------------------------------|-----------|
| `<summary>`**_financière_**`</summary>`           | Spécifie que le *texte* est une brève description de l’élément de programme. La description correspond généralement à une ou deux phrases.|
| `<remarks>`**_financière_**`</remarks>`           | Spécifie que le *texte* contient des informations supplémentaires sur l’élément de programme.|
| `<param name="`**_nom_** `">` ** _Description_**`</param>` | Spécifie le nom et la description d’un paramètre de fonction ou de méthode.|
| `<typeparam name="`**_nom_** `">` ** _Description_**`</typeparam>` | Spécifie le nom et la description d’un paramètre de type.|
| `<returns>`**_financière_**`</returns>`           | Spécifie que le *texte* décrit la valeur de retour d’une fonction ou d’une méthode.|
| `<exception cref="`**_type_** `">` ** _Description_**`</exception>` |Spécifie le type d’exception qui peut être généré et les circonstances dans lesquelles il est levé.|
| `<seealso cref="`**_faire_**`"/>`      | Spécifie un lien Voir également vers la documentation d’un autre type. La *référence* est le nom tel qu’il apparaît dans le fichier de documentation XML. Consultez également les liens qui apparaissent généralement en bas d’une page de documentation.|

Le tableau suivant décrit les balises à utiliser dans les sections de Description :

| Syntaxe de balise                                | Description |
|-------------------------------------------|-------------|
| `<para>`**_financière_**`</para>`               | Spécifie un paragraphe de texte. Il est utilisé pour séparer le texte dans la balise **Notes** .|
| `<code>`**_financière_**`</code>`               | Spécifie que le *texte* est plusieurs lignes de code. Cette balise peut être utilisée par les générateurs de documentation pour afficher du texte dans une police appropriée pour le code.|
| `<paramref name="`**_nomme_**`"/>`         | Spécifie une référence à un paramètre dans le même commentaire de documentation.|
| `<typeparamref name="`**_nomme_**`"/>`     | Spécifie une référence à un paramètre de type dans le même commentaire de documentation.|
| `<c>`**_financière_**`</c>`                     | Spécifie que le *texte* est un code incorporé. Cette balise peut être utilisée par les générateurs de documentation pour afficher du texte dans une police appropriée pour le code.|
| `<see cref="`**_référence_** `">` ** _texte_**`</see>` | Spécifie un lien Inline vers un autre élément de programme. La *référence* est le nom tel qu’il apparaît dans le fichier de documentation XML. Le *texte* est le texte affiché dans le lien.|

### <a name="user-defined-tags"></a>Balises définies par l’utilisateur

Les balises précédentes représentent celles qui sont reconnues par le compilateur F # et les outils d’éditeur F # typiques. Toutefois, un utilisateur est libre de définir ses propres balises.
Des outils comme fsdocs prennent en charge les balises supplémentaires comme [\<namespacedoc>](https://github.com/fsharp/fslang-design/blob/master/tooling/FST-1031-xmldoc-extensions.md) .
Des outils de génération de documentation personnalisés ou internes peuvent également être utilisés avec les balises standard, et plusieurs formats de sortie, du format HTML au format PDF, peuvent être pris en charge.

## <a name="compile-time-checking"></a>Vérification au moment de la compilation

Lorsque `--warnon:3390` est activé, le compilateur vérifie la syntaxe du XML et les paramètres référencés dans les `<param>` `<paramref>` balises et.

## <a name="documenting-f-constructs"></a>Documentation des constructions F #

Les constructions F # telles que les modules, les membres, les cas d’Union et les champs d’enregistrement sont documentées par un `///` Commentaire immédiatement avant leur déclaration.
Si nécessaire, les constructeurs implicites des classes sont documentés en donnant un `///` commentaire avant la liste d’arguments. Exemple :

```fsharp
/// This is the type
type SomeType
      /// This is the implicit constructor
      (a: int, b: int) =

    /// This is the member
    member _.Sum() = a + b
```

## <a name="limitations"></a>Limites

Certaines fonctionnalités de la documentation XML en C# et d’autres langages .NET ne sont pas prises en charge en C#.

- En F #, les références croisées doivent utiliser la signature XML complète du symbole correspondant, par exemple `cref="T:System.Console"` .
  Les références croisées de style C# simples telles que `cref="Console"` ne sont pas élaborées vers des signatures XML complètes et ces éléments ne sont pas vérifiés par le compilateur F #. Certains outils de documentation peuvent autoriser l’utilisation de ces références croisées par le traitement suivant, mais les signatures complètes doivent être utilisées.
  
- Les balises ne `<include>` `<inheritdoc>` sont pas prises en charge par le compilateur F #. Aucune erreur n’est fournie si elles sont utilisées, mais elles sont simplement copiées dans le fichier de documentation généré sans affecter autrement la documentation générée.

- Les références croisées ne sont pas vérifiées par le compilateur F #, même quand `-warnon:3390` est utilisé.

- Les noms utilisés dans les balises `<typeparam>` et ne `<typeparamref>` sont pas vérifiés par le compilateur F #, même quand `--warnon:3390` est utilisé.

- Aucun avertissement n’est fourni si la documentation est manquante, même si `--warnon:3390` est utilisé.

## <a name="recommendations"></a>Recommandations

La documentation du code est recommandée pour de nombreuses raisons. Voici quelques-unes des meilleures pratiques, des scénarios de cas d’usage généraux et des éléments que vous devez connaître lorsque vous utilisez des balises de documentation XML dans votre code F #.

- Activez l’option `--warnon:3390` dans votre code pour vous assurer que la documentation XML est un fichier XML valide.

- Envisagez d’ajouter des fichiers de signature pour séparer les longs commentaires de documentation XML de votre implémentation.

- Par souci de cohérence, tous les types visibles publiquement et leurs membres doivent être documentés. Si vous devez le faire, faites-le complètement.

- Au minimum, les modules, les types et leurs membres doivent avoir un `///` commentaire ou une `<summary>` balise simple. Cela s’affiche dans une fenêtre d’info-bulle de saisie semi-automatique dans les outils d’édition F #.

- Le texte de la documentation doit être écrit à l’aide de phrases complètes se terminant par un point.

## <a name="see-also"></a>Voir aussi

- [Commentaires de documentation XML C# &#40;Guide de programmation du&#35; C&#41;](../../csharp/programming-guide/xmldoc/index.md).
- [Informations de référence sur le langage F #](index.md)
- [Options du compilateur](compiler-options.md)
