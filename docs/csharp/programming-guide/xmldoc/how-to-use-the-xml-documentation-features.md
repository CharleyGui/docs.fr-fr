---
title: Guide pratique pour utiliser les fonctionnalités de la documentation XML-Guide de programmation C#
ms.date: 06/01/2018
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: b7c5a8a895271f067505496c0d13f98b66a393d9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287361"
---
# <a name="how-to-use-the-xml-documentation-features"></a><span data-ttu-id="98169-102">Comment utiliser les fonctionnalités de la documentation XML</span><span class="sxs-lookup"><span data-stu-id="98169-102">How to use the XML documentation features</span></span>

<span data-ttu-id="98169-103">L’exemple suivant montre un type qui a été documenté.</span><span class="sxs-lookup"><span data-stu-id="98169-103">The following sample provides a basic overview of a type that has been documented.</span></span>

## <a name="example"></a><span data-ttu-id="98169-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="98169-104">Example</span></span>

[!code-csharp[csProgGuideDocComments#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#15)]

<span data-ttu-id="98169-105">L’exemple génère un fichier *. xml* avec le contenu suivant.</span><span class="sxs-lookup"><span data-stu-id="98169-105">The example generates an *.xml* file with the following contents.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>xmlsample</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            <summary>
            Class level summary documentation goes here.
            </summary>
            <remarks>
            Longer comments can be associated with a type or member through
            the remarks tag.
            </remarks>
        </member>
        <member name="F:TestClass._name">
            <summary>
            Store for the Name property.
            </summary>
        </member>
        <member name="M:TestClass.#ctor">
            <summary>
            The class constructor.
            </summary>
        </member>
        <member name="P:TestClass.Name">
            <summary>
            Name property.
            </summary>
            <value>
            A value tag is used to describe the property value.
            </value>
        </member>
        <member name="M:TestClass.SomeMethod(System.String)">
            <summary>
            Description for SomeMethod.
            </summary>
            <param name="s"> Parameter description for s goes here.</param>
            <seealso cref="T:System.String">
            You can use the cref attribute on any tag to reference a type or member
            and the compiler will check that the reference exists.
            </seealso>
        </member>
        <member name="M:TestClass.SomeOtherMethod">
            <summary>
            Some other method.
            </summary>
            <returns>
            Return values are described through the returns tag.
            </returns>
            <seealso cref="M:TestClass.SomeMethod(System.String)">
            Notice the use of the cref attribute to reference a specific method.
            </seealso>
        </member>
        <member name="M:TestClass.Main(System.String[])">
            <summary>
            The entry point for the application.
            </summary>
            <param name="args"> A list of command line arguments.</param>
        </member>
        <member name="T:TestInterface">
            <summary>
            Documentation that describes the interface goes here.
            </summary>
            <remarks>
            Details about the interface go here.
            </remarks>
        </member>
        <member name="M:TestInterface.InterfaceMethod(System.Int32)">
            <summary>
            Documentation that describes the method goes here.
            </summary>
            <param name="n">
            Parameter n requires an integer argument.
            </param>
            <returns>
            The method returns an integer.
            </returns>
        </member>
    </members>
</doc>
```

## <a name="compiling-the-code"></a><span data-ttu-id="98169-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="98169-106">Compiling the code</span></span>

<span data-ttu-id="98169-107">Pour compiler l’exemple, entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="98169-107">To compile the example, enter the following command:</span></span>

`csc XMLsample.cs /doc:XMLsample.xml`

<span data-ttu-id="98169-108">Cette commande crée le fichier XML *XMLsample. xml*, que vous pouvez afficher dans votre navigateur ou à l’aide de la `TYPE` commande.</span><span class="sxs-lookup"><span data-stu-id="98169-108">This command creates the XML file *XMLsample.xml*, which you can view in your browser or by using the `TYPE` command.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="98169-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="98169-109">Robust programming</span></span>

<span data-ttu-id="98169-110">La documentation XML commence par `///` .</span><span class="sxs-lookup"><span data-stu-id="98169-110">XML documentation starts with `///`.</span></span> <span data-ttu-id="98169-111">Lorsque vous créez un projet, les assistants placent des lignes de démarrage `///` pour vous.</span><span class="sxs-lookup"><span data-stu-id="98169-111">When you create a new project, the wizards put some starter `///` lines in for you.</span></span> <span data-ttu-id="98169-112">Le traitement de ces commentaires présente certaines restrictions :</span><span class="sxs-lookup"><span data-stu-id="98169-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="98169-113">La documentation doit être dans un format XML correct.</span><span class="sxs-lookup"><span data-stu-id="98169-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="98169-114">Si le XML n’est pas correct, un avertissement est généré. En outre, un commentaire indiquant qu’une erreur s’est produite est ajouté au fichier de documentation.</span><span class="sxs-lookup"><span data-stu-id="98169-114">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>

- <span data-ttu-id="98169-115">Les développeurs sont libres de créer leur propre jeu de balises.</span><span class="sxs-lookup"><span data-stu-id="98169-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="98169-116">Il existe un [ensemble recommandé de balises](recommended-tags-for-documentation-comments.md).</span><span class="sxs-lookup"><span data-stu-id="98169-116">There is a [recommended set of tags](recommended-tags-for-documentation-comments.md).</span></span> <span data-ttu-id="98169-117">Certaines des balises recommandées ont des significations spéciales :</span><span class="sxs-lookup"><span data-stu-id="98169-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="98169-118">La `<param>` balise est utilisée pour décrire les paramètres.</span><span class="sxs-lookup"><span data-stu-id="98169-118">The `<param>` tag is used to describe parameters.</span></span> <span data-ttu-id="98169-119">Quand elle est utilisée, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="98169-119">If used, the compiler verifies that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="98169-120">Si la vérification échoue, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="98169-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="98169-121">L' `cref` attribut peut être attaché à n’importe quelle balise pour référencer un élément de code.</span><span class="sxs-lookup"><span data-stu-id="98169-121">The `cref` attribute can be attached to any tag to reference a code element.</span></span> <span data-ttu-id="98169-122">Le compilateur vérifie l’existence de cet élément de code.</span><span class="sxs-lookup"><span data-stu-id="98169-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="98169-123">Si la vérification échoue, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="98169-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="98169-124">Le compilateur respecte toutes les instructions `using` lorsqu’il recherche un type décrit dans l’attribut `cref`.</span><span class="sxs-lookup"><span data-stu-id="98169-124">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="98169-125">La `<summary>` balise est utilisée par IntelliSense dans Visual Studio pour afficher des informations supplémentaires sur un type ou un membre.</span><span class="sxs-lookup"><span data-stu-id="98169-125">The `<summary>` tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>

    > [!NOTE]
    > <span data-ttu-id="98169-126">Le fichier XML ne fournit pas des informations complètes sur le type et les membres (par exemple, il ne contient pas d’informations sur le type).</span><span class="sxs-lookup"><span data-stu-id="98169-126">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="98169-127">Pour obtenir des informations complètes sur un type ou un membre, utilisez le fichier de documentation ainsi que la réflexion sur le type ou le membre réel.</span><span class="sxs-lookup"><span data-stu-id="98169-127">To get full information about a type or member, use the documentation file together with reflection on the actual type or member.</span></span>

## <a name="see-also"></a><span data-ttu-id="98169-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98169-128">See also</span></span>

- [<span data-ttu-id="98169-129">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="98169-129">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="98169-130">-doc (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="98169-130">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
- [<span data-ttu-id="98169-131">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="98169-131">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="98169-132">Processeur de documentation DocFX</span><span class="sxs-lookup"><span data-stu-id="98169-132">DocFX documentation processor</span></span>](https://dotnet.github.io/docfx/)
- [<span data-ttu-id="98169-133">Processeur de documentation Sandcastle</span><span class="sxs-lookup"><span data-stu-id="98169-133">Sandcastle documentation processor</span></span>](https://github.com/EWSoftware/SHFB)
