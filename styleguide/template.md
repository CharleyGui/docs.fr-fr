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
# <a name="metadata-and-markdown-template"></a><span data-ttu-id="24327-102">Métadonnées et modèle Markdown</span><span class="sxs-lookup"><span data-stu-id="24327-102">Metadata and Markdown Template</span></span>

<span data-ttu-id="24327-103">Ce modèle dotnet/docs contient des exemples de syntaxe Markdown ainsi que des conseils sur la définition des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="24327-103">This dotnet/docs template contains examples of Markdown syntax, as well as guidance on setting the metadata.</span></span> <span data-ttu-id="24327-104">Pour en tirer le meilleur parti, vous devez afficher à la fois le [Markdown brut](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) et la [vue rendue](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (par exemple, le Markdown brut affiche le bloc de métadonnées contrairement à la vue rendue).</span><span class="sxs-lookup"><span data-stu-id="24327-104">To get the most of it, you must view both the [raw Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md) and the [rendered view](https://github.com/dotnet/docs/blob/master/styleguide/template.md) (for instance, the raw Markdown shows the metadata block, while the rendered view does not).</span></span>

<span data-ttu-id="24327-105">Quand vous créez un fichier Markdown, vous devez copier ce modèle dans un nouveau fichier, remplir les métadonnées comme indiqué ci-dessous, définir le titre de l’article comme titre H1 ci-dessus et supprimer le contenu.</span><span class="sxs-lookup"><span data-stu-id="24327-105">When creating a Markdown file, you should copy this template to a new file, fill out the metadata as specified below, set the H1 heading above to the title of the article, and delete the content.</span></span>

## <a name="metadata"></a><span data-ttu-id="24327-106">Metadata</span><span class="sxs-lookup"><span data-stu-id="24327-106">Metadata</span></span>

<span data-ttu-id="24327-107">L’intégralité du bloc de métadonnées se situe au-dessus (dans le [Markdown brut](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)) et est divisé en champs obligatoires et champs facultatifs.</span><span class="sxs-lookup"><span data-stu-id="24327-107">The full metadata block is above (in the [raw Markdown](https://raw.githubusercontent.com/dotnet/docs/master/styleguide/template.md)), divided into required fields and optional fields.</span></span> <span data-ttu-id="24327-108">Quelques remarques importantes :</span><span class="sxs-lookup"><span data-stu-id="24327-108">Some key notes:</span></span>

- <span data-ttu-id="24327-109">Vous **devez** ajouter un espace entre le signe deux-points (:) et la valeur d’un élément de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="24327-109">You **must** have a space between the colon (:) and the value for a metadata element.</span></span>
- <span data-ttu-id="24327-110">Si un élément de métadonnées facultatif n’a pas de valeur, placez l’élément en commentaire avec un signe # ou supprimez-le (ne le laissez pas vide ou n’utilisez pas « na »).</span><span class="sxs-lookup"><span data-stu-id="24327-110">If an optional metadata element doesn't have a value, comment out the element with a # or remove it (don't leave it blank or use "na").</span></span> <span data-ttu-id="24327-111">Si vous ajoutez une valeur à un élément qui a été placé en commentaire, veillez à supprimer le signe #.</span><span class="sxs-lookup"><span data-stu-id="24327-111">If you're adding a value to an element that was commented out, be sure to remove the #.</span></span>
- <span data-ttu-id="24327-112">Des signes deux-points dans une valeur (par exemple, un titre) interrompent l’analyseur de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="24327-112">Colons in a value (for example, a title) break the metadata parser.</span></span> <span data-ttu-id="24327-113">Dans ce cas, entourez le titre de guillemets doubles (par exemple, `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).</span><span class="sxs-lookup"><span data-stu-id="24327-113">In this case, surround the title with double quotes (for example, `title: "Writing .NET Core console apps: An advanced step-by-step guide"`).</span></span>
- <span data-ttu-id="24327-114">**title** : Apparaît dans les résultats du moteur de recherche.</span><span class="sxs-lookup"><span data-stu-id="24327-114">**title**: Appears in search engine results.</span></span> <span data-ttu-id="24327-115">Le titre ne doit pas être identique au titre H1 et il doit contenir au maximum 60 caractères.</span><span class="sxs-lookup"><span data-stu-id="24327-115">The title shouldn't be identical to the title in your H1 heading, and it should contain 60 characters or less.</span></span>
- <span data-ttu-id="24327-116">**description** : Résume le contenu de l’article.</span><span class="sxs-lookup"><span data-stu-id="24327-116">**description**: Summarizes the content of the article.</span></span> <span data-ttu-id="24327-117">Il est généralement affiché dans la page des résultats de la recherche, mais il n’est pas utilisé pour le classement de la recherche.</span><span class="sxs-lookup"><span data-stu-id="24327-117">It's usually shown in the search results page, but it isn't used for search ranking.</span></span> <span data-ttu-id="24327-118">Sa longueur doit être de 115 à 145 caractères, espaces compris.</span><span class="sxs-lookup"><span data-stu-id="24327-118">Its length should be 115-145 characters including spaces.</span></span>
- <span data-ttu-id="24327-119">**author** et **ms.author** : Le champ author doit contenir le **nom d’utilisateur GitHub** de l’auteur, et non pas son alias.</span><span class="sxs-lookup"><span data-stu-id="24327-119">**author** and **ms.author**: The author field should contain the **GitHub username** of the author, not his/her alias.</span></span>  <span data-ttu-id="24327-120">Le champ **ms.author** doit de son côté contenir un alias Microsoft et indiquer la personne responsable de la maintenance de l’article.</span><span class="sxs-lookup"><span data-stu-id="24327-120">The **ms.author** field, on the other hand, should contain a Microsoft alias and indicates the person responsible for maintaining the article.</span></span>
- <span data-ttu-id="24327-121">**ms.topic** : Type de rubrique.</span><span class="sxs-lookup"><span data-stu-id="24327-121">**ms.topic**: The topic type.</span></span> <span data-ttu-id="24327-122">La valeur la plus courante est `conceptual` et elle est définie à un niveau global.</span><span class="sxs-lookup"><span data-stu-id="24327-122">The most common value is `conceptual` and is set at a global level.</span></span> <span data-ttu-id="24327-123">Les autres valeurs courantes utilisées sont `tutorial`, `overview` et `reference`.</span><span class="sxs-lookup"><span data-stu-id="24327-123">Other common values used are `tutorial`, `overview`, and `reference`.</span></span>
- <span data-ttu-id="24327-124">**ms.devlang** définit le filtre de langage affiché pour la rubrique.</span><span class="sxs-lookup"><span data-stu-id="24327-124">**ms.devlang** defines the language filter displayed for the topic.</span></span> <span data-ttu-id="24327-125">Vous pouvez voir une liste des valeurs prises en charge dans la section [Langages pris en charge](#supported-languages).</span><span class="sxs-lookup"><span data-stu-id="24327-125">You can see a list of the supported values in the [Supported languages](#supported-languages) section.</span></span> <span data-ttu-id="24327-126">Ce champ doit être défini seulement quand plusieurs langages de programmation sont couverts dans la rubrique.</span><span class="sxs-lookup"><span data-stu-id="24327-126">Only needs to be set when there's more than one programming language covered in the topic.</span></span> <span data-ttu-id="24327-127">En règle générale, nous utilisons seulement `csharp`, `vb`, `fsharp` et `cpp` pour cette valeur dans notre contenu.</span><span class="sxs-lookup"><span data-stu-id="24327-127">Typically, we only use `csharp`, `vb`, `fsharp`, and `cpp` for this value in our content.</span></span>
- <span data-ttu-id="24327-128">**ms.prod** : Identification du produit utilisée à des fins de BI.</span><span class="sxs-lookup"><span data-stu-id="24327-128">**ms.prod**: Product identification used for BI purposes.</span></span> <span data-ttu-id="24327-129">Elles sont généralement définies à un niveau global, de sorte qu’elles n’apparaissent généralement pas dans le bloc de métadonnées de chaque article.</span><span class="sxs-lookup"><span data-stu-id="24327-129">They're usually set at a global level, so they don't usually appear in the metadata block of each article.</span></span>
- <span data-ttu-id="24327-130">**ms.technology** : Classification BI supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="24327-130">**ms.technology**: Additional BI classification.</span></span> <span data-ttu-id="24327-131">Voici quelques-unes des valeurs prises en charge : `devlang-csharp` pour les rubriques C#, `devlang-fsharp` pour les rubriques F# et `devlang-visual-basic` pour les rubriques VB.</span><span class="sxs-lookup"><span data-stu-id="24327-131">Some of the supported values are: `devlang-csharp` for C# topics, `devlang-fsharp` for F# topics, and `devlang-visual-basic` for VB topics.</span></span> <span data-ttu-id="24327-132">Pour les autres guides, les valeurs varient : demandez à un membre de l’équipe de vous aider.</span><span class="sxs-lookup"><span data-stu-id="24327-132">For other guides, the values will vary, so ask a member of the team for guidance.</span></span>
- <span data-ttu-id="24327-133">**ms.date** : Date au format JJ/MM/AAAA.</span><span class="sxs-lookup"><span data-stu-id="24327-133">**ms.date**: A date in the format MM/DD/YYYY.</span></span> <span data-ttu-id="24327-134">Affiché sur la page publiée pour indiquer la dernière fois que l’article a été modifié de façon substantielle ou garanti « actualisé » (c’est-à-dire que l’article a été révisé et qu’il est considéré comme étant à jour).</span><span class="sxs-lookup"><span data-stu-id="24327-134">Displayed on the published page to indicate the last time the article was substantially edited or guaranteed "fresh" (that is, the article was reviewed and considered up-to-date).</span></span>
- <span data-ttu-id="24327-135">**helpviewer_keywords** : Les entrées sont utilisées pour l’index des livres hors connexion (fonctionnalité dans Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="24327-135">**helpviewer_keywords**: Entries are used for the offline books index (functionality in Visual Studio).</span></span>
- <span data-ttu-id="24327-136">**f1_keywords** : Connecte l’article à la touche F1 (fonctionnalité dans Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="24327-136">**f1_keywords**: Connects the article to the F1 key (functionality in Visual Studio).</span></span>

## <a name="basic-markdown-gfm-and-special-characters"></a><span data-ttu-id="24327-137">Markdown de base, GFM et caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="24327-137">Basic Markdown, GFM, and special characters</span></span>

<span data-ttu-id="24327-138">Toute la syntaxe Markdown de base et GFM (GitHub Flavored Markdown) est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="24327-138">All basic and GitHub Flavored Markdown (GFM) is supported.</span></span> <span data-ttu-id="24327-139">Pour plus d’informations sur cette syntaxe, consultez :</span><span class="sxs-lookup"><span data-stu-id="24327-139">For more information on these, see:</span></span>

- [<span data-ttu-id="24327-140">Syntaxe Markdown de base</span><span class="sxs-lookup"><span data-stu-id="24327-140">Baseline Markdown syntax</span></span>](https://daringfireball.net/projects/markdown/syntax)
- [<span data-ttu-id="24327-141">Documentation GFM</span><span class="sxs-lookup"><span data-stu-id="24327-141">GFM documentation</span></span>](https://guides.github.com/features/mastering-markdown)

<span data-ttu-id="24327-142">Markdown utilise des caractères spéciaux tels que \*, \` et \# pour la mise en forme.</span><span class="sxs-lookup"><span data-stu-id="24327-142">Markdown uses special characters such as \*, \`, and \# for formatting.</span></span> <span data-ttu-id="24327-143">Si vous souhaitez inclure l’un de ces caractères dans votre contenu, vous devez effectuer l’une des deux opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="24327-143">If you wish to include one of these characters in your content, you must do one of two things:</span></span>

- <span data-ttu-id="24327-144">Placer une barre oblique inverse devant le caractère spécial pour l’« échappement » de ce caractère (par exemple, `\*` pour un \*)</span><span class="sxs-lookup"><span data-stu-id="24327-144">Put a backslash before the special character to "escape" it (for example, `\*` for a \*)</span></span>
- <span data-ttu-id="24327-145">Utiliser le [code d’entité HTML](https://www.ascii.cl/htmlcodes.htm) pour le caractère (par exemple, `&#42;` pour un &#42;).</span><span class="sxs-lookup"><span data-stu-id="24327-145">Use the [HTML entity code](https://www.ascii.cl/htmlcodes.htm) for the character (for example, `&#42;` for a &#42;).</span></span>

## <a name="file-name"></a><span data-ttu-id="24327-146">Nom de fichier</span><span class="sxs-lookup"><span data-stu-id="24327-146">File name</span></span>

<span data-ttu-id="24327-147">Les noms des fichiers utilisent les règles suivantes :</span><span class="sxs-lookup"><span data-stu-id="24327-147">File names use the following rules:</span></span>

* <span data-ttu-id="24327-148">Ils contiennent uniquement des lettres minuscules, des chiffres et des traits d’union.</span><span class="sxs-lookup"><span data-stu-id="24327-148">Contain only lowercase letters, numbers, and hyphens.</span></span>
* <span data-ttu-id="24327-149">Aucun espace ni caractère de ponctuation.</span><span class="sxs-lookup"><span data-stu-id="24327-149">No spaces or punctuation characters.</span></span> <span data-ttu-id="24327-150">Utilisez les traits d’union pour séparer les mots et les nombres dans le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="24327-150">Use the hyphens to separate words and numbers in the file name.</span></span>
* <span data-ttu-id="24327-151">Utilisez des verbes d’actions spécifiques, tels que développer, acheter, générer, dépanner.</span><span class="sxs-lookup"><span data-stu-id="24327-151">Use action verbs that are specific, such as develop, buy, build, troubleshoot.</span></span> <span data-ttu-id="24327-152">Pas de substantif.</span><span class="sxs-lookup"><span data-stu-id="24327-152">No -ing words.</span></span>
* <span data-ttu-id="24327-153">Pas de mot trop court ; évitez un, et, le, en, ou, etc.</span><span class="sxs-lookup"><span data-stu-id="24327-153">No small words - don't include a, and, the, in, or, etc.</span></span>
* <span data-ttu-id="24327-154">Le nom doit être au format Markdown et utiliser l’extension de fichier .md.</span><span class="sxs-lookup"><span data-stu-id="24327-154">Must be in Markdown and use the .md file extension.</span></span>
* <span data-ttu-id="24327-155">Privilégiez des noms de fichiers courts.</span><span class="sxs-lookup"><span data-stu-id="24327-155">Keep file names reasonably short.</span></span> <span data-ttu-id="24327-156">Ils font partie de l’URL pour vos articles.</span><span class="sxs-lookup"><span data-stu-id="24327-156">They are part of the URL for your articles.</span></span>

## <a name="headings"></a><span data-ttu-id="24327-157">Titres</span><span class="sxs-lookup"><span data-stu-id="24327-157">Headings</span></span>

<span data-ttu-id="24327-158">Utilisez la mise en majuscules comme pour les phrases.</span><span class="sxs-lookup"><span data-stu-id="24327-158">Use sentence-style capitalization.</span></span> <span data-ttu-id="24327-159">Mettez toujours en majuscules :</span><span class="sxs-lookup"><span data-stu-id="24327-159">Always capitalize:</span></span>

- <span data-ttu-id="24327-160">Le premier mot d’un titre.</span><span class="sxs-lookup"><span data-stu-id="24327-160">The first word of a heading.</span></span>
- <span data-ttu-id="24327-161">Le mot qui suit le signe deux-points dans un titre ou un en-tête (par exemple, « Comment : Trier un tableau »).</span><span class="sxs-lookup"><span data-stu-id="24327-161">The word following a colon in a title or heading (for example, "How to: Sort an array").</span></span>

<span data-ttu-id="24327-162">Les titres doivent être créés à l’aide du style atx, c’est-à-dire en utilisant 1 à 6 caractères de hachage (#) au début de la ligne pour indiquer un titre, correspondant aux niveaux de titres HTML H1 à H6.</span><span class="sxs-lookup"><span data-stu-id="24327-162">Headings should be done using atx-style, that is, use 1-6 hash characters (#) at the start of the line to indicate a heading, corresponding to HTML headings levels H1 through H6.</span></span> <span data-ttu-id="24327-163">Des exemples de titres de premier et second niveau sont utilisés ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="24327-163">Examples of first- and second-level headers are used above.</span></span>

<span data-ttu-id="24327-164">Il ne **doit** exister qu’un seul titre de premier niveau (H1) dans votre rubrique, qui sera affiché comme titre sur la page.</span><span class="sxs-lookup"><span data-stu-id="24327-164">There **must** be only one first-level heading (H1) in your topic, which will be displayed as the on-page title.</span></span>

<span data-ttu-id="24327-165">Si votre titre se termine par un caractère `#`, vous devez ajouter un autre caractère `#` à la fin pour que le titre soit correctement rendu.</span><span class="sxs-lookup"><span data-stu-id="24327-165">If your heading finishes with a `#` character, you need to add an extra `#` character in the end in order for the title to render correctly.</span></span> <span data-ttu-id="24327-166">Par exemple, `# Async Programming in F# #`.</span><span class="sxs-lookup"><span data-stu-id="24327-166">For example, `# Async Programming in F# #`.</span></span>

<span data-ttu-id="24327-167">Les titres de second niveau génèrent la table des matières sur la page qui s’affiche dans la section « Dans cet article » en dessous du titre sur la page.</span><span class="sxs-lookup"><span data-stu-id="24327-167">Second-level headings will generate the on-page TOC that appears in the "In this article" section underneath the on-page title.</span></span>

### <a name="third-level-heading"></a><span data-ttu-id="24327-168">Titre de troisième niveau</span><span class="sxs-lookup"><span data-stu-id="24327-168">Third-level heading</span></span>
#### <a name="fourth-level-heading"></a><span data-ttu-id="24327-169">Titre de quatrième niveau</span><span class="sxs-lookup"><span data-stu-id="24327-169">Fourth-level heading</span></span>
##### <a name="fifth-level-heading"></a><span data-ttu-id="24327-170">Titre de cinquième niveau</span><span class="sxs-lookup"><span data-stu-id="24327-170">Fifth level heading</span></span>
###### <a name="sixth-level-heading"></a><span data-ttu-id="24327-171">Titre de sixième niveau</span><span class="sxs-lookup"><span data-stu-id="24327-171">Sixth-level heading</span></span>

## <a name="text-styling"></a><span data-ttu-id="24327-172">Style du texte</span><span class="sxs-lookup"><span data-stu-id="24327-172">Text styling</span></span>

<span data-ttu-id="24327-173">*Italique* À utiliser pour les fichiers, dossiers, chemins (pour les éléments longs, placés sur une ligne distincte) et les nouveaux termes.</span><span class="sxs-lookup"><span data-stu-id="24327-173">*Italics* Use for files, folders, paths (for long items, split onto their own line), new terms.</span></span>

<span data-ttu-id="24327-174">**Gras** À utiliser pour les éléments d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="24327-174">**Bold** Use for UI elements.</span></span>

<span data-ttu-id="24327-175">`Code` À utiliser pour le code inline, les mots clés du langage, les noms de package NuGet, les commandes de ligne de commande, les noms des tables et des colonnes de base de données ainsi que les URL sur lesquelles les lecteurs ne doivent pas pouvoir cliquer.</span><span class="sxs-lookup"><span data-stu-id="24327-175">`Code` Use for inline code, language keywords, NuGet package names, command-line commands, database table and column names, and URLs that you don't want to be clickable.</span></span>

## <a name="links"></a><span data-ttu-id="24327-176">Liens</span><span class="sxs-lookup"><span data-stu-id="24327-176">Links</span></span>

### <a name="internal-links"></a><span data-ttu-id="24327-177">Liens internes</span><span class="sxs-lookup"><span data-stu-id="24327-177">Internal Links</span></span>

<span data-ttu-id="24327-178">Pour établir un lien à un en-tête dans le même fichier Markdown (également appelés liens d’ancrage), vous devrez trouver l’ID de l’en-tête en question.</span><span class="sxs-lookup"><span data-stu-id="24327-178">To link to a header in the same Markdown file (also known as anchor links), you'll need to find out the id of the header you're trying to link to.</span></span> <span data-ttu-id="24327-179">Pour vérifier l’ID, affichez la source de l’article rendu, recherchez l’ID de l’en-tête (par exemple, `id="blockquote"`) et établissez le lien avec # + ID (par exemple, `#blockquote`).</span><span class="sxs-lookup"><span data-stu-id="24327-179">To confirm the ID, view the source of the rendered article, find the id of the header (for example, `id="blockquote"`), and link using # + id (for example, `#blockquote`).</span></span>
<span data-ttu-id="24327-180">L’ID est généré automatiquement en fonction du texte d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="24327-180">The id is auto-generated based on the header text.</span></span> <span data-ttu-id="24327-181">Ainsi, par exemple, étant donné une section unique nommée `## Step 2`, l’ID ressemblerait à `id="step-2"`.</span><span class="sxs-lookup"><span data-stu-id="24327-181">So, for example, given a unique section named `## Step 2`, the id would look like this `id="step-2"`.</span></span>

- <span data-ttu-id="24327-182">Exemple : `[Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier)` produit [Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier) (Déclarer des blocs inline avec un identificateur du langage).</span><span class="sxs-lookup"><span data-stu-id="24327-182">Example: `[Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier)` produces [Declare inline blocks with a language identifier](#inline-code-blocks-with-language-identifier).</span></span>

<span data-ttu-id="24327-183">Pour établir un lien à un fichier Markdown dans le même dépôt, utilisez des [liens relatifs](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), dont « .md » à la fin du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="24327-183">To link to a Markdown file in the same repo, use [relative links](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2), including the ".md" at the end of the filename.</span></span>

- <span data-ttu-id="24327-184">Exemple : `[Readme file](../README.md)` produit [Readme file](../README.md) (Fichier Lisez-moi).</span><span class="sxs-lookup"><span data-stu-id="24327-184">Example: `[Readme file](../README.md)` produces [Readme file](../README.md).</span></span> <span data-ttu-id="24327-185">(Notez que les liens sont sensibles à la casse.)</span><span class="sxs-lookup"><span data-stu-id="24327-185">(Note that links are case-sensitive.)</span></span>
- <span data-ttu-id="24327-186">Exemple : `[Welcome to .NET](../docs/welcome.md)` produit [Welcome to .NET](../docs/welcome.md) (Bienvenue dans .NET).</span><span class="sxs-lookup"><span data-stu-id="24327-186">Example: `[Welcome to .NET](../docs/welcome.md)` produces [Welcome to .NET](../docs/welcome.md).</span></span>

<span data-ttu-id="24327-187">Pour établir un lien à un en-tête d’un fichier Markdown dans le même dépôt, utilisez la liaison relative + la liaison hashtag.</span><span class="sxs-lookup"><span data-stu-id="24327-187">To link to a header in a Markdown file in the same repo, use relative linking + hashtag linking.</span></span>

- <span data-ttu-id="24327-188">Exemple : `[.NET Community](../docs/welcome.md#open-source)` produit [.NET Community](../docs/welcome.md#open-source) (Communauté .NET).</span><span class="sxs-lookup"><span data-stu-id="24327-188">Example: `[.NET Community](../docs/welcome.md#open-source)` produces [.NET Community](../docs/welcome.md#open-source).</span></span>

<span data-ttu-id="24327-189">Dans la plupart des cas, nous utilisons les liens relatifs et nous n’encourageons pas l’utilisation de `~/` dans les liens, car les liens relatifs sont résolus dans la source sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="24327-189">In most cases, we use the relative links and discourage the use of `~/` in links because relative links resolve in the source on GitHub.</span></span> <span data-ttu-id="24327-190">Cependant, chaque fois que nous utilisons un lien vers un fichier dans un dépôt dépendant, nous utilisons le caractère `~/` pour fournir le chemin.</span><span class="sxs-lookup"><span data-stu-id="24327-190">However, whenever we link to a file in a dependent repo, we'll use the `~/` character to provide the path.</span></span> <span data-ttu-id="24327-191">Comme les fichiers dans les dépôts dépendants se trouvent à un emplacement différent dans GitHub, les liens ne sont pas correctement résolus avec les liens relatifs, quelle que soit la façon dont ils ont été écrits.</span><span class="sxs-lookup"><span data-stu-id="24327-191">Because the files in the dependent repo are in a different location in GitHub the links won't resolve correctly with relative links regardless of how they were written.</span></span>

<span data-ttu-id="24327-192">La spécification du langage C# et la spécification du langage Visual Basic sont incluses dans les documents .NET grâce à l’inclusion de la source des dépôts du langage.</span><span class="sxs-lookup"><span data-stu-id="24327-192">The C# language specification and the Visual Basic language specification are included in the .NET docs by including the source from the language repositories.</span></span> <span data-ttu-id="24327-193">Les sources Markdown sont gérées dans les dépôts [csharplang](https://github.com/dotnet/csharplang) et [visual basic](https://github.com/dotnet/vblang).</span><span class="sxs-lookup"><span data-stu-id="24327-193">The markdown sources are managed in the [csharplang](https://github.com/dotnet/csharplang) and [visual basic](https://github.com/dotnet/vblang) repositories.</span></span>

<span data-ttu-id="24327-194">Les liens vers la spécification doivent pointer vers les répertoires sources où ces spécifications sont incluses.</span><span class="sxs-lookup"><span data-stu-id="24327-194">Links to the spec must point to the source directories where those specs are included.</span></span> <span data-ttu-id="24327-195">Pour C#, il s’agit de **~/_csharplang/spec** et pour VB, il s’agit de **~/_vblang/spec**.</span><span class="sxs-lookup"><span data-stu-id="24327-195">For C#, it's **~/_csharplang/spec** and for VB, it's **~/_vblang/spec**.</span></span>

- <span data-ttu-id="24327-196">Exemple : `[C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions)` produit [C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions) (Expressions de requête de requête C#).</span><span class="sxs-lookup"><span data-stu-id="24327-196">Example: `[C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions)` produces [C# Query Expressions](~/_csharplang/spec/expressions.md#query-expressions).</span></span>

### <a name="external-links"></a><span data-ttu-id="24327-197">Liens externes</span><span class="sxs-lookup"><span data-stu-id="24327-197">External Links</span></span>

<span data-ttu-id="24327-198">Pour établir un lien à un fichier externe, utilisez l’URL complète comme lien.</span><span class="sxs-lookup"><span data-stu-id="24327-198">To link to an external file, use the full URL as the link.</span></span>

- <span data-ttu-id="24327-199">Exemple : `[GitHub](https://www.github.com)` produit [GitHub](https://www.github.com).</span><span class="sxs-lookup"><span data-stu-id="24327-199">Example: `[GitHub](https://www.github.com)` produces [GitHub](https://www.github.com).</span></span>

<span data-ttu-id="24327-200">Si une URL apparaît dans un fichier Markdown, elle est transformée en lien interactif.</span><span class="sxs-lookup"><span data-stu-id="24327-200">If a URL appears in a Markdown file, it will be transformed into a clickable link.</span></span>

- <span data-ttu-id="24327-201">Exemple : `<https://www.github.com>` produit <https://www.github.com>.</span><span class="sxs-lookup"><span data-stu-id="24327-201">Example: `<https://www.github.com>` produces <https://www.github.com>.</span></span>

<span data-ttu-id="24327-202">Préférez le protocole `https` pour les liens externes.</span><span class="sxs-lookup"><span data-stu-id="24327-202">Prefer the `https` protocol for external links.</span></span> <span data-ttu-id="24327-203">Utilisez des liens `http` seulement pour les sites qui ne prennent pas en charge `https`.</span><span class="sxs-lookup"><span data-stu-id="24327-203">Only use `http` links for sites that do not support `https`.</span></span>

### <a name="links-to-apis"></a><span data-ttu-id="24327-204">Liens vers des API</span><span class="sxs-lookup"><span data-stu-id="24327-204">Links to APIs</span></span>

<span data-ttu-id="24327-205">Le système de génération a certaines extensions qui permettent d’établir des liens à des API .NET sans avoir à utiliser de liens externes.</span><span class="sxs-lookup"><span data-stu-id="24327-205">The build system has some extensions that allow us to link to .NET APIs without having to use external links.</span></span>
<span data-ttu-id="24327-206">Lors de la liaison à une API, vous pouvez utiliser son identificateur unique (UID) qui est généré automatiquement à partir du code source.</span><span class="sxs-lookup"><span data-stu-id="24327-206">When linking to an API, you can use its unique identifier (UID) that is auto-generated from the source code.</span></span>

<span data-ttu-id="24327-207">L’UID équivaut au nom complet du type et du membre.</span><span class="sxs-lookup"><span data-stu-id="24327-207">The UID equates to the fully qualified type and member name.</span></span>

<span data-ttu-id="24327-208">Si vous ajoutez un caractère \* (ou %2A) après l’UID, le lien représente alors la page de surcharge et non pas une API spécifique.</span><span class="sxs-lookup"><span data-stu-id="24327-208">If you add a \* (or %2A) after the UID, the link then represents the overload page and not a specific API.</span></span> <span data-ttu-id="24327-209">Par exemple, vous pouvez utiliser cela quand vous voulez créer un lien vers la page [List\<T>.BinarySearch Method](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch) de façon générique au lieu d’une surcharge spécifique comme [List\<T>.BinarySearch(T, IComparer\<T>)](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch#System_Collections_Generic_List_1_BinarySearch__0_).</span><span class="sxs-lookup"><span data-stu-id="24327-209">For example, you can use that when you want to link to the [List\<T>.BinarySearch Method](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch) page in a generic way instead of a specific overload such as [List\<T>.BinarySearch(T, IComparer\<T>)](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1.binarysearch#System_Collections_Generic_List_1_BinarySearch__0_).</span></span> <span data-ttu-id="24327-210">Vous pouvez également utiliser \* pour établir un lien vers une page de membre quand le membre n’est pas surchargé : ceci vous évite de devoir inclure la liste des paramètres dans l’UID.</span><span class="sxs-lookup"><span data-stu-id="24327-210">You can also use \* to link to a member page when the member is not overloaded; this saves you from having to include the parameter list in the UID.</span></span>

<span data-ttu-id="24327-211">Pour établir un lien vers une surcharge de méthode spécifique, vous devez inclure le nom complet du type de chacun des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="24327-211">To link to a specific method overload, you must include the fully qualified type name of each of the method's parameters.</span></span> <span data-ttu-id="24327-212">Par exemple, \<xref:System.DateTime.ToString> établit un lien vers la méthode [DateTime.ToString](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString) sans paramètres, alors que \<xref:System.DateTime.ToString(System.String,System.IFormatProvider)> établit un lien vers la méthode [DateTime.ToString(String,IFormatProvider)](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString_System_String_System_IFormatProvider_).</span><span class="sxs-lookup"><span data-stu-id="24327-212">For example, \<xref:System.DateTime.ToString> links to the parameterless [DateTime.ToString](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString) method, while \<xref:System.DateTime.ToString(System.String,System.IFormatProvider)> links to the  [DateTime.ToString(String,IFormatProvider)](https://docs.microsoft.com/dotnet/api/system.datetime.tostring#System_DateTime_ToString_System_String_System_IFormatProvider_) method.</span></span> <span data-ttu-id="24327-213">Vous pouvez rechercher les UID d’un membre surchargé particulier à partir de `https://xref.docs.microsoft.com/autocomplete`.</span><span class="sxs-lookup"><span data-stu-id="24327-213">You can find the UIDs of a particular overloaded member from `https://xref.docs.microsoft.com/autocomplete`.</span></span> <span data-ttu-id="24327-214">La chaîne de requête « ?text= *\<nom_type_membre>*  » identifie le type ou le membre dont vous voulez voir les UID.</span><span class="sxs-lookup"><span data-stu-id="24327-214">The query string "?text=*\<type-member-name>*" identifies the type or member whose UIDs you'd like to see.</span></span> <span data-ttu-id="24327-215">Par exemple, `https://xref.docs.microsoft.com/autocomplete?text=string.format` récupère les surcharges de [String.Format](https://docs.microsoft.com/dotnet/api/system.string.format).</span><span class="sxs-lookup"><span data-stu-id="24327-215">For example, `https://xref.docs.microsoft.com/autocomplete?text=string.format` retrieves the [String.Format](https://docs.microsoft.com/dotnet/api/system.string.format) overloads.</span></span>

<span data-ttu-id="24327-216">Pour établir un lien vers un type générique, comme [System.Collections.Generic.List\<T>](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1), vous utilisez le caractère \` (%60) suivi du nombre de paramètres de type générique.</span><span class="sxs-lookup"><span data-stu-id="24327-216">To link to a generic type, such as [System.Collections.Generic.List\<T>](https://docs.microsoft.com/dotnet/api/system.collections.generic.list-1), you use the \` (%60) character followed by the number of generic type parameters.</span></span> <span data-ttu-id="24327-217">Par exemple, \<xref:System.Nullable%601> établit un lien vers le type [System.Nullable\<T>](https://docs.microsoft.com/dotnet/api/system.nullable-1), alors que \<xref:System.Func%602> établit un lien vers le délégué [System.Func\<T,TResult>](https://docs.microsoft.com/dotnet/api/system.func-2).</span><span class="sxs-lookup"><span data-stu-id="24327-217">For example, \<xref:System.Nullable%601> links to the [System.Nullable\<T>](https://docs.microsoft.com/dotnet/api/system.nullable-1) type, while \<xref:System.Func%602> links to the [System.Func\<T,TResult>](https://docs.microsoft.com/dotnet/api/system.func-2) delegate.</span></span>

<span data-ttu-id="24327-218">Vous pouvez utiliser l’une des syntaxes suivantes :</span><span class="sxs-lookup"><span data-stu-id="24327-218">You can use one of the following syntax:</span></span>

1. <span data-ttu-id="24327-219">Liaison automatique : `<xref:UID>` ou `<xref:UID?displayProperty=nameWithType>`</span><span class="sxs-lookup"><span data-stu-id="24327-219">Auto-link: `<xref:UID>` or `<xref:UID?displayProperty=nameWithType>`</span></span>

   <span data-ttu-id="24327-220">Le paramètre de requête `displayProperty` produit un texte de lien complet.</span><span class="sxs-lookup"><span data-stu-id="24327-220">The `displayProperty` query    parameter produces a fully qualified link text.</span></span> <span data-ttu-id="24327-221">Par défaut, le texte du lien affiche seulement le nom du membre ou du type.</span><span class="sxs-lookup"><span data-stu-id="24327-221">By default, link text shows only the member or type name.</span></span>

2. <span data-ttu-id="24327-222">Lien Markdown : `[link text](xref:UID)`</span><span class="sxs-lookup"><span data-stu-id="24327-222">Markdown link: `[link text](xref:UID)`</span></span>

   <span data-ttu-id="24327-223">À utiliser quand vous voulez personnaliser le texte du lien affiché.</span><span class="sxs-lookup"><span data-stu-id="24327-223">Use when you want to customize the link text displayed.</span></span>

<span data-ttu-id="24327-224">Exemples :</span><span class="sxs-lookup"><span data-stu-id="24327-224">Examples:</span></span>

- <span data-ttu-id="24327-225">`<xref:System.String>` est rendu sous forme de [String](https://docs.microsoft.com/dotnet/api/system.string)</span><span class="sxs-lookup"><span data-stu-id="24327-225">`<xref:System.String>` renders as [String](https://docs.microsoft.com/dotnet/api/system.string)</span></span>
- <span data-ttu-id="24327-226">`<xref:System.String?displayProperty=nameWithType>` est rendu sous forme de [System.String](https://docs.microsoft.com/dotnet/api/system.string)</span><span class="sxs-lookup"><span data-stu-id="24327-226">`<xref:System.String?displayProperty=nameWithType>` renders as [System.String](https://docs.microsoft.com/dotnet/api/system.string)</span></span>
- <span data-ttu-id="24327-227">`[String class](xref:System.String)` est rendu sous forme de [classe String](https://docs.microsoft.com/dotnet/api/system.string)</span><span class="sxs-lookup"><span data-stu-id="24327-227">`[String class](xref:System.String)` renders as [String class](https://docs.microsoft.com/dotnet/api/system.string)</span></span>

<span data-ttu-id="24327-228">Pour plus d’informations sur l’utilisation de cette notation, consultez [Utilisation de renvois](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference).</span><span class="sxs-lookup"><span data-stu-id="24327-228">For more information about using this notation, see [Using cross reference](https://dotnet.github.io/docfx/tutorial/links_and_cross_references.html#using-cross-reference).</span></span>

<span data-ttu-id="24327-229">Vous pouvez trouver l’UID de deux façons :</span><span class="sxs-lookup"><span data-stu-id="24327-229">There are two ways to find the UID:</span></span>

- <span data-ttu-id="24327-230">Affichez la source de la page de l’API vers laquelle vous voulez établir un lien et recherchez la valeur de ms.assetid.</span><span class="sxs-lookup"><span data-stu-id="24327-230">View the source for the API page you want to link to and find the ms.assetid value.</span></span> <span data-ttu-id="24327-231">Notez que les valeurs de surcharge individuelles ne sont pas affichées dans la source.</span><span class="sxs-lookup"><span data-stu-id="24327-231">Note that individual overload values are not shown in the source.</span></span>
- <span data-ttu-id="24327-232">Utilisez l’outil suivant pour rechercher les UID : https://xref.docs.microsoft.com/autocomplete?text=tostring (remplacez tostring par des parties du nom de l’API que vous recherchez).</span><span class="sxs-lookup"><span data-stu-id="24327-232">Use the following tool to search for UIDs: https://xref.docs.microsoft.com/autocomplete?text=tostring (replace tostring with parts of the API name you're trying to find).</span></span> <span data-ttu-id="24327-233">L’outil recherche le paramètre de requête `text` fourni dans toutes les parties de l’UID.</span><span class="sxs-lookup"><span data-stu-id="24327-233">The tool searches for the provided `text` query parameter in any part of the UID.</span></span> <span data-ttu-id="24327-234">Par exemple, vous pouvez rechercher le nom de membre (ToString), le nom de membre partiel (ToStri), le nom de type et de membre (Double.ToString), etc.</span><span class="sxs-lookup"><span data-stu-id="24327-234">For example, you can search for member name (ToString), partial member name (ToStri), type and member name (Double.ToString), etc.</span></span>

<span data-ttu-id="24327-235">Quand l’UID contient les caractères spéciaux \`, \# ou \*, la valeur de l’UID doit être encodée au format HTML, respectivement en `%60`, `%23` et `%2A`.</span><span class="sxs-lookup"><span data-stu-id="24327-235">When the UID contains the special characters \`, \# or \*, the UID value needs to be HTML encoded as `%60`, `%23` and `%2A` respectively.</span></span> <span data-ttu-id="24327-236">Vous verrez parfois des parenthèses encodées, mais ce n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="24327-236">You'll sometimes see parentheses encoded but it's not a requirement.</span></span>

<span data-ttu-id="24327-237">Exemples :</span><span class="sxs-lookup"><span data-stu-id="24327-237">Examples:</span></span>

- <span data-ttu-id="24327-238">System.Threading.Tasks.Task\`1 devient `System.Threading.Tasks.Task%601`</span><span class="sxs-lookup"><span data-stu-id="24327-238">System.Threading.Tasks.Task\`1 becomes `System.Threading.Tasks.Task%601`</span></span>
- <span data-ttu-id="24327-239">System.Exception.\#ctor devient `System.Exception.%23ctor`</span><span class="sxs-lookup"><span data-stu-id="24327-239">System.Exception.\#ctor becomes `System.Exception.%23ctor`</span></span>
- <span data-ttu-id="24327-240">System.Lazy\`1.\#ctor(System.Threading.LazyThreadSafetyMode) devient `System.Lazy%601.%23ctor%28System.Threading.LazyThreadSafetyMode%29`</span><span class="sxs-lookup"><span data-stu-id="24327-240">System.Lazy\`1.\#ctor(System.Threading.LazyThreadSafetyMode) becomes  `System.Lazy%601.%23ctor%28System.Threading.LazyThreadSafetyMode%29`</span></span>

## <a name="lists"></a><span data-ttu-id="24327-241">Listes</span><span class="sxs-lookup"><span data-stu-id="24327-241">Lists</span></span>

### <a name="ordered-lists"></a><span data-ttu-id="24327-242">Listes triées</span><span class="sxs-lookup"><span data-stu-id="24327-242">Ordered lists</span></span>

1. <span data-ttu-id="24327-243">This</span><span class="sxs-lookup"><span data-stu-id="24327-243">This</span></span>
1. <span data-ttu-id="24327-244">Is</span><span class="sxs-lookup"><span data-stu-id="24327-244">Is</span></span>
1. <span data-ttu-id="24327-245">An</span><span class="sxs-lookup"><span data-stu-id="24327-245">An</span></span>
1. <span data-ttu-id="24327-246">Ordered</span><span class="sxs-lookup"><span data-stu-id="24327-246">Ordered</span></span>
1. <span data-ttu-id="24327-247">List</span><span class="sxs-lookup"><span data-stu-id="24327-247">List</span></span>

#### <a name="ordered-list-with-an-embedded-list"></a><span data-ttu-id="24327-248">Liste triée avec une liste incorporée</span><span class="sxs-lookup"><span data-stu-id="24327-248">Ordered list with an embedded list</span></span>

1. <span data-ttu-id="24327-249">Here</span><span class="sxs-lookup"><span data-stu-id="24327-249">Here</span></span>
1. <span data-ttu-id="24327-250">comes</span><span class="sxs-lookup"><span data-stu-id="24327-250">comes</span></span>
1. <span data-ttu-id="24327-251">an</span><span class="sxs-lookup"><span data-stu-id="24327-251">an</span></span>
1. <span data-ttu-id="24327-252">embedded</span><span class="sxs-lookup"><span data-stu-id="24327-252">embedded</span></span>
    1. <span data-ttu-id="24327-253">Miss Scarlett</span><span class="sxs-lookup"><span data-stu-id="24327-253">Miss Scarlett</span></span>
    1. <span data-ttu-id="24327-254">Professor Plum</span><span class="sxs-lookup"><span data-stu-id="24327-254">Professor Plum</span></span>
1. <span data-ttu-id="24327-255">ordered</span><span class="sxs-lookup"><span data-stu-id="24327-255">ordered</span></span>
1. <span data-ttu-id="24327-256">list</span><span class="sxs-lookup"><span data-stu-id="24327-256">list</span></span>

### <a name="unordered-lists"></a><span data-ttu-id="24327-257">Listes non triées</span><span class="sxs-lookup"><span data-stu-id="24327-257">Unordered Lists</span></span>

- <span data-ttu-id="24327-258">This</span><span class="sxs-lookup"><span data-stu-id="24327-258">This</span></span>
- <span data-ttu-id="24327-259">est</span><span class="sxs-lookup"><span data-stu-id="24327-259">is</span></span>
- <span data-ttu-id="24327-260">a</span><span class="sxs-lookup"><span data-stu-id="24327-260">a</span></span>
- <span data-ttu-id="24327-261">bulleted</span><span class="sxs-lookup"><span data-stu-id="24327-261">bulleted</span></span>
- <span data-ttu-id="24327-262">list</span><span class="sxs-lookup"><span data-stu-id="24327-262">list</span></span>

#### <a name="unordered-list-with-an-embedded-list"></a><span data-ttu-id="24327-263">Liste non triée avec une liste incorporée</span><span class="sxs-lookup"><span data-stu-id="24327-263">Unordered list with an embedded list</span></span>

- <span data-ttu-id="24327-264">This</span><span class="sxs-lookup"><span data-stu-id="24327-264">This</span></span>
- <span data-ttu-id="24327-265">bulleted</span><span class="sxs-lookup"><span data-stu-id="24327-265">bulleted</span></span>
- <span data-ttu-id="24327-266">list</span><span class="sxs-lookup"><span data-stu-id="24327-266">list</span></span>
  - <span data-ttu-id="24327-267">Mrs. Peacock</span><span class="sxs-lookup"><span data-stu-id="24327-267">Mrs. Peacock</span></span>
  - <span data-ttu-id="24327-268">Mr. Green</span><span class="sxs-lookup"><span data-stu-id="24327-268">Mr. Green</span></span>
- <span data-ttu-id="24327-269">contains</span><span class="sxs-lookup"><span data-stu-id="24327-269">contains</span></span>
- <span data-ttu-id="24327-270">other</span><span class="sxs-lookup"><span data-stu-id="24327-270">other</span></span>
  1. <span data-ttu-id="24327-271">Colonel Mustard</span><span class="sxs-lookup"><span data-stu-id="24327-271">Colonel Mustard</span></span>
  1. <span data-ttu-id="24327-272">Mrs. White</span><span class="sxs-lookup"><span data-stu-id="24327-272">Mrs. White</span></span>
- <span data-ttu-id="24327-273">lists</span><span class="sxs-lookup"><span data-stu-id="24327-273">lists</span></span>

## <a name="horizontal-rule"></a><span data-ttu-id="24327-274">Ligne horizontale</span><span class="sxs-lookup"><span data-stu-id="24327-274">Horizontal rule</span></span>

---

## <a name="tables"></a><span data-ttu-id="24327-275">Tables</span><span class="sxs-lookup"><span data-stu-id="24327-275">Tables</span></span>

| <span data-ttu-id="24327-276">Tables</span><span class="sxs-lookup"><span data-stu-id="24327-276">Tables</span></span>        | <span data-ttu-id="24327-277">Sont</span><span class="sxs-lookup"><span data-stu-id="24327-277">Are</span></span>           | <span data-ttu-id="24327-278">Cool</span><span class="sxs-lookup"><span data-stu-id="24327-278">Cool</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="24327-279">col 3 est</span><span class="sxs-lookup"><span data-stu-id="24327-279">col 3 is</span></span>      | <span data-ttu-id="24327-280">alignée à droite</span><span class="sxs-lookup"><span data-stu-id="24327-280">right-aligned</span></span> | <span data-ttu-id="24327-281">1 600 $</span><span class="sxs-lookup"><span data-stu-id="24327-281">$1600</span></span> |
| <span data-ttu-id="24327-282">col 2 est</span><span class="sxs-lookup"><span data-stu-id="24327-282">col 2 is</span></span>      | <span data-ttu-id="24327-283">centrée</span><span class="sxs-lookup"><span data-stu-id="24327-283">centered</span></span>      |   <span data-ttu-id="24327-284">12 $</span><span class="sxs-lookup"><span data-stu-id="24327-284">$12</span></span> |
| <span data-ttu-id="24327-285">col 1 est la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="24327-285">col 1 is default</span></span> | <span data-ttu-id="24327-286">alignée à gauche</span><span class="sxs-lookup"><span data-stu-id="24327-286">left-aligned</span></span>     |    <span data-ttu-id="24327-287">1 $</span><span class="sxs-lookup"><span data-stu-id="24327-287">$1</span></span> |

<span data-ttu-id="24327-288">Vous pouvez utiliser un [outil de génération de table Markdown](https://www.tablesgenerator.com/markdown_tables) pour les créer plus facilement.</span><span class="sxs-lookup"><span data-stu-id="24327-288">You can use a [Markdown table generator tool](https://www.tablesgenerator.com/markdown_tables) to help creating them more easily.</span></span>

## <a name="code"></a><span data-ttu-id="24327-289">Code</span><span class="sxs-lookup"><span data-stu-id="24327-289">Code</span></span>

<span data-ttu-id="24327-290">La meilleure façon d’inclure du code consiste à ajouter des extraits à partir d’un exemple fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="24327-290">The best way to include code is to include snippets from a working sample.</span></span> <span data-ttu-id="24327-291">Créez votre exemple en suivant les instructions du [guide de contribution](../CONTRIBUTING.md#contributing-to-samples).</span><span class="sxs-lookup"><span data-stu-id="24327-291">Create your sample following the instructions in the [contributing guide](../CONTRIBUTING.md#contributing-to-samples).</span></span>

<span data-ttu-id="24327-292">Vous pouvez inclure le code avec la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="24327-292">You can include the code using the following syntax:</span></span>

```markdown
[!code-<language>[<name>](<pathToFile><queryoption><queryoptionvalue>)]
```

* <span data-ttu-id="24327-293">`-<language>` (*facultatif* mais *recommandé*)</span><span class="sxs-lookup"><span data-stu-id="24327-293">`-<language>` (*optional* but *recommended*)</span></span>
  * <span data-ttu-id="24327-294">Langage de l’extrait de code référencé.</span><span class="sxs-lookup"><span data-stu-id="24327-294">Language of the code snippet being referenced.</span></span> <span data-ttu-id="24327-295">Pour obtenir la liste des valeurs prises en charge, consultez [Langages pris en charge](#supported-languages).</span><span class="sxs-lookup"><span data-stu-id="24327-295">For a list of supported values, see [Supported languages](#supported-languages).</span></span>

* <span data-ttu-id="24327-296">`<name>` (*facultatif*)</span><span class="sxs-lookup"><span data-stu-id="24327-296">`<name>` (*optional*)</span></span>
  * <span data-ttu-id="24327-297">Nom pour l’extrait de code.</span><span class="sxs-lookup"><span data-stu-id="24327-297">Name for the code snippet.</span></span> <span data-ttu-id="24327-298">Il n’a aucun impact sur le code HTML de sortie, mais vous pouvez l’utiliser pour améliorer la lisibilité de votre source Markdown.</span><span class="sxs-lookup"><span data-stu-id="24327-298">It doesn’t have any impact on the output HTML, but you can use it to improve the readability of your Markdown source.</span></span>

* <span data-ttu-id="24327-299">`<pathToFile>` (*obligatoire*)</span><span class="sxs-lookup"><span data-stu-id="24327-299">`<pathToFile>` (*mandatory*)</span></span>
  * <span data-ttu-id="24327-300">Chemin relatif dans le système de fichiers qui indique le fichier de l’extrait de code à référencer.</span><span class="sxs-lookup"><span data-stu-id="24327-300">Relative path in the file system that indicates the code snippet file to reference.</span></span>

* <span data-ttu-id="24327-301">`<queryoption>` et `<queryoptionvalue>` (*facultatif*)</span><span class="sxs-lookup"><span data-stu-id="24327-301">`<queryoption>` and `<queryoptionvalue>` (*optional*)</span></span>
  * <span data-ttu-id="24327-302">Utilisés ensemble pour spécifier la façon dont le code doit être récupéré à partir du fichier :</span><span class="sxs-lookup"><span data-stu-id="24327-302">Used together to specify how the code should be retrieved from the file:</span></span>
    * <span data-ttu-id="24327-303">`#` :  `#L{startlinenumber}-L{endlinenumber}` (plage de lignes) *ou* `#{tagname}` (nom de l’étiquette).</span><span class="sxs-lookup"><span data-stu-id="24327-303">`#`:  `#L{startlinenumber}-L{endlinenumber}` (line range) *or* `#{tagname}` (tag name).</span></span>
    <span data-ttu-id="24327-304">Nous déconseillons d’utiliser les numéros de ligne, car ceux-ci sont très instables.</span><span class="sxs-lookup"><span data-stu-id="24327-304">We discourage the use of line numbers because they are very brittle.</span></span> <span data-ttu-id="24327-305">Le nom d’étiquette est le meilleur moyen de référencer des extraits de code.</span><span class="sxs-lookup"><span data-stu-id="24327-305">Tag name is the preferred way of referencing code snippets.</span></span>
    * <span data-ttu-id="24327-306">`range`: `?range=1,3-5` Une plage de lignes.</span><span class="sxs-lookup"><span data-stu-id="24327-306">`range`: `?range=1,3-5` A range of lines.</span></span> <span data-ttu-id="24327-307">Cet exemple inclut les lignes 1, 3, 4 et 5.</span><span class="sxs-lookup"><span data-stu-id="24327-307">This example includes lines 1, 3, 4, and 5.</span></span>
    * <span data-ttu-id="24327-308">`dedent`: `?dedent=8` Désindente les lignes d’un certain nombre d’espaces ; dans ce cas, de 8 espaces.</span><span class="sxs-lookup"><span data-stu-id="24327-308">`dedent`: `?dedent=8` Dedents the lines by a number of spaces--in this case, 8.</span></span> <span data-ttu-id="24327-309">Ceci peut être combiné avec `range` et d’autres options de requête qui sélectionnent un sous-ensemble des lignes d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="24327-309">This can be combined with the `range` and other query options that select a subset of the lines of a file.</span></span>
    * <span data-ttu-id="24327-310">`outdent`: `?outdent=8` Inverse l’indentation des lignes d’un certain nombre d’espaces ; dans ce cas, de 8 espaces.</span><span class="sxs-lookup"><span data-stu-id="24327-310">`outdent`: `?outdent=8` Reverses the indent of the lines by a number of spaces--in this case, 8.</span></span> <span data-ttu-id="24327-311">Ceci peut être combiné avec `range` et d’autres options de requête qui sélectionnent un sous-ensemble des lignes d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="24327-311">This can be combined with `range` and other query options that select a subset of the lines of a file.</span></span>

<span data-ttu-id="24327-312">Nous vous recommandons d’utiliser l’option du nom d’étiquette dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="24327-312">We recommend using the tag name option whenever possible.</span></span> <span data-ttu-id="24327-313">Le nom d’étiquette est le nom d’une région ou d’un commentaire du code au format `Snippettagname` présent dans le code source.</span><span class="sxs-lookup"><span data-stu-id="24327-313">The tag name is the name of a region or of a code comment in the format of `Snippettagname` present in the source code.</span></span> <span data-ttu-id="24327-314">L’exemple suivant montre comment référencer le nom d’étiquette `1` :</span><span class="sxs-lookup"><span data-stu-id="24327-314">The following example shows how to refer to the tag name `1`:</span></span>

```markdown
[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]
```

<span data-ttu-id="24327-315">Vous pouvez voir comment les étiquettes d’extrait de code sont structurées dans [ce fichier source](https://github.com/dotnet/samples/blob/master/snippets/csharp/language-reference/keywords/throw/throw-1.cs).</span><span class="sxs-lookup"><span data-stu-id="24327-315">And you can see how the snippet tags are structured in [this source file](https://github.com/dotnet/samples/blob/master/snippets/csharp/language-reference/keywords/throw/throw-1.cs).</span></span> <span data-ttu-id="24327-316">Pour plus d’informations sur la représentation des noms d’étiquette dans les fichiers sources d’extraits de code par langage, consultez les [Instructions pour DocFX](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#tag-name-representation-in-code-snippet-source-file).</span><span class="sxs-lookup"><span data-stu-id="24327-316">For details about tag name representation in code snippet source files by language, see the [DocFX guidelines](https://dotnet.github.io/docfx/spec/docfx_flavored_markdown.html#tag-name-representation-in-code-snippet-source-file).</span></span>

<span data-ttu-id="24327-317">L’ajout d’extraits de programmes complets garantit que tout le code s’exécute via notre système d’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="24327-317">Including snippets from full programs ensures that all code runs through our Continuous Integration (CI) system.</span></span> <span data-ttu-id="24327-318">Toutefois, si vous avez besoin d’afficher un élément qui entraîne des erreurs lors de la compilation ou de l’exécution, vous pouvez utiliser des blocs de code en ligne.</span><span class="sxs-lookup"><span data-stu-id="24327-318">However, if you need to show something that causes compile time or runtime errors, you can use inline code blocks.</span></span>

### <a name="inline-code-blocks-with-language-identifier"></a><span data-ttu-id="24327-319">Blocs de code en ligne avec identificateur de langage</span><span class="sxs-lookup"><span data-stu-id="24327-319">Inline code blocks with language identifier</span></span>

<span data-ttu-id="24327-320">Utilisez trois accents graves (\`\`\`) + un ID de langage pour appliquer un codage en couleurs spécifique au langage à un bloc de code.</span><span class="sxs-lookup"><span data-stu-id="24327-320">Use three backticks (\`\`\`) + a language ID to apply language-specific color coding to a code block.</span></span> <span data-ttu-id="24327-321">Voici la liste des langages pris en charge montrant l’étiquette Markdown pour chaque ID de langage.</span><span class="sxs-lookup"><span data-stu-id="24327-321">Here is the list of supported languages showing the markdown label for each language ID.</span></span>

#### <a name="supported-languages"></a><span data-ttu-id="24327-322">Langages pris en charge</span><span class="sxs-lookup"><span data-stu-id="24327-322">Supported languages</span></span>

|<span data-ttu-id="24327-323">Name</span><span class="sxs-lookup"><span data-stu-id="24327-323">Name</span></span>|<span data-ttu-id="24327-324">Étiquette Markdown</span><span class="sxs-lookup"><span data-stu-id="24327-324">Markdown label</span></span>|
|-----|-------|
|<span data-ttu-id="24327-325">ASP.NET avec C#</span><span class="sxs-lookup"><span data-stu-id="24327-325">ASP.NET with C#</span></span>|<span data-ttu-id="24327-326">aspx-csharp</span><span class="sxs-lookup"><span data-stu-id="24327-326">aspx-csharp</span></span>|
|<span data-ttu-id="24327-327">ASP.NET avec VB</span><span class="sxs-lookup"><span data-stu-id="24327-327">ASP.NET with VB</span></span>|<span data-ttu-id="24327-328">aspx-vb</span><span class="sxs-lookup"><span data-stu-id="24327-328">aspx-vb</span></span>|
|<span data-ttu-id="24327-329">D’Azure CLI</span><span class="sxs-lookup"><span data-stu-id="24327-329">Azure CLI</span></span>|<span data-ttu-id="24327-330">azurecli</span><span class="sxs-lookup"><span data-stu-id="24327-330">azurecli</span></span>|
|<span data-ttu-id="24327-331">AzCopy</span><span class="sxs-lookup"><span data-stu-id="24327-331">AzCopy</span></span>|<span data-ttu-id="24327-332">azcopy</span><span class="sxs-lookup"><span data-stu-id="24327-332">azcopy</span></span>|
|<span data-ttu-id="24327-333">C++</span><span class="sxs-lookup"><span data-stu-id="24327-333">C++</span></span>|<span data-ttu-id="24327-334">cpp</span><span class="sxs-lookup"><span data-stu-id="24327-334">cpp</span></span>|
|<span data-ttu-id="24327-335">C#</span><span class="sxs-lookup"><span data-stu-id="24327-335">C#</span></span>|<span data-ttu-id="24327-336">csharp</span><span class="sxs-lookup"><span data-stu-id="24327-336">csharp</span></span>|
|<span data-ttu-id="24327-337">C# dans un navigateur</span><span class="sxs-lookup"><span data-stu-id="24327-337">C# in browser</span></span>|<span data-ttu-id="24327-338">csharp-interactive</span><span class="sxs-lookup"><span data-stu-id="24327-338">csharp-interactive</span></span>|
|<span data-ttu-id="24327-339">Console</span><span class="sxs-lookup"><span data-stu-id="24327-339">Console</span></span>|<span data-ttu-id="24327-340">console</span><span class="sxs-lookup"><span data-stu-id="24327-340">console</span></span>|
|<span data-ttu-id="24327-341">F#</span><span class="sxs-lookup"><span data-stu-id="24327-341">F#</span></span>|<span data-ttu-id="24327-342">fsharp</span><span class="sxs-lookup"><span data-stu-id="24327-342">fsharp</span></span>|
|<span data-ttu-id="24327-343">Java</span><span class="sxs-lookup"><span data-stu-id="24327-343">Java</span></span>|<span data-ttu-id="24327-344">java</span><span class="sxs-lookup"><span data-stu-id="24327-344">java</span></span>|
|<span data-ttu-id="24327-345">JavaScript</span><span class="sxs-lookup"><span data-stu-id="24327-345">JavaScript</span></span>|<span data-ttu-id="24327-346">javascript</span><span class="sxs-lookup"><span data-stu-id="24327-346">javascript</span></span>|
|<span data-ttu-id="24327-347">JSON</span><span class="sxs-lookup"><span data-stu-id="24327-347">JSON</span></span>|<span data-ttu-id="24327-348">json</span><span class="sxs-lookup"><span data-stu-id="24327-348">json</span></span>|
|<span data-ttu-id="24327-349">NodeJS</span><span class="sxs-lookup"><span data-stu-id="24327-349">NodeJS</span></span>|<span data-ttu-id="24327-350">nodejs</span><span class="sxs-lookup"><span data-stu-id="24327-350">nodejs</span></span>|
|<span data-ttu-id="24327-351">Objective-C</span><span class="sxs-lookup"><span data-stu-id="24327-351">Objective-C</span></span>|<span data-ttu-id="24327-352">objc</span><span class="sxs-lookup"><span data-stu-id="24327-352">objc</span></span>|
|<span data-ttu-id="24327-353">PHP</span><span class="sxs-lookup"><span data-stu-id="24327-353">PHP</span></span>|<span data-ttu-id="24327-354">php</span><span class="sxs-lookup"><span data-stu-id="24327-354">php</span></span>|
|<span data-ttu-id="24327-355">PowerShell</span><span class="sxs-lookup"><span data-stu-id="24327-355">PowerShell</span></span>|<span data-ttu-id="24327-356">powershell</span><span class="sxs-lookup"><span data-stu-id="24327-356">powershell</span></span>|
|<span data-ttu-id="24327-357">Python</span><span class="sxs-lookup"><span data-stu-id="24327-357">Python</span></span>|<span data-ttu-id="24327-358">python</span><span class="sxs-lookup"><span data-stu-id="24327-358">python</span></span>|
|<span data-ttu-id="24327-359">Ruby</span><span class="sxs-lookup"><span data-stu-id="24327-359">Ruby</span></span>|<span data-ttu-id="24327-360">ruby</span><span class="sxs-lookup"><span data-stu-id="24327-360">ruby</span></span>|
|<span data-ttu-id="24327-361">SQL</span><span class="sxs-lookup"><span data-stu-id="24327-361">SQL</span></span>|<span data-ttu-id="24327-362">sql</span><span class="sxs-lookup"><span data-stu-id="24327-362">sql</span></span>|
|<span data-ttu-id="24327-363">Swift</span><span class="sxs-lookup"><span data-stu-id="24327-363">Swift</span></span>|<span data-ttu-id="24327-364">swift</span><span class="sxs-lookup"><span data-stu-id="24327-364">swift</span></span>|
|<span data-ttu-id="24327-365">VB</span><span class="sxs-lookup"><span data-stu-id="24327-365">VB</span></span>|<span data-ttu-id="24327-366">vb</span><span class="sxs-lookup"><span data-stu-id="24327-366">vb</span></span>|
|<span data-ttu-id="24327-367">XAML</span><span class="sxs-lookup"><span data-stu-id="24327-367">XAML</span></span>|<span data-ttu-id="24327-368">xaml</span><span class="sxs-lookup"><span data-stu-id="24327-368">xaml</span></span>|
|<span data-ttu-id="24327-369">XML</span><span class="sxs-lookup"><span data-stu-id="24327-369">XML</span></span>|<span data-ttu-id="24327-370">xml</span><span class="sxs-lookup"><span data-stu-id="24327-370">xml</span></span>|

<span data-ttu-id="24327-371">Le nom `csharp-interactive` spécifie le langage C# et la possibilité d’exécuter les exemples à partir du navigateur.</span><span class="sxs-lookup"><span data-stu-id="24327-371">The `csharp-interactive` name specifies the C# language, and the ability to run the samples from the browser.</span></span> <span data-ttu-id="24327-372">Ces extraits de code sont compilés et exécutés dans un conteneur Docker, et les résultats de l’exécution de ce programme sont affichés dans la fenêtre du navigateur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="24327-372">These snippets are compiled and executed in a Docker container, and the results of that program execution are displayed in the user's browser window.</span></span>

<span data-ttu-id="24327-373">Voici quelques exemples de blocs de code utilisant les ID de langage pour C# (\`\`\`csharp), Python (\`\`\`python) et PowerShell (\`\`\`powershell).</span><span class="sxs-lookup"><span data-stu-id="24327-373">The following are examples of code blocks using the language IDs for C# (\`\`\`csharp), Python (\`\`\`python), and PowerShell (\`\`\`powershell).</span></span>

##### <a name="c9839"></a><span data-ttu-id="24327-374">C&#9839;</span><span class="sxs-lookup"><span data-stu-id="24327-374">C&#9839;</span></span>

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

#### <a name="python"></a><span data-ttu-id="24327-375">Python</span><span class="sxs-lookup"><span data-stu-id="24327-375">Python</span></span>

```python
friends = ['john', 'pat', 'gary', 'michael']
for i, name in enumerate(friends):
    print "iteration {iteration} is {name}".format(iteration=i, name=name)
```

#### <a name="powershell"></a><span data-ttu-id="24327-376">PowerShell</span><span class="sxs-lookup"><span data-stu-id="24327-376">PowerShell</span></span>

```powershell
Clear-Host
$Directory = "C:\Windows\"
$Files = Get-Childitem $Directory -recurse -Include *.log `
-ErrorAction SilentlyContinue
```

### <a name="generic-code-block"></a><span data-ttu-id="24327-377">Bloc de code générique</span><span class="sxs-lookup"><span data-stu-id="24327-377">Generic code block</span></span>

<span data-ttu-id="24327-378">Utilisez trois accents graves (&#96;&#96;&#96;) pour le codage de bloc de code générique.</span><span class="sxs-lookup"><span data-stu-id="24327-378">Use three backticks (&#96;&#96;&#96;) for generic code block coding.</span></span>

> <span data-ttu-id="24327-379">L’approche recommandée consiste à utiliser des blocs de code avec les identificateurs de langage, comme expliqué dans la section précédente, pour garantir la coloration syntaxique appropriée sur le site de documentation.</span><span class="sxs-lookup"><span data-stu-id="24327-379">The recommended approach is to use code blocks with language identifiers as explained in the previous section to ensure the proper syntax highlighting in the documentation site.</span></span> <span data-ttu-id="24327-380">Utilisez des blocs de code générique uniquement si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="24327-380">Use generic code blocks only when necessary.</span></span>

```
function fancyAlert(arg) {
    if(arg) {
        $.docs({div:'#foo'})
    }
}
```

## <a name="blockquotes"></a><span data-ttu-id="24327-381">Éléments blockquote</span><span class="sxs-lookup"><span data-stu-id="24327-381">Blockquotes</span></span>

> <span data-ttu-id="24327-382">La sécheresse durait maintenant depuis dix millions d’années et le règne des terribles lézards avait depuis longtemps pris fin.</span><span class="sxs-lookup"><span data-stu-id="24327-382">The drought had lasted now for ten million years, and the reign of the terrible lizards had long since ended.</span></span> <span data-ttu-id="24327-383">Ici, à l’équateur, sur le continent qui s’appellerait un jour l’Afrique, la lutte pour l’existence avait atteint un nouveau sommet dans la férocité, et le vainqueur n’était pas encore connu.</span><span class="sxs-lookup"><span data-stu-id="24327-383">Here on the Equator, in the continent which would one day be known as Africa, the battle for existence had reached a new climax of ferocity, and the victor was not yet in sight.</span></span> <span data-ttu-id="24327-384">Dans ce territoire aride et désolé, seul le plus petit, le plus rapide ou le plus puissant pouvait croître et espérer survivre.</span><span class="sxs-lookup"><span data-stu-id="24327-384">In this barren and desiccated land, only the small or the swift or the fierce could flourish, or even hope to survive.</span></span>

## <a name="images"></a><span data-ttu-id="24327-385">Images</span><span class="sxs-lookup"><span data-stu-id="24327-385">Images</span></span>

### <a name="static-image-or-animated-gif"></a><span data-ttu-id="24327-386">Image statique ou GIF animée</span><span class="sxs-lookup"><span data-stu-id="24327-386">Static Image or Animated gif</span></span>

```markdown
![this is the alt text](../images/Logo_DotNet.png)
```

![il s’agit du texte de remplacement](../images/Logo_DotNet.png)

### <a name="linked-image"></a><span data-ttu-id="24327-388">Image liée</span><span class="sxs-lookup"><span data-stu-id="24327-388">Linked Image</span></span>

```markdown
[![alt text for linked image](../images/Logo_DotNet.png)](https://dot.net)
```

<span data-ttu-id="24327-389">[![texte de remplacement pour l’image liée](../images/Logo_DotNet.png)](https://dot.net)</span><span class="sxs-lookup"><span data-stu-id="24327-389">[![alt text for linked image](../images/Logo_DotNet.png)](https://dot.net)</span></span>

## <a name="videos"></a><span data-ttu-id="24327-390">Vidéos</span><span class="sxs-lookup"><span data-stu-id="24327-390">Videos</span></span>

<span data-ttu-id="24327-391">Actuellement, vous pouvez incorporer des vidéos Channel 9 et YouTube avec la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="24327-391">Currently, you can embed both Channel 9 and YouTube videos with the following syntax:</span></span>

### <a name="channel-9"></a><span data-ttu-id="24327-392">Channel 9</span><span class="sxs-lookup"><span data-stu-id="24327-392">Channel 9</span></span>

```markdown
> [!VIDEO <channel9_video_link>]
```

<span data-ttu-id="24327-393">Pour obtenir l’URL correcte de la vidéo, sélectionnez l’onglet **Incorporer** sous la trame vidéo, puis copiez l’URL à partir de l’élément `<iframe>`.</span><span class="sxs-lookup"><span data-stu-id="24327-393">To get the video's correct URL, select the **Embed** tab below the video frame, and copy the URL from the `<iframe>` element.</span></span> <span data-ttu-id="24327-394">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="24327-394">For example:</span></span>

```markdown
> [!VIDEO https://channel9.msdn.com/Blogs/dotnet/NET-Core-20-Released/player]
```

### <a name="youtube"></a><span data-ttu-id="24327-395">YouTube</span><span class="sxs-lookup"><span data-stu-id="24327-395">YouTube</span></span>

<span data-ttu-id="24327-396">Pour obtenir l’URL correcte de la vidéo, cliquez avec le bouton droit sur la vidéo, sélectionnez **Copier le code incorporé**, puis copiez l’URL à partir de l’élément `<iframe>`.</span><span class="sxs-lookup"><span data-stu-id="24327-396">To get the video's correct URL, right-click on the video, select **Copy Embed Code**, and copy the URL from the `<iframe>` element.</span></span>

```markdown
> [!VIDEO <youtube_video_link>]
```

<span data-ttu-id="24327-397">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="24327-397">For example:</span></span>

```markdown
> [!VIDEO https://www.youtube.com/embed/Q2mMbjw6cLA]
```

## <a name="docsmicrosoft-extensions"></a><span data-ttu-id="24327-398">extensions docs.microsoft</span><span class="sxs-lookup"><span data-stu-id="24327-398">docs.microsoft extensions</span></span>

<span data-ttu-id="24327-399">docs.microsoft fournit quelques extensions supplémentaires à GitHub Flavored Markdown.</span><span class="sxs-lookup"><span data-stu-id="24327-399">docs.microsoft provides a few additional extensions to GitHub Flavored Markdown.</span></span>

### <a name="alerts"></a><span data-ttu-id="24327-400">Alertes</span><span class="sxs-lookup"><span data-stu-id="24327-400">Alerts</span></span>

<span data-ttu-id="24327-401">Il est important d’utiliser les styles d’alerte suivants pour un rendu avec le style approprié sur le site de documentation.</span><span class="sxs-lookup"><span data-stu-id="24327-401">It's important to use the following alert styles so they render with the proper style in the documentation site.</span></span> <span data-ttu-id="24327-402">Toutefois, le moteur de rendu sur GitHub ne les différencie pas.</span><span class="sxs-lookup"><span data-stu-id="24327-402">However, the rendering engine on GitHub doesn't diferentiate them.</span></span>

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

<span data-ttu-id="24327-403">Et tous seront rendus comme ceci : ![Styles d’alertes](../images/alerts.png)</span><span class="sxs-lookup"><span data-stu-id="24327-403">And they'll render like this: ![Alert styles](../images/alerts.png)</span></span>

### <a name="includes"></a><span data-ttu-id="24327-404">Inclut</span><span class="sxs-lookup"><span data-stu-id="24327-404">Includes</span></span>

<span data-ttu-id="24327-405">Vous pouvez incorporer le Markdown d’un fichier dans un autre en utilisant une instruction include.</span><span class="sxs-lookup"><span data-stu-id="24327-405">You can embed the Markdown of one file into another using an include.</span></span>

[!INCLUDE[sample include file](../includes/sampleinclude.md)]

### <a name="checked-lists"></a><span data-ttu-id="24327-406">Listes cochées</span><span class="sxs-lookup"><span data-stu-id="24327-406">Checked lists</span></span>

<span data-ttu-id="24327-407">Un style personnalisé est disponible pour les listes.</span><span class="sxs-lookup"><span data-stu-id="24327-407">A custom style is available for lists.</span></span> <span data-ttu-id="24327-408">Vous pouvez restituer des listes avec des coches vertes.</span><span class="sxs-lookup"><span data-stu-id="24327-408">You can render lists with green check marks.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="24327-409">Créer une application .NET Core</span><span class="sxs-lookup"><span data-stu-id="24327-409">How to create a .NET Core app</span></span>
> * <span data-ttu-id="24327-410">Ajouter une référence au package Microsoft.XmlSerializer.Generator</span><span class="sxs-lookup"><span data-stu-id="24327-410">How to add a reference to the Microsoft.XmlSerializer.Generator package</span></span>
> * <span data-ttu-id="24327-411">Modifier votre fichier MyApp.csproj pour ajouter des dépendances</span><span class="sxs-lookup"><span data-stu-id="24327-411">How to edit your MyApp.csproj to add dependencies</span></span>
> * <span data-ttu-id="24327-412">Ajouter une classe et un XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="24327-412">How to add a class and an XmlSerializer</span></span>
> * <span data-ttu-id="24327-413">Générer et exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="24327-413">How to build and run the application</span></span>

<span data-ttu-id="24327-414">Vous pouvez voir un exemple de listes cochées dans action dans les [documents .NET Core](https://docs.microsoft.com/dotnet/core/additional-tools/xml-serializer-generator).</span><span class="sxs-lookup"><span data-stu-id="24327-414">You can see an example of checked lists in action in the [.NET Core docs](https://docs.microsoft.com/dotnet/core/additional-tools/xml-serializer-generator).</span></span>

### <a name="buttons"></a><span data-ttu-id="24327-415">Boutons</span><span class="sxs-lookup"><span data-stu-id="24327-415">Buttons</span></span>

> [!div class="button"]
> [<span data-ttu-id="24327-416">Liens de boutons</span><span class="sxs-lookup"><span data-stu-id="24327-416">button links</span></span>](../docs/core/index.md)

<span data-ttu-id="24327-417">Vous pouvez voir un exemple de boutons en action dans les [documents Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio#step-2---download-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="24327-417">You can see an example of buttons in action in the [Visual Studio docs](https://docs.microsoft.com/visualstudio/install/install-visual-studio#step-2---download-visual-studio).</span></span>

### <a name="selectors"></a><span data-ttu-id="24327-418">Sélecteurs</span><span class="sxs-lookup"><span data-stu-id="24327-418">Selectors</span></span>

> [!div class="op_single_selector"]
- [<span data-ttu-id="24327-419">macOS</span><span class="sxs-lookup"><span data-stu-id="24327-419">macOS</span></span>](../docs/core/tutorials/using-on-macos.md)
- [<span data-ttu-id="24327-420">Fenêtres</span><span class="sxs-lookup"><span data-stu-id="24327-420">Windows</span></span>](../docs/core/tutorials/with-visual-studio.md)

<span data-ttu-id="24327-421">Vous pouvez voir un exemple de sélecteurs en action dans les [documents Azure](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-classic).</span><span class="sxs-lookup"><span data-stu-id="24327-421">You can see an example of selectors in action at the [Azure docs](https://docs.microsoft.com/azure/expressroute/expressroute-howto-circuit-classic).</span></span>

### <a name="step-by-steps"></a><span data-ttu-id="24327-422">Procédures détaillées</span><span class="sxs-lookup"><span data-stu-id="24327-422">Step-By-Steps</span></span>

>[!div class="step-by-step"]
>[Précédent](../docs/csharp/expression-trees-interpreting.md)
>[Suivant](../docs/csharp/expression-trees-translating.md)

<span data-ttu-id="24327-424">Vous pouvez voir un exemple de procédures pas à pas en action dans le [Guide C#](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/program-structure).</span><span class="sxs-lookup"><span data-stu-id="24327-424">You can see an example of step-by-steps in action at the [C# Guide](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/program-structure).</span></span>
