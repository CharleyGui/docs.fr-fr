---
title:
- TITRE DE L’ARTICLE
description: ''
author:
- GITHUB USERNAME
ms.author:
- MICROSOFT ALIAS OF INTERNAL OWNER
ms.date:
- CREATION/UPDATE DATE - mm/dd/yyyy
ms.topic:
- TOPIC TYPE
ms.prod:
- PRODUCT VALUE
helpviewer_keywords:
- OFFLINE BOOK INDEX ENTRIES
ms.openlocfilehash: 0e8548745768bc9137e8fc76f86fc9fc7982b8de
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "68616349"
---
# <a name="metadata-and-markdown-template"></a>Métadonnées et modèle Markdown

Ce modèle dotnet/docs contient des exemples de syntaxe Markdown ainsi que des conseils sur la définition des métadonnées. Pour en tirer le meilleur parti, vous devez afficher à la fois le [Markdown brut](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) et la [vue rendue](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (par exemple, le Markdown brut affiche le bloc de métadonnées contrairement à la vue rendue).

Quand vous créez un fichier Markdown, vous devez copier ce modèle dans un nouveau fichier, remplir les métadonnées comme indiqué ci-dessous, définir le titre de l’article comme titre H1 ci-dessus et supprimer le contenu.

## <a name="metadata"></a>Metadata

L’intégralité du bloc de métadonnées se situe au-dessus (dans le [Markdown brut](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)) et est divisé en champs obligatoires et champs facultatifs. Quelques remarques importantes :

- Vous **devez** ajouter un espace entre le signe deux-points (:) et la valeur d’un élément de métadonnées.
- Si un élément de métadonnées facultatif n’a pas de valeur, placez l’élément en commentaire avec un signe # ou supprimez-le (ne le laissez pas vide ou n’utilisez pas « na »). Si vous ajoutez une valeur à un élément qui a été placé en commentaire, veillez à supprimer le signe #.
- Des signes deux-points dans une valeur (par exemple, un titre) interrompent l’analyseur de métadonnées. Dans ce cas, entourez le titre de guillemets doubles (par exemple, `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).
- **title** : Apparaît dans les résultats du moteur de recherche. Le titre ne doit pas être identique au titre H1 et il doit contenir au maximum 60 caractères.
- **description** : Résume le contenu de l’article. Il est généralement affiché dans la page des résultats de la recherche, mais il n’est pas utilisé pour le classement de la recherche. Sa longueur doit être de 115 à 145 caractères, espaces compris.
- **author** et **ms.author** : Le champ author doit contenir le **nom d’utilisateur GitHub** de l’auteur, et non pas son alias.  Le champ **ms.author** doit de son côté contenir un alias Microsoft et indiquer la personne responsable de la maintenance de l’article.
- **ms.topic** : Type de rubrique. La valeur la plus courante est `conceptual` et elle est définie à un niveau global. Les autres valeurs courantes utilisées sont `tutorial`, `overview` et `reference`.
- **ms.devlang** définit le filtre de langage affiché pour la rubrique. Vous pouvez voir une liste des valeurs prises en charge dans la section [Langages pris en charge](#supported-languages). Ce champ doit être défini seulement quand plusieurs langages de programmation sont couverts dans la rubrique. En règle générale, nous utilisons seulement `csharp`, `vb`, `fsharp` et `cpp` pour cette valeur dans notre contenu.
- **ms.prod** : Identification du produit utilisée à des fins de BI. Elles sont généralement définies à un niveau global, de sorte qu’elles n’apparaissent généralement pas dans le bloc de métadonnées de chaque article.
- **ms.technology** : Classification BI supplémentaire. Voici quelques-unes des valeurs prises en charge : `devlang-csharp` pour les rubriques C#, `devlang-fsharp` pour les rubriques F# et `devlang-visual-basic` pour les rubriques VB. Pour les autres guides, les valeurs varient : demandez à un membre de l’équipe de vous aider.
- **ms.date** : Date au format JJ/MM/AAAA. Affiché sur la page publiée pour indiquer la dernière fois que l’article a été modifié de façon substantielle ou garanti « actualisé » (c’est-à-dire que l’article a été révisé et qu’il est considéré comme étant à jour).
- **helpviewer_keywords** : Les entrées sont utilisées pour l’index des livres hors connexion (fonctionnalité dans Visual Studio).
- **f1_keywords** : Connecte l’article à la touche F1 (fonctionnalité dans Visual Studio).

## <a name="basic-markdown-gfm-and-special-characters"></a>Markdown de base, GFM et caractères spéciaux

Toute la syntaxe Markdown de base et GFM (GitHub Flavored Markdown) est prise en charge. Pour plus d’informations sur cette syntaxe, consultez :

- [Syntaxe Markdown de base](https://daringfireball.net/projects/markdown/syntax)
- [Documentation GFM](https://guides.github.com/features/mastering-markdown)

Markdown utilise des caractères spéciaux tels que \*, \` et \# pour la mise en forme. Si vous souhaitez inclure l’un de ces caractères dans votre contenu, vous devez effectuer l’une des deux opérations suivantes :

- Placer une barre oblique inverse devant le caractère spécial pour l’« échappement » de ce caractère (par exemple, `\*` pour un \*)
- Utiliser le [code d’entité HTML](https://www.ascii.cl/htmlcodes.htm) pour le caractère (par exemple, `&#42;` pour un &#42;).

## <a name="file-name"></a>Nom de fichier

Les noms des fichiers utilisent les règles suivantes :

* Ils contiennent uniquement des lettres minuscules, des chiffres et des traits d’union.
* Aucun espace ni caractère de ponctuation. Utilisez les traits d’union pour séparer les mots et les nombres dans le nom de fichier.
* Utilisez des verbes d’actions spécifiques, tels que développer, acheter, générer, dépanner. Pas de substantif.
* Pas de mot trop court ; évitez un, et, le, en, ou, etc.
* Le nom doit être au format Markdown et utiliser l’extension de fichier .md.
* Privilégiez des noms de fichiers courts. Ils font partie de l’URL pour vos articles.

## <a name="headings"></a>Titres

Utilisez la mise en majuscules comme pour les phrases. Mettez toujours en majuscules :

- Le premier mot d’un titre.
- Le mot qui suit le signe deux-points dans un titre ou un en-tête (par exemple, « Comment : Trier un tableau »).

Les titres doivent être créés à l’aide du style atx, c’est-à-dire en utilisant 1 à 6 caractères de hachage (#) au début de la ligne pour indiquer un titre, correspondant aux niveaux de titres HTML H1 à H6. Des exemples de titres de premier et second niveau sont utilisés ci-dessus.

Il ne **doit** exister qu’un seul titre de premier niveau (H1) dans votre rubrique, qui sera affiché comme titre sur la page.

Si votre titre se termine par un caractère `#`, vous devez ajouter un autre caractère `#` à la fin pour que le titre soit correctement rendu. Par exemple, `# Async Programming in F# #`.

Les titres de second niveau génèrent la table des matières sur la page qui s’affiche dans la section « Dans cet article » en dessous du titre sur la page.

### <a name="third-level-heading"></a>Titre de troisième niveau
#### <a name="fourth-level-heading"></a>Titre de quatrième niveau
##### <a name="fifth-level-heading"></a>Titre de cinquième niveau
###### <a name="sixth-level-heading"></a>Titre de sixième niveau

## <a name="text-styling"></a>Style du texte

*Italique* À utiliser pour les fichiers, dossiers, chemins (pour les éléments longs, placés sur une ligne distincte) et les nouveaux termes.

**Gras** À utiliser pour les éléments d’interface utilisateur.

`Code` À utiliser pour le code inline, les mots clés du langage, les noms de package NuGet, les commandes de ligne de commande, les noms des tables et des colonnes de base de données ainsi que les URL sur lesquelles les lecteurs ne doivent pas pouvoir cliquer.

## <a name="links"></a>Liens

### <a name="internal-links"></a>Liens internes

Pour établir un lien à un en-tête dans le même fichier Markdown (également appelés liens d’ancrage), vous devrez trouver l’ID de l’en-tête en question. Pour vérifier l’ID, affichez la source de l’article rendu, recherchez l’ID de l’en-tête (par exemple, `id="blockquote"`) et établissez le lien avec # + ID (par exemple, `#blockquote`).
L’ID est généré automatiquement en fonction du texte d’en-tête. Ainsi, par exemple, étant donné une section unique nommée `## Step 2`, l’ID ressemblerait à `id="step-2"`.

- Exemple : `[Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier)` produit [Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier) (Déclarer des blocs inline avec un identificateur du langage).

Pour établir un lien à un fichier Markdown dans le même dépôt, utilisez des [liens relatifs](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), dont « .md » à la fin du nom de fichier.

- Exemple : `[Readme file](../README.md)` produit [Readme file](../README.md) (Fichier Lisez-moi). (Notez que les liens sont sensibles à la casse.)
- Exemple : `[Welcome to .NET](../docs/welcome.md)` produit [Welcome to .NET](../docs/welcome.md) (Bienvenue dans .NET).

Pour établir un lien à un en-tête d’un fichier Markdown dans le même dépôt, utilisez la liaison relative + la liaison hashtag.

- Exemple : `[.NET Community](../docs/welcome.md#open-source)` produit [.NET Community](../docs/welcome.md#open-source) (Communauté .NET).

Dans la plupart des cas, nous utilisons les liens relatifs et nous n’encourageons pas l’utilisation de `~/` dans les liens, car les liens relatifs sont résolus dans la source sur GitHub. Cependant, chaque fois que nous utilisons un lien vers un fichier dans un dépôt dépendant, nous utilisons le caractère `~/` pour fournir le chemin. Comme les fichiers dans les dépôts dépendants se trouvent à un emplacement différent dans GitHub, les liens ne sont pas correctement résolus avec les liens relatifs, quelle que soit la façon dont ils ont été écrits.

La spécification du langage C# et la spécification du langage Visual Basic sont incluses dans les documents .NET grâce à l’inclusion de la source des dépôts du langage. Les sources Markdown sont gérées dans les dépôts [csharplang](https://github.com/dotnet/csharplang) et [visual basic](https://github.com/dotnet/vblang).

Les liens vers la spécification doivent pointer vers les répertoires sources où ces spécifications sont incluses. Pour C#, il s’agit de **~/_csharplang/spec** et pour VB, il s’agit de **~/_vblang/spec**.

- Exemple : `[C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions)` produit [C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions) (Expressions de requête de requête C#).

### <a name="external-links"></a>Liens externes

Pour établir un lien à un fichier externe, utilisez l’URL complète comme lien.

- Exemple : `[GitHub](https://www.github.com)` produit [GitHub](https://www.github.com).

Si une URL apparaît dans un fichier Markdown, elle est transformée en lien interactif.

- Exemple : `<https://www.github.com>` produit <https://www.github.com>.

Préférez le protocole `https` pour les liens externes. Utilisez des liens `http` seulement pour les sites qui ne prennent pas en charge `https`.

### <a name="links-to-apis"></a>Liens vers des API

Le système de génération a certaines extensions qui permettent d’établir des liens à des API .NET sans avoir à utiliser de liens externes.
Lors de la liaison à une API, vous pouvez utiliser son identificateur unique (UID) qui est généré automatiquement à partir du code source.

L’UID équivaut au nom complet du type et du membre.

Si vous ajoutez un caractère \* (ou %2A) après l’UID, le lien représente alors la page de surcharge et non pas une API spécifique. Par exemple, vous pouvez utiliser cela quand vous voulez créer un lien vers la page [List\<T>.BinarySearch Method](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch) de façon générique au lieu d’une surcharge spécifique comme [List\<T>.BinarySearch(T, IComparer\<T>)](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch#System_Collections_Generic_List_1_BinarySearch__0_). Vous pouvez également utiliser \* pour établir un lien vers une page de membre quand le membre n’est pas surchargé : ceci vous évite de devoir inclure la liste des paramètres dans l’UID.

Pour établir un lien vers une surcharge de méthode spécifique, vous devez inclure le nom complet du type de chacun des paramètres de la méthode. Par exemple, \<xref:System.DateTime.ToString> établit un lien vers la méthode [DateTime.ToString](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString) sans paramètres, alors que \<xref:System.DateTime.ToString(System.String,System.IFormatProvider)> établit un lien vers la méthode [DateTime.ToString(String,IFormatProvider)](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString_System_String_System_IFormatProvider_). Vous pouvez rechercher les UID d’un membre surchargé particulier à partir de `https://xref.docs.microsoft.com/autocomplete`. La chaîne de requête « ?text= *\<nom_type_membre>*  » identifie le type ou le membre dont vous voulez voir les UID. Par exemple, `https://xref.docs.microsoft.com/autocomplete?text=string.format` récupère les surcharges de [String.Format](https://docs.microsoft.com/dotnet/api/system.string.format).

Pour établir un lien vers un type générique, comme [System.Collections.Generic.List\<T>](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1), vous utilisez le caractère ` (%60) suivi du nombre de paramètres de type générique. Par exemple, \<xref:System.Nullable%601> établit un lien vers le type [System.Nullable\<T>](https://docs.microsoft.com/dotnet/api/system.nullable-1), alors que \<xref:System.Func%602> établit un lien vers le délégué [System.Func\<T,TResult>](https://docs.microsoft.com/dotnet/api/system.func-2).

Vous pouvez utiliser l’une des syntaxes suivantes :

1. Liaison automatique : `<xref:UID>` ou `<xref:UID?displayProperty=nameWithType>`

   Le paramètre de requête `displayProperty` produit un texte de lien complet. Par défaut, le texte du lien affiche seulement le nom du membre ou du type.

2. Lien Markdown : `[link text](xref:UID)`

   À utiliser quand vous voulez personnaliser le texte du lien affiché.

Exemples :

- `<xref:System.String>` est rendu sous forme de [String](https://docs.microsoft.com/dotnet/api/system.string)
- `<xref:System.String?displayProperty=nameWithType>` est rendu sous forme de [System.String](https://docs.microsoft.com/dotnet/api/system.string)
- `[String class](xref:System.String)` est rendu sous forme de [classe String](https://docs.microsoft.com/dotnet/api/system.string)

Pour plus d’informations sur l’utilisation de cette notation, consultez [Utilisation de renvois](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference).

Vous pouvez trouver l’UID de deux façons :

- Affichez la source de la page de l’API vers laquelle vous voulez établir un lien et recherchez la valeur de ms.assetid. Notez que les valeurs de surcharge individuelles ne sont pas affichées dans la source.
- Utilisez l’outil suivant pour rechercher les UID : https://xref.docs.microsoft.com/autocomplete?text=tostring (remplacez tostring par des parties du nom de l’API que vous recherchez). L’outil recherche le paramètre de requête `text` fourni dans toutes les parties de l’UID. Par exemple, vous pouvez rechercher le nom de membre (ToString), le nom de membre partiel (ToStri), le nom de type et de membre (Double.ToString), etc.

Quand l’UID contient les caractères spéciaux \`, \# ou \*, la valeur de l’UID doit être encodée au format HTML, respectivement en `%60`, `%23` et `%2A`. Vous verrez parfois des parenthèses encodées, mais ce n’est pas obligatoire.

Exemples :

- System.Threading.Tasks.Task\`1 devient `System.Threading.Tasks.Task%601`
- System.Exception.\#ctor devient `System.Exception.%23ctor`
- System.Lazy\`1.\#ctor(System.Threading.LazyThreadSafetyMode) devient `System.Lazy%601.%23ctor%28System.Threading.LazyThreadSafetyMode%29`

## <a name="lists"></a>Listes

### <a name="ordered-lists"></a>Listes triées

1. This
1. Is
1. An
1. Ordered
1. List

#### <a name="ordered-list-with-an-embedded-list"></a>Liste triée avec une liste incorporée

1. Here
1. comes
1. an
1. embedded
    1. Miss Scarlett
    1. Professor Plum
1. ordered
1. list

### <a name="unordered-lists"></a>Listes non triées

- This
- est
- a
- bulleted
- list

#### <a name="unordered-list-with-an-embedded-list"></a>Liste non triée avec une liste incorporée

- This
- bulleted
- list
  - Mrs. Peacock
  - Mr. Green
- contains
- other
  1. Colonel Mustard
  1. Mrs. White
- lists

## <a name="horizontal-rule"></a>Ligne horizontale

---

## <a name="tables"></a>Tables

| Tables        | Sont           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 est      | alignée à droite | 1 600 $ |
| col 2 est      | centrée      |   12 $ |
| col 1 est la valeur par défaut | alignée à gauche     |    1 $ |

Vous pouvez utiliser un [outil de génération de table Markdown](https://www.tablesgenerator.com/markdown_tables) pour les créer plus facilement.

## <a name="code"></a>Code

La meilleure façon d’inclure du code consiste à ajouter des extraits à partir d’un exemple fonctionnel. Créez votre exemple en suivant les instructions du [guide de contribution](../CONTRIBUTING.md#contributing-to-samples).

Vous pouvez inclure le code avec la syntaxe suivante :

```markdown
[!code-<language>[<name>](<pathToFile><queryoption><queryoptionvalue>)]
```

* `-<language>` (*facultatif* mais *recommandé*)
  * Langage de l’extrait de code référencé. Pour obtenir la liste des valeurs prises en charge, consultez [Langages pris en charge](#supported-languages).

* `<name>` (*facultatif*)
  * Nom pour l’extrait de code. Il n’a aucun impact sur le code HTML de sortie, mais vous pouvez l’utiliser pour améliorer la lisibilité de votre source Markdown.

* `<pathToFile>` (*obligatoire*)
  * Chemin relatif dans le système de fichiers qui indique le fichier de l’extrait de code à référencer.

* `<queryoption>` et `<queryoptionvalue>` (*facultatif*)
  * Utilisés ensemble pour spécifier la façon dont le code doit être récupéré à partir du fichier :
    * `#` :  `#L{startlinenumber}-L{endlinenumber}` (plage de lignes) *ou* `#{tagname}` (nom de l’étiquette).
    Nous déconseillons d’utiliser les numéros de ligne, car ceux-ci sont très instables. Le nom d’étiquette est le meilleur moyen de référencer des extraits de code.
    * `range`: `?range=1,3-5` Une plage de lignes. Cet exemple inclut les lignes 1, 3, 4 et 5.
    * `dedent`: `?dedent=8` Désindente les lignes d’un certain nombre d’espaces ; dans ce cas, de 8 espaces. Ceci peut être combiné avec `range` et d’autres options de requête qui sélectionnent un sous-ensemble des lignes d’un fichier.
    * `outdent`: `?outdent=8` Inverse l’indentation des lignes d’un certain nombre d’espaces ; dans ce cas, de 8 espaces. Ceci peut être combiné avec `range` et d’autres options de requête qui sélectionnent un sous-ensemble des lignes d’un fichier.

Nous vous recommandons d’utiliser l’option du nom d’étiquette dans la mesure du possible. Le nom d’étiquette est le nom d’une région ou d’un commentaire du code au format `Snippettagname` présent dans le code source. L’exemple suivant montre comment référencer le nom d’étiquette `1` :

```markdown
[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]
```

Vous pouvez voir comment les étiquettes d’extrait de code sont structurées dans [ce fichier source](https://github.com/dotnet/samples/blob/master/snippets/csharp/language-reference/keywords/throw/throw-1.cs). Pour plus d’informations sur la représentation des noms d’étiquette dans les fichiers sources d’extraits de code par langage, consultez les [Instructions pour DocFX](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#tag-name-representation-in-code-snippet-source-file).

L’ajout d’extraits de programmes complets garantit que tout le code s’exécute via notre système d’intégration continue. Toutefois, si vous avez besoin d’afficher un élément qui entraîne des erreurs lors de la compilation ou de l’exécution, vous pouvez utiliser des blocs de code en ligne.

### <a name="inline-code-blocks-with-language-identifier"></a>Blocs de code en ligne avec identificateur de langage

Utilisez trois accents graves (\`\`\`) + un ID de langage pour appliquer un codage en couleurs spécifique au langage à un bloc de code. Voici la liste des langages pris en charge montrant l’étiquette Markdown pour chaque ID de langage.

#### <a name="supported-languages"></a>Langages pris en charge

|Name|Étiquette Markdown|
|-----|-------|
|ASP.NET avec C#|aspx-csharp|
|ASP.NET avec VB|aspx-vb|
|D’Azure CLI|azurecli|
|AzCopy|azcopy|
|C++|cpp|
|C#|csharp|
|C# dans un navigateur|csharp-interactive|
|Console|console|
|F#|fsharp|
|Java|java|
|JavaScript|javascript|
|JSON|json|
|NodeJS|nodejs|
|Objective-C|objc|
|PHP|php|
|PowerShell|powershell|
|Python|python|
|Ruby|ruby|
|SQL|sql|
|Swift|swift|
|VB|vb|
|XAML|xaml|
|XML|xml|

Le nom `csharp-interactive` spécifie le langage C# et la possibilité d’exécuter les exemples à partir du navigateur. Ces extraits de code sont compilés et exécutés dans un conteneur Docker, et les résultats de l’exécution de ce programme sont affichés dans la fenêtre du navigateur de l’utilisateur.

Voici quelques exemples de blocs de code utilisant les ID de langage pour C# (\`\`\`csharp), Python (\`\`\`python) et PowerShell (\`\`\`powershell).

##### <a name="c9839"></a>C&#9839;

```csharp
using System;
namespace HelloWorld
{
    class Hello
    {
        static void Main()
        {
            Console.WriteLine("Hello World!");

            // Keep the console window open in debug mode.
            Console.WriteLine("Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

#### <a name="python"></a>Python

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```

#### <a name="powershell"></a>PowerShell

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a>Bloc de code générique

Utilisez trois accents graves (&#96;&#96;&#96;) pour le codage de bloc de code générique.

> L’approche recommandée consiste à utiliser des blocs de code avec les identificateurs de langage, comme expliqué dans la section précédente, pour garantir la coloration syntaxique appropriée sur le site de documentation. Utilisez des blocs de code générique uniquement si nécessaire.

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

## <a name="blockquotes"></a>Éléments blockquote

> La sécheresse durait maintenant depuis dix millions d’années et le règne des terribles lézards avait depuis longtemps pris fin. Ici, à l’équateur, sur le continent qui s’appellerait un jour l’Afrique, la lutte pour l’existence avait atteint un nouveau sommet dans la férocité, et le vainqueur n’était pas encore connu. Dans ce territoire aride et désolé, seul le plus petit, le plus rapide ou le plus puissant pouvait croître et espérer survivre.

## <a name="images"></a>Images

### <a name="static-image-or-animated-gif"></a>Image statique ou GIF animée

```markdown
![this is the alt text](../images/Logo_DotNet.png)
```

![il s’agit du texte de remplacement](../images/Logo_DotNet.png)

### <a name="linked-image"></a>Image liée

```markdown
[![alt text for linked image](../images/Logo_DotNet.png)](https://dot.net)
```

[![texte de remplacement pour l’image liée](../images/Logo_DotNet.png)](https://dot.net)

## <a name="videos"></a>Vidéos

Actuellement, vous pouvez incorporer des vidéos Channel 9 et YouTube avec la syntaxe suivante :

### <a name="channel-9"></a>Channel 9

```markdown
> [!VIDEO <channel9_video_link>]
```

Pour obtenir l’URL correcte de la vidéo, sélectionnez l’onglet **Incorporer** sous la trame vidéo, puis copiez l’URL à partir de l’élément `<iframe>`. Par exemple :

```markdown
> [!VIDEO https://channel9.msdn.com/Blogs/dotnet/NET-Core-20-Released/player]
```

### <a name="youtube"></a>YouTube

Pour obtenir l’URL correcte de la vidéo, cliquez avec le bouton droit sur la vidéo, sélectionnez **Copier le code incorporé**, puis copiez l’URL à partir de l’élément `<iframe>`.

```markdown
> [!VIDEO <youtube_video_link>]
```

Par exemple :

```markdown
> [!VIDEO https://www.youtube.com/embed/Q2mMbjw6cLA]
```

## <a name="docsmicrosoft-extensions"></a>extensions docs.microsoft

docs.microsoft fournit quelques extensions supplémentaires à GitHub Flavored Markdown.

### <a name="alerts"></a>Alertes

Il est important d’utiliser les styles d’alerte suivants pour un rendu avec le style approprié sur le site de documentation. Toutefois, le moteur de rendu sur GitHub ne les différencie pas.

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

Et tous seront rendus comme ceci : ![Styles d’alertes](../images/alerts.png)

### <a name="includes"></a>Inclut

Vous pouvez incorporer le Markdown d’un fichier dans un autre en utilisant une instruction include.

[!INCLUDE[sample include file](../includes/sampleinclude.md)]

### <a name="checked-lists"></a>Listes cochées

Un style personnalisé est disponible pour les listes. Vous pouvez restituer des listes avec des coches vertes.

> [!div class="checklist"]
> * Créer une application .NET Core
> * Ajouter une référence au package Microsoft.XmlSerializer.Generator
> * Modifier votre fichier MyApp.csproj pour ajouter des dépendances
> * Ajouter une classe et un XmlSerializer
> * Générer et exécuter l’application

Vous pouvez voir un exemple de listes cochées dans action dans les [documents .NET Core](https://docs.microsoft.com/dotnet/core/additional-tools/xml-serializer-generator).

### <a name="buttons"></a>Boutons

> [!div class="button"]
> [Liens de boutons](../docs/core/index.md)

Vous pouvez voir un exemple de boutons en action dans les [documents Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio#step-2---download-visual-studio).

### <a name="selectors"></a>Sélecteurs

> [!div class="op_single_selector"]
- [macOS](../docs/core/tutorials/using-on-macos.md)
- [Fenêtres](../docs/core/tutorials/with-visual-studio.md)

Vous pouvez voir un exemple de sélecteurs en action dans les [documents Azure](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-classic).

### <a name="step-by-steps"></a>Procédures détaillées

>[!div class="step-by-step"]
>[Précédent](../docs/csharp/expression-trees-interpreting.md)
>[Suivant](../docs/csharp/expression-trees-translating.md)

Vous pouvez voir un exemple de procédures pas à pas en action dans le [Guide C#](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/program-structure).
