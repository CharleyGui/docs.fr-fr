---
title: Documentation de votre code avec des commentaires XML
description: Découvrez comment documenter votre code avec des commentaires de documentation XML et générer un fichier de documentation XML au moment de la compilation.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 91de11c610ea17999dabff6d0552de9440f532e6
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465297"
---
# <a name="document-your-code-with-xml-comments"></a>Documenter votre code avec des commentaires XML

Les commentaires de documentation XML sont un genre particulier de commentaire, ajouté au-dessus de la définition d’un type ou d’un membre défini par l’utilisateur.
Ils sont spéciaux, car ils peuvent être traités par le compilateur pour générer un fichier de documentation XML au moment de la compilation.
Le fichier XML généré par le compilateur peut être distribué avec votre assembly .NET afin que Visual Studio et d’autres IDE puissent utiliser IntelliSense pour afficher des informations rapides sur les types ou les membres. De plus, le fichier XML peut être exécuté par l’intermédiaire d’outils tels que [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) pour générer des sites web de références d’API.

Les commentaires de documentation XML, comme tous les autres commentaires, sont ignorés par le compilateur.

Vous pouvez générer le fichier XML au moment de la compilation en procédant comme suit :

- Si vous développez une application avec .NET Core à partir de la ligne de commande, vous pouvez ajouter un `GenerateDocumentationFile` élément à la `<PropertyGroup>` section de votre fichier projet. csproj. Vous pouvez également spécifier le chemin d’accès au fichier de documentation directement à l’aide de l' [ `DocumentationFile` élément](/visualstudio/msbuild/common-msbuild-project-properties). L’exemple suivant génère un fichier XML dans le répertoire du projet avec le même nom de fichier racine que l’assembly :

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```

   est équivalente à celle-ci :

   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- Si vous développez une application à l’aide de Visual Studio, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**. Dans la boîte de dialogue des propriétés, sélectionnez l’onglet **Générer**, puis cochez **Fichier de documentation XML**. Vous pouvez également changer l’emplacement dans lequel le compilateur écrit le fichier.

- Si vous compilez une application .NET à partir de la ligne de commande, ajoutez l' [option de compilateur-doc](language-reference/compiler-options/doc-compiler-option.md) lors de la compilation.  

Les commentaires de documentation XML utilisent des barres obliques triples (`///`) et le corps d’un commentaire au format XML. Par exemple :

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a>Procédure pas à pas

Passons en revue la documentation d’une bibliothèque mathématique très basique pour permettre aux nouveaux développeurs de comprendre et de contribuer facilement et aux développeurs tiers de les utiliser.

Voici le code de la bibliothèque mathématique simple :

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

L’exemple de bibliothèque prend en charge quatre opérations arithmétiques majeures ( `add` ,, `subtract` `multiply` et `divide` ) sur les `int` types de `double` données et.

Vous souhaitez maintenant être en mesure de créer un document de référence d’API à partir de votre code pour les développeurs tiers qui utilisent votre bibliothèque, mais n’ont pas accès au code source.
Comme nous l’avons déjà mentionné, vous pouvez pour cela utiliser les balises de documentation XML. Vous allez maintenant découvrir les balises XML standard prises en charge par le compilateur C#.

## \<summary>

La balise `<summary>` ajoute des informations succinctes relatives à un type ou un membre.
Je vais expliquer son utilisation en l’ajoutant à la définition de la classe `Math` et à la première méthode `Add`. N’hésitez pas à l’appliquer au reste de votre code.

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

La `<summary>` balise est importante et nous vous recommandons de l’inclure car son contenu est la principale source d’informations sur les types ou les membres dans IntelliSense ou un document de référence sur les API.

## \<remarks>

La balise `<remarks>` complète les informations relatives aux types ou aux membres fournies par la balise `<summary>`. Dans cet exemple, vous allez simplement l’ajouter à la classe.

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## \<returns>

La balise `<returns>` décrit la valeur de retour d’une déclaration de méthode.
Comme auparavant, l’exemple suivant illustre la balise `<returns>` sur la première méthode `Add`. Vous pouvez effectuer la même opération sur d’autres méthodes.

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## \<value>

La balise `<value>` est similaire à la balise `<returns>`, excepté que vous l’utilisez pour les propriétés.
En supposant que votre bibliothèque `Math` a une propriété statique appelée `PI`, voici comment utiliser cette balise :

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## \<example>

La balise `<example>` permet d’inclure un exemple de votre documentation XML.
Cela implique l’utilisation de la balise enfant `<code>`.

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

La balise `code` conserve les sauts de ligne et la mise en retrait pour les exemples plus longs.

## \<para>

La balise `<para>` permet de mettre en forme le contenu de sa balise parente. `<para>` est généralement utilisée dans une balise, telle que `<remarks>` ou `<returns>`, pour diviser du texte en paragraphes.
Vous pouvez mettre en forme le contenu de la balise `<remarks>` pour la définition de votre classe.

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## \<c>

Toujours concernant la mise en forme, vous utilisez la balise `<c>` pour le marquage d’une partie du texte comme code.
Elle est semblable à la balise `<code>`, mais inline. Elle est utile quand vous voulez afficher un exemple de code rapide comme partie du contenu d’une balise.
Mettons à jour la documentation de la classe `Math`.

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## \<exception>

En utilisant la balise `<exception>`, vous informez vos développeurs qu’une méthode peut lever des exceptions spécifiques.
Si vous examinez votre bibliothèque `Math`, vous pouvez voir que les deux méthodes `Add` lèvent une exception si une certaine condition est remplie. Il est toutefois moins évident de voir que la méthode `Divide` utilisée avec un entier lève également une exception si le paramètre `b` est égal à zéro. Ajoutez maintenant une documentation d’exception à cette méthode.

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

L’attribut `cref` référence une exception qui est disponible à partir de l’environnement de compilation actuel.
Il peut s’agir de tout type défini dans le projet ou dans un assembly référencé. Le compilateur émet un avertissement si sa valeur ne peut pas être résolue.

## \<see>

La balise `<see>` vous permet de créer un lien interactif vers une page de documentation pour un autre élément de code. Dans notre prochain exemple, nous allons créer un lien interactif entre les deux méthodes `Add`.

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

`cref` est un attribut **obligatoire** qui représente une référence à un type ou à ses membres et qui est disponible à partir de l’environnement de compilation actuel.
Il peut s’agir de tout type défini dans le projet ou dans un assembly référencé.

## \<seealso>

Vous pouvez utiliser la balise `<seealso>` de la même façon que la balise `<see>`. La seule différence est que son contenu est généralement placé dans une section "Voir aussi". Ici, nous allons ajouter une balise `seealso` sous la méthode `Add` utilisée avec un entier pour référencer d’autres méthodes de la classe qui acceptent des paramètres entiers :

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

L’attribut `cref` représente une référence à un type ou à ses membres et est disponible à partir de l’environnement de compilation actuel.
Il peut s’agir de tout type défini dans le projet ou dans un assembly référencé.

## \<param>

La balise `<param>` permet de décrire les paramètres d’une méthode. Voici un exemple de la méthode double `Add` : le paramètre que la balise décrit est spécifié dans l’attribut **Required** `name` .

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## \<typeparam>

Vous utilisez la balise `<typeparam>` exactement comme la balise `<param>`, mais pour permettre aux déclarations de types ou de méthodes génériques de décrire un paramètre générique.
Ajoutez une méthode générique rapide à votre classe `Math` pour vérifier si une quantité est supérieure à une autre.

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## \<paramref>

Alors que vous décrivez ce que fait une méthode dans ce qui pourrait être une balise `<summary>`, vous souhaiterez peut-être créer une référence à un paramètre. La balise `<paramref>` est idéale pour cette tâche précise. Mettons à jour le récapitulatif de notre méthode `Add` double. À l’instar de la `<param>` balise, le nom du paramètre est spécifié dans l’attribut **Required** `name` .

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## \<typeparamref>

Vous utilisez la balise `<typeparamref>` exactement comme la balise `<paramref>`, mais pour permettre aux déclarations de types ou de méthodes génériques de décrire un paramètre générique.
Vous pouvez utiliser la même méthode générique que celle créée précédemment.

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## \<list>

Vous utilisez la `<list>` balise pour mettre en forme les informations de documentation sous la forme d’une liste triée, d’une liste non triée ou d’une table. Créez une liste non triée de toutes les opérations mathématiques prises en charge par votre bibliothèque `Math`.

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

Vous pouvez créer une liste triée ou un tableau en remplaçant l’attribut `type` par `number` ou `table`, respectivement.

## \<inheritdoc>

Vous pouvez utiliser la `<inheritdoc>` balise pour hériter des commentaires XML des classes de base, des interfaces et des méthodes similaires. Cela élimine la copie et le collage indésirables de commentaires XML en double et conserve automatiquement les commentaires XML synchronisés.

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a>Assemblage

Si vous avez suivi ce didacticiel et appliqué les balises à votre code au besoin, votre code doit maintenant ressembler à ce qui suit :

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

À partir de votre code, vous pouvez générer un site web de documentation détaillée complet avec des références croisées interactives. Vous êtes maintenant confronté à un autre problème : votre code est devenu difficile à lire.
Avec toutes ces informations à parcourir, cela va être un cauchemar pour les développeurs qui veulent contribuer à ce code.
Heureusement, il existe une balise XML qui peut vous aider à gérer ce problème :

## \<include>

La balise `<include>` vous permet de faire référence à des commentaires se trouvant dans un fichier XML distinct et décrivant les types et les membres de votre code source au lieu de placer des commentaires de documentation directement dans votre fichier de code source.

Vous allez maintenant déplacer toutes vos balises XML dans un fichier XML distinct nommé `docs.xml`. Vous pouvez nommer ce fichier comme vous le souhaitez.

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

Dans le code XML ci-dessus, les commentaires de documentation de chaque membre apparaissent directement dans une balise nommée en fonction de ce qu’il fait. Vous pouvez choisir votre propre stratégie.
Maintenant que vous avez vos commentaires XML dans un fichier distinct, voyons comment votre code peut être rendu plus lisible à l’aide de la balise `<include>` :

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

Et voilà : notre code est à nouveau lisible, et aucune information de documentation n’a été perdue.

L’attribut `file` représente le nom du fichier XML contenant la documentation.

L’attribut `path` représente une requête [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) au `tag name` présent dans le `file` spécifié.

L’attribut `name` représente le spécificateur de nom dans la balise qui précède les commentaires.

L' `id` attribut, qui peut être utilisé à la place de `name` , représente l’ID de la balise qui précède les commentaires.

### <a name="user-defined-tags"></a>Balises définies par l’utilisateur

Toutes les balises décrites ci-dessus représentent celles qui sont reconnues par le compilateur C#. Toutefois, un utilisateur est libre de définir ses propres balises.
Les outils tels que Sandcastle apportent la prise en charge de balises supplémentaires comme [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) et [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) , et prennent même en charge la [documentation des espaces de noms](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).
Des outils de génération de documentation personnalisés ou internes peuvent également être utilisés avec les balises standard, et plusieurs formats de sortie, du format HTML au format PDF, peuvent être pris en charge.

## <a name="recommendations"></a>Recommandations

La documentation du code est recommandée pour de nombreuses raisons. Voici quelques bonnes pratiques, des scénarios de cas d’usage généraux et des éléments que vous devez connaître quand vous utilisez des balises de documentation XML dans votre code C#.

- Par souci de cohérence, tous les types visibles publiquement et leurs membres doivent être documentés. Si vous devez le faire, faites-le complètement.
- Les membres privés peuvent également être documentés à l’aide de commentaires XML. Toutefois, cela expose le fonctionnement interne (potentiellement confidentiel) de votre bibliothèque.
- Au minimum, les types et leurs membres doivent avoir une balise `<summary>`, car son contenu est nécessaire pour IntelliSense.
- Le texte de la documentation doit être écrit à l’aide de phrases complètes se terminant par un point.
- Les classes partielles sont entièrement prises en charge, et les informations de documentation seront concaténées dans une seule entrée pour ce type.
- Le compilateur vérifie la syntaxe des `<exception>` `<include>` balises,,,, `<param>` `<see>` `<seealso>` et `<typeparam>` .
- Le compilateur valide les paramètres qui contiennent des chemins de fichiers et des références à d’autres parties du code.

## <a name="see-also"></a>Voir aussi

- [Commentaires de documentation XML (Guide de programmation C#)](programming-guide/xmldoc/index.md)
- [Balises recommandées pour les commentaires de documentation (Guide de programmation C#)](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
