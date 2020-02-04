---
title: Documentation de votre code avec des commentaires XML
description: Découvrez comment documenter votre code avec des commentaires de documentation XML et générer un fichier de documentation XML au moment de la compilation.
ms.date: 01/21/2020
ms.technology: csharp-fundamentals
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.openlocfilehash: 1ec088db1de7c953bdb20b1129c5fd40f9e31454
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965930"
---
# <a name="document-your-code-with-xml-comments"></a><span data-ttu-id="e8e18-103">Documenter votre code avec des commentaires XML</span><span class="sxs-lookup"><span data-stu-id="e8e18-103">Document your code with XML comments</span></span>

<span data-ttu-id="e8e18-104">Les commentaires de documentation XML sont un genre particulier de commentaire, ajouté au-dessus de la définition d’un type ou d’un membre défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e8e18-104">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span>
<span data-ttu-id="e8e18-105">Ils sont spéciaux, car ils peuvent être traités par le compilateur pour générer un fichier de documentation XML au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e8e18-105">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="e8e18-106">Le fichier XML généré par le compilateur peut être distribué avec votre assembly .NET afin que Visual Studio et d’autres IDE puissent utiliser IntelliSense pour afficher des informations rapides sur les types ou les membres.</span><span class="sxs-lookup"><span data-stu-id="e8e18-106">The compiler-generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="e8e18-107">De plus, le fichier XML peut être exécuté par l’intermédiaire d’outils tels que [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) pour générer des sites web de références d’API.</span><span class="sxs-lookup"><span data-stu-id="e8e18-107">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="e8e18-108">Les commentaires de documentation XML, comme tous les autres commentaires, sont ignorés par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="e8e18-108">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="e8e18-109">Vous pouvez générer le fichier XML au moment de la compilation en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="e8e18-109">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="e8e18-110">Si vous développez une application avec .NET Core à partir de la ligne de commande, vous pouvez ajouter un élément `GenerateDocumentationFile` à la section `<PropertyGroup>` de votre fichier projet. csproj.</span><span class="sxs-lookup"><span data-stu-id="e8e18-110">If you are developing an application with .NET Core from the command line, you can add a `GenerateDocumentationFile` element to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="e8e18-111">Vous pouvez également spécifier le chemin d’accès au fichier de documentation directement à l’aide de [`DocumentationFile` élément](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="e8e18-111">You can also specify the path to the documentation file directly using [`DocumentationFile` element](/visualstudio/msbuild/common-msbuild-project-properties).</span></span> <span data-ttu-id="e8e18-112">L’exemple suivant génère un fichier XML dans le répertoire du projet avec le même nom de fichier racine que l’assembly :</span><span class="sxs-lookup"><span data-stu-id="e8e18-112">The following example generates an XML file in the project directory with the same root filename as the assembly:</span></span>

   ```xml
   <GenerateDocumentationFile>true</GenerateDocumentationFile>
   ```
   
   <span data-ttu-id="e8e18-113">est équivalente à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="e8e18-113">This is equivalent to the following:</span></span>
   
   ```xml
   <DocumentationFile>bin\$(Configuration)\$(TargetFramework)\$(AssemblyName).xml</DocumentationFile>
   ```

- <span data-ttu-id="e8e18-114">Si vous développez une application à l’aide de Visual Studio, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e8e18-114">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="e8e18-115">Dans la boîte de dialogue des propriétés, sélectionnez l’onglet **Générer**, puis cochez **Fichier de documentation XML**.</span><span class="sxs-lookup"><span data-stu-id="e8e18-115">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="e8e18-116">Vous pouvez également changer l’emplacement dans lequel le compilateur écrit le fichier.</span><span class="sxs-lookup"><span data-stu-id="e8e18-116">You can also change the location to which the compiler writes the file.</span></span>

- <span data-ttu-id="e8e18-117">Si vous compilez une application .NET Framework à partir de la ligne de commande, ajoutez l' [option de compilateur-doc](language-reference/compiler-options/doc-compiler-option.md) lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="e8e18-117">If you are compiling a .NET Framework application from the command line, add the [-doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="e8e18-118">Les commentaires de documentation XML utilisent des barres obliques triples (`///`) et le corps d’un commentaire au format XML.</span><span class="sxs-lookup"><span data-stu-id="e8e18-118">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="e8e18-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e8e18-119">For example:</span></span>

[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]

## <a name="walkthrough"></a><span data-ttu-id="e8e18-120">Procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="e8e18-120">Walkthrough</span></span>

<span data-ttu-id="e8e18-121">Passons en revue la documentation d’une bibliothèque mathématique très basique pour permettre aux nouveaux développeurs de comprendre et de contribuer facilement et aux développeurs tiers de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="e8e18-121">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third-party developers to use.</span></span>

<span data-ttu-id="e8e18-122">Voici le code de la bibliothèque mathématique simple :</span><span class="sxs-lookup"><span data-stu-id="e8e18-122">Here's code for the simple math library:</span></span>

[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]

<span data-ttu-id="e8e18-123">L’exemple de bibliothèque prend en charge quatre opérations arithmétiques principales (`add`, `subtract`, `multiply`et `divide`) sur les types de données `int` et `double`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-123">The sample library supports four major arithmetic operations (`add`, `subtract`, `multiply`, and `divide`) on `int` and `double` data types.</span></span>

<span data-ttu-id="e8e18-124">Vous souhaitez maintenant être en mesure de créer un document de référence d’API à partir de votre code pour les développeurs tiers qui utilisent votre bibliothèque, mais n’ont pas accès au code source.</span><span class="sxs-lookup"><span data-stu-id="e8e18-124">Now you want to be able to create an API reference document from your code for third-party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="e8e18-125">Comme nous l’avons déjà mentionné, vous pouvez pour cela utiliser les balises de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="e8e18-125">As mentioned earlier XML documentation tags can be used to achieve this.</span></span> <span data-ttu-id="e8e18-126">Vous allez maintenant découvrir les balises XML standard prises en charge par le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="e8e18-126">You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

## <a name="summary"></a><span data-ttu-id="e8e18-127">\<summary></span><span class="sxs-lookup"><span data-stu-id="e8e18-127">\<summary></span></span>

<span data-ttu-id="e8e18-128">La balise `<summary>` ajoute des informations succinctes relatives à un type ou un membre.</span><span class="sxs-lookup"><span data-stu-id="e8e18-128">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="e8e18-129">Je vais expliquer son utilisation en l’ajoutant à la définition de la classe `Math` et à la première méthode `Add`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-129">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="e8e18-130">N’hésitez pas à l’appliquer au reste de votre code.</span><span class="sxs-lookup"><span data-stu-id="e8e18-130">Feel free to apply it to the rest of your code.</span></span>

[!code-csharp[Summary Tag](~/samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]

<span data-ttu-id="e8e18-131">La balise `<summary>` est importante et nous vous recommandons de l’inclure, car son contenu est la principale source d’informations sur les types ou les membres dans IntelliSense ou un document de référence sur les API.</span><span class="sxs-lookup"><span data-stu-id="e8e18-131">The `<summary>` tag is important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

## <a name="remarks"></a><span data-ttu-id="e8e18-132">\<remarks></span><span class="sxs-lookup"><span data-stu-id="e8e18-132">\<remarks></span></span>

<span data-ttu-id="e8e18-133">La balise `<remarks>` complète les informations relatives aux types ou aux membres fournies par la balise `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-133">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="e8e18-134">Dans cet exemple, vous allez simplement l’ajouter à la classe.</span><span class="sxs-lookup"><span data-stu-id="e8e18-134">In this example, you'll just add it to the class.</span></span>

[!code-csharp[Remarks Tag](~/samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]

## <a name="returns"></a><span data-ttu-id="e8e18-135">\<returns></span><span class="sxs-lookup"><span data-stu-id="e8e18-135">\<returns></span></span>

<span data-ttu-id="e8e18-136">La balise `<returns>` décrit la valeur de retour d’une déclaration de méthode.</span><span class="sxs-lookup"><span data-stu-id="e8e18-136">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="e8e18-137">Comme auparavant, l’exemple suivant illustre la balise `<returns>` sur la première méthode `Add`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-137">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="e8e18-138">Vous pouvez effectuer la même opération sur d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="e8e18-138">You can do the same on other methods.</span></span>

[!code-csharp[Returns Tag](~/samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]

## <a name="value"></a><span data-ttu-id="e8e18-139">\<valeur></span><span class="sxs-lookup"><span data-stu-id="e8e18-139">\<value></span></span>

<span data-ttu-id="e8e18-140">La balise `<value>` est similaire à la balise `<returns>`, excepté que vous l’utilisez pour les propriétés.</span><span class="sxs-lookup"><span data-stu-id="e8e18-140">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="e8e18-141">En supposant que votre bibliothèque `Math` a une propriété statique appelée `PI`, voici comment utiliser cette balise :</span><span class="sxs-lookup"><span data-stu-id="e8e18-141">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

[!code-csharp[Value Tag](~/samples/snippets/csharp/concepts/codedoc/value-tag.cs)]

## <a name="example"></a><span data-ttu-id="e8e18-142">\<example></span><span class="sxs-lookup"><span data-stu-id="e8e18-142">\<example></span></span>

<span data-ttu-id="e8e18-143">La balise `<example>` permet d’inclure un exemple de votre documentation XML.</span><span class="sxs-lookup"><span data-stu-id="e8e18-143">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="e8e18-144">Cela implique l’utilisation de la balise enfant `<code>`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-144">This involves using the child `<code>` tag.</span></span>

[!code-csharp[Example Tag](~/samples/snippets/csharp/concepts/codedoc/example-tag.cs)]

<span data-ttu-id="e8e18-145">La balise `code` conserve les sauts de ligne et la mise en retrait pour les exemples plus longs.</span><span class="sxs-lookup"><span data-stu-id="e8e18-145">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

## <a name="para"></a><span data-ttu-id="e8e18-146">\<para></span><span class="sxs-lookup"><span data-stu-id="e8e18-146">\<para></span></span>

<span data-ttu-id="e8e18-147">La balise `<para>` permet de mettre en forme le contenu de sa balise parente.</span><span class="sxs-lookup"><span data-stu-id="e8e18-147">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="e8e18-148">`<para>` est généralement utilisée dans une balise, telle que `<remarks>` ou `<returns>`, pour diviser du texte en paragraphes.</span><span class="sxs-lookup"><span data-stu-id="e8e18-148">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="e8e18-149">Vous pouvez mettre en forme le contenu de la balise `<remarks>` pour la définition de votre classe.</span><span class="sxs-lookup"><span data-stu-id="e8e18-149">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

[!code-csharp[Para Tag](~/samples/snippets/csharp/concepts/codedoc/para-tag.cs)]

## <a name="c"></a><span data-ttu-id="e8e18-150">\<c></span><span class="sxs-lookup"><span data-stu-id="e8e18-150">\<c></span></span>

<span data-ttu-id="e8e18-151">Toujours concernant la mise en forme, vous utilisez la balise `<c>` pour le marquage d’une partie du texte comme code.</span><span class="sxs-lookup"><span data-stu-id="e8e18-151">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="e8e18-152">Elle est semblable à la balise `<code>`, mais inline.</span><span class="sxs-lookup"><span data-stu-id="e8e18-152">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="e8e18-153">Elle est utile quand vous voulez afficher un exemple de code rapide comme partie du contenu d’une balise.</span><span class="sxs-lookup"><span data-stu-id="e8e18-153">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="e8e18-154">Mettons à jour la documentation de la classe `Math`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-154">Let's update the documentation for the `Math` class.</span></span>

[!code-csharp[C Tag](~/samples/snippets/csharp/concepts/codedoc/c-tag.cs)]

## <a name="exception"></a><span data-ttu-id="e8e18-155">\<exception></span><span class="sxs-lookup"><span data-stu-id="e8e18-155">\<exception></span></span>

<span data-ttu-id="e8e18-156">En utilisant la balise `<exception>`, vous informez vos développeurs qu’une méthode peut lever des exceptions spécifiques.</span><span class="sxs-lookup"><span data-stu-id="e8e18-156">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="e8e18-157">Si vous examinez votre bibliothèque `Math`, vous pouvez voir que les deux méthodes `Add` lèvent une exception si une certaine condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="e8e18-157">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="e8e18-158">Il est toutefois moins évident de voir que la méthode `Divide` utilisée avec un entier lève également une exception si le paramètre `b` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="e8e18-158">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="e8e18-159">Ajoutez maintenant une documentation d’exception à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="e8e18-159">Now add exception documentation to this method.</span></span>

[!code-csharp[Exception Tag](~/samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]

<span data-ttu-id="e8e18-160">L’attribut `cref` référence une exception qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="e8e18-160">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="e8e18-161">Il peut s’agir de tout type défini dans le projet ou dans un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="e8e18-161">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="e8e18-162">Le compilateur émet un avertissement si sa valeur ne peut pas être résolue.</span><span class="sxs-lookup"><span data-stu-id="e8e18-162">The compiler will issue a warning if its value cannot be resolved.</span></span>

## <a name="see"></a><span data-ttu-id="e8e18-163">\<see></span><span class="sxs-lookup"><span data-stu-id="e8e18-163">\<see></span></span>

<span data-ttu-id="e8e18-164">La balise `<see>` vous permet de créer un lien interactif vers une page de documentation pour un autre élément de code.</span><span class="sxs-lookup"><span data-stu-id="e8e18-164">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="e8e18-165">Dans notre prochain exemple, nous allons créer un lien interactif entre les deux méthodes `Add`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-165">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

[!code-csharp[See Tag](~/samples/snippets/csharp/concepts/codedoc/see-tag.cs)]

<span data-ttu-id="e8e18-166">`cref` est un attribut **obligatoire** qui représente une référence à un type ou à ses membres et qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="e8e18-166">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="e8e18-167">Il peut s’agir de tout type défini dans le projet ou dans un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="e8e18-167">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="seealso"></a><span data-ttu-id="e8e18-168">\<seealso></span><span class="sxs-lookup"><span data-stu-id="e8e18-168">\<seealso></span></span>

<span data-ttu-id="e8e18-169">Vous pouvez utiliser la balise `<seealso>` de la même façon que la balise `<see>`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-169">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="e8e18-170">La seule différence est que son contenu est généralement placé dans une section "Voir aussi".</span><span class="sxs-lookup"><span data-stu-id="e8e18-170">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="e8e18-171">Ici, nous allons ajouter une balise `seealso` sous la méthode `Add` utilisée avec un entier pour référencer d’autres méthodes de la classe qui acceptent des paramètres entiers :</span><span class="sxs-lookup"><span data-stu-id="e8e18-171">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

[!code-csharp[Seealso Tag](~/samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]

<span data-ttu-id="e8e18-172">L’attribut `cref` représente une référence à un type ou à ses membres et est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="e8e18-172">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="e8e18-173">Il peut s’agir de tout type défini dans le projet ou dans un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="e8e18-173">This can be any type defined in the project or a referenced assembly.</span></span>

## <a name="param"></a><span data-ttu-id="e8e18-174">\<param></span><span class="sxs-lookup"><span data-stu-id="e8e18-174">\<param></span></span>

<span data-ttu-id="e8e18-175">La balise `<param>` permet de décrire les paramètres d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="e8e18-175">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="e8e18-176">Voici un exemple de la méthode double `Add` : le paramètre que la balise décrit est spécifié dans l’attribut `name` **requis** .</span><span class="sxs-lookup"><span data-stu-id="e8e18-176">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Param Tag](~/samples/snippets/csharp/concepts/codedoc/param-tag.cs)]

## <a name="typeparam"></a><span data-ttu-id="e8e18-177">\<typeparam></span><span class="sxs-lookup"><span data-stu-id="e8e18-177">\<typeparam></span></span>

<span data-ttu-id="e8e18-178">Vous utilisez la balise `<typeparam>` exactement comme la balise `<param>`, mais pour permettre aux déclarations de types ou de méthodes génériques de décrire un paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="e8e18-178">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="e8e18-179">Ajoutez une méthode générique rapide à votre classe `Math` pour vérifier si une quantité est supérieure à une autre.</span><span class="sxs-lookup"><span data-stu-id="e8e18-179">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

[!code-csharp[Typeparam Tag](~/samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]

## <a name="paramref"></a><span data-ttu-id="e8e18-180">\<paramref></span><span class="sxs-lookup"><span data-stu-id="e8e18-180">\<paramref></span></span>

<span data-ttu-id="e8e18-181">Alors que vous décrivez ce que fait une méthode dans ce qui pourrait être une balise `<summary>`, vous souhaiterez peut-être créer une référence à un paramètre.</span><span class="sxs-lookup"><span data-stu-id="e8e18-181">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="e8e18-182">La balise `<paramref>` est idéale pour cette tâche précise.</span><span class="sxs-lookup"><span data-stu-id="e8e18-182">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="e8e18-183">Mettons à jour le récapitulatif de notre méthode `Add` double.</span><span class="sxs-lookup"><span data-stu-id="e8e18-183">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="e8e18-184">À l’instar de la balise `<param>`, le nom du paramètre est spécifié dans l’attribut `name` **requis** .</span><span class="sxs-lookup"><span data-stu-id="e8e18-184">Like the `<param>` tag, the parameter name is specified in the **required** `name` attribute.</span></span>

[!code-csharp[Paramref Tag](~/samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]

## <a name="typeparamref"></a><span data-ttu-id="e8e18-185">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="e8e18-185">\<typeparamref></span></span>

<span data-ttu-id="e8e18-186">Vous utilisez la balise `<typeparamref>` exactement comme la balise `<paramref>`, mais pour permettre aux déclarations de types ou de méthodes génériques de décrire un paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="e8e18-186">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="e8e18-187">Vous pouvez utiliser la même méthode générique que celle créée précédemment.</span><span class="sxs-lookup"><span data-stu-id="e8e18-187">You can use the same generic method you previously created.</span></span>

[!code-csharp[Typeparamref Tag](~/samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]

## <a name="list"></a><span data-ttu-id="e8e18-188">\<list></span><span class="sxs-lookup"><span data-stu-id="e8e18-188">\<list></span></span>

<span data-ttu-id="e8e18-189">Vous utilisez la balise `<list>` pour mettre en forme les informations de documentation sous la forme d’une liste triée, d’une liste non triée ou d’une table.</span><span class="sxs-lookup"><span data-stu-id="e8e18-189">You use the `<list>` tag to format documentation information as an ordered list, unordered list, or table.</span></span> <span data-ttu-id="e8e18-190">Créez une liste non triée de toutes les opérations mathématiques prises en charge par votre bibliothèque `Math`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-190">Make an unordered list of every math operation your `Math` library supports.</span></span>

[!code-csharp[List Tag](~/samples/snippets/csharp/concepts/codedoc/list-tag.cs)]

<span data-ttu-id="e8e18-191">Vous pouvez créer une liste triée ou un tableau en remplaçant l’attribut `type` par `number` ou `table`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="e8e18-191">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

## <a name="inheritdoc"></a><span data-ttu-id="e8e18-192">\<inheritdoc ></span><span class="sxs-lookup"><span data-stu-id="e8e18-192">\<inheritdoc></span></span>

<span data-ttu-id="e8e18-193">Vous pouvez utiliser la balise `<inheritdoc>` pour hériter des commentaires XML des classes de base, des interfaces et des méthodes similaires.</span><span class="sxs-lookup"><span data-stu-id="e8e18-193">You can use the `<inheritdoc>` tag to inherit XML comments from base classes, interfaces, and similar methods.</span></span> <span data-ttu-id="e8e18-194">Cela élimine la copie et le collage indésirables de commentaires XML en double et conserve automatiquement les commentaires XML synchronisés.</span><span class="sxs-lookup"><span data-stu-id="e8e18-194">This eliminates unwanted copying and pasting of duplicate XML comments and automatically keeps XML comments synchronized.</span></span>

[!code-csharp-interactive[InheritDoc Tag](~/samples/snippets/csharp/concepts/codedoc/inheritdoc-tag.cs)]

### <a name="put-it-all-together"></a><span data-ttu-id="e8e18-195">Rassemblez tous les éléments</span><span class="sxs-lookup"><span data-stu-id="e8e18-195">Put it all together</span></span>

<span data-ttu-id="e8e18-196">Si vous avez suivi ce didacticiel et appliqué les balises à votre code au besoin, votre code doit maintenant ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e8e18-196">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

[!code-csharp[Tagged Library](~/samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]

<span data-ttu-id="e8e18-197">À partir de votre code, vous pouvez générer un site web de documentation détaillée complet avec des références croisées interactives.</span><span class="sxs-lookup"><span data-stu-id="e8e18-197">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="e8e18-198">Vous êtes maintenant confronté à un autre problème : votre code est devenu difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="e8e18-198">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="e8e18-199">Avec toutes ces informations à parcourir, cela va être un cauchemar pour les développeurs qui veulent contribuer à ce code.</span><span class="sxs-lookup"><span data-stu-id="e8e18-199">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span>
<span data-ttu-id="e8e18-200">Heureusement, il existe une balise XML qui peut vous aider à gérer ce problème :</span><span class="sxs-lookup"><span data-stu-id="e8e18-200">Thankfully there's an XML tag that can help you deal with this:</span></span>

## <a name="include"></a><span data-ttu-id="e8e18-201">\<include></span><span class="sxs-lookup"><span data-stu-id="e8e18-201">\<include></span></span>

<span data-ttu-id="e8e18-202">La balise `<include>` vous permet de faire référence à des commentaires se trouvant dans un fichier XML distinct et décrivant les types et les membres de votre code source au lieu de placer des commentaires de documentation directement dans votre fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="e8e18-202">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="e8e18-203">Vous allez maintenant déplacer toutes vos balises XML dans un fichier XML distinct nommé `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-203">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="e8e18-204">Vous pouvez nommer ce fichier comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="e8e18-204">Feel free to name the file whatever you want.</span></span>

[!code-xml[Sample XML](~/samples/snippets/csharp/concepts/codedoc/include.xml)]

<span data-ttu-id="e8e18-205">Dans le code XML ci-dessus, les commentaires de documentation de chaque membre apparaissent directement dans une balise nommée en fonction de ce qu’il fait.</span><span class="sxs-lookup"><span data-stu-id="e8e18-205">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="e8e18-206">Vous pouvez choisir votre propre stratégie.</span><span class="sxs-lookup"><span data-stu-id="e8e18-206">You can choose your own strategy.</span></span>
<span data-ttu-id="e8e18-207">Maintenant que vous avez vos commentaires XML dans un fichier distinct, voyons comment votre code peut être rendu plus lisible à l’aide de la balise `<include>` :</span><span class="sxs-lookup"><span data-stu-id="e8e18-207">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

[!code-csharp[Include Tag](~/samples/snippets/csharp/concepts/codedoc/include-tag.cs)]

<span data-ttu-id="e8e18-208">Et voilà : notre code est à nouveau lisible, et aucune information de documentation n’a été perdue.</span><span class="sxs-lookup"><span data-stu-id="e8e18-208">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span>

<span data-ttu-id="e8e18-209">L’attribut `file` représente le nom du fichier XML contenant la documentation.</span><span class="sxs-lookup"><span data-stu-id="e8e18-209">The `file` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="e8e18-210">L’attribut `path` représente une requête [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) au `tag name` présent dans le `file` spécifié.</span><span class="sxs-lookup"><span data-stu-id="e8e18-210">The `path` attribute represents an [XPath](../standard/data/xml/xpath-queries-and-namespaces.md) query to the `tag name` present in the specified `file`.</span></span>

<span data-ttu-id="e8e18-211">L’attribut `name` représente le spécificateur de nom dans la balise qui précède les commentaires.</span><span class="sxs-lookup"><span data-stu-id="e8e18-211">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="e8e18-212">L’attribut `id`, qui peut être utilisé à la place de `name`, représente l’ID de la balise qui précède les commentaires.</span><span class="sxs-lookup"><span data-stu-id="e8e18-212">The `id` attribute, which can be used in place of `name`, represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="e8e18-213">Balises définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="e8e18-213">User-defined tags</span></span>

<span data-ttu-id="e8e18-214">Toutes les balises décrites ci-dessus représentent celles qui sont reconnues par le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="e8e18-214">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="e8e18-215">Toutefois, un utilisateur est libre de définir ses propres balises.</span><span class="sxs-lookup"><span data-stu-id="e8e18-215">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="e8e18-216">Les outils tels que Sandcastle apportent la prise en charge de balises supplémentaires telles que [\<événement >](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) et [\<note >](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), et même prendre en charge la [documentation des espaces de noms](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="e8e18-216">Tools like Sandcastle bring support for extra tags like [\<event>](https://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm) and [\<note>](https://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm), and even support [documenting namespaces](https://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="e8e18-217">Des outils de génération de documentation personnalisés ou internes peuvent également être utilisés avec les balises standard, et plusieurs formats de sortie, du format HTML au format PDF, peuvent être pris en charge.</span><span class="sxs-lookup"><span data-stu-id="e8e18-217">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="e8e18-218">Recommandations</span><span class="sxs-lookup"><span data-stu-id="e8e18-218">Recommendations</span></span>

<span data-ttu-id="e8e18-219">La documentation du code est recommandée pour de nombreuses raisons.</span><span class="sxs-lookup"><span data-stu-id="e8e18-219">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="e8e18-220">Voici quelques bonnes pratiques, des scénarios de cas d’usage généraux et des éléments que vous devez connaître quand vous utilisez des balises de documentation XML dans votre code C#.</span><span class="sxs-lookup"><span data-stu-id="e8e18-220">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

- <span data-ttu-id="e8e18-221">Par souci de cohérence, tous les types visibles publiquement et leurs membres doivent être documentés.</span><span class="sxs-lookup"><span data-stu-id="e8e18-221">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="e8e18-222">Si vous devez le faire, faites-le complètement.</span><span class="sxs-lookup"><span data-stu-id="e8e18-222">If you must do it, do it all.</span></span>
- <span data-ttu-id="e8e18-223">Les membres privés peuvent également être documentés à l’aide de commentaires XML.</span><span class="sxs-lookup"><span data-stu-id="e8e18-223">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="e8e18-224">Toutefois, cela expose le fonctionnement interne (potentiellement confidentiel) de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="e8e18-224">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
- <span data-ttu-id="e8e18-225">Au minimum, les types et leurs membres doivent avoir une balise `<summary>`, car son contenu est nécessaire pour IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e8e18-225">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
- <span data-ttu-id="e8e18-226">Le texte de la documentation doit être écrit à l’aide de phrases complètes se terminant par un point.</span><span class="sxs-lookup"><span data-stu-id="e8e18-226">Documentation text should be written using complete sentences ending with full stops.</span></span>
- <span data-ttu-id="e8e18-227">Les classes partielles sont entièrement prises en charge, et les informations de documentation seront concaténées dans une seule entrée pour ce type.</span><span class="sxs-lookup"><span data-stu-id="e8e18-227">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
- <span data-ttu-id="e8e18-228">Le compilateur vérifie la syntaxe des balises `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`et `<typeparam>`.</span><span class="sxs-lookup"><span data-stu-id="e8e18-228">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>`, and `<typeparam>` tags.</span></span>
- <span data-ttu-id="e8e18-229">Le compilateur valide les paramètres qui contiennent des chemins de fichiers et des références à d’autres parties du code.</span><span class="sxs-lookup"><span data-stu-id="e8e18-229">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8e18-230">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8e18-230">See also</span></span>

- [<span data-ttu-id="e8e18-231">Commentaires de documentation XML (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e8e18-231">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/index.md)
- [<span data-ttu-id="e8e18-232">Balises recommandées pour les commentaires de documentation (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e8e18-232">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
