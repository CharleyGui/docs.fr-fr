---
title: <summary> - Guide de programmation C
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: 1ae3c17bef69a52b4d5852e09284929dc328bf8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789671"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="fcd59-102">\<résumé> (guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="fcd59-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="fcd59-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcd59-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="fcd59-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fcd59-104">Parameters</span></span>

- `description`

  <span data-ttu-id="fcd59-105">Résumé de l’objet.</span><span class="sxs-lookup"><span data-stu-id="fcd59-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="fcd59-106">Notes </span><span class="sxs-lookup"><span data-stu-id="fcd59-106">Remarks</span></span>

<span data-ttu-id="fcd59-107">La balise \<summary> doit être utilisée pour décrire un type ou un membre de type.</span><span class="sxs-lookup"><span data-stu-id="fcd59-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="fcd59-108">Utilisez [ \<des remarques>](./remarks.md) pour ajouter des informations supplémentaires à une description de type.</span><span class="sxs-lookup"><span data-stu-id="fcd59-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="fcd59-109">Utilisez l’[attribut cref](./cref-attribute.md) pour activer des outils de documentation tels que [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) afin de créer des liens hypertexte internes aux pages de documentation pour les éléments de code.</span><span class="sxs-lookup"><span data-stu-id="fcd59-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="fcd59-110">Le texte de la balise \<summary> est la seule source d’informations sur le type dans IntelliSense et il est également affiché dans la fenêtre Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="fcd59-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="fcd59-111">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="fcd59-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="fcd59-112">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé, ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="fcd59-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="fcd59-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="fcd59-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="fcd59-114">L’exemple précédent génère le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="fcd59-114">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>YourNamespace</name>
    </assembly>
    <members>
        <member name="T:TestClass">
            text for class TestClass
        </member>
        <member name="M:TestClass.DoWork(System.Int32)">
            <summary>DoWork is a method in the TestClass class.
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>
            <seealso cref="M:TestClass.Main"/>
            </summary>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="fcd59-115"> Exemple</span><span class="sxs-lookup"><span data-stu-id="fcd59-115">Example</span></span>

<span data-ttu-id="fcd59-116">L’exemple suivant montre comment effectuer une référence `cref` à un type générique.</span><span class="sxs-lookup"><span data-stu-id="fcd59-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="fcd59-117">L’exemple précédent génère le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="fcd59-117">The previous example produces the following XML file.</span></span>

```xml
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:A">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:B">
            <summary cref="T:C`1">
            </summary>
        </member>
        <member name="T:C`1">
            <summary cref="T:A">
            </summary>
            <typeparam name="T"></typeparam>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="fcd59-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcd59-118">See also</span></span>

- [<span data-ttu-id="fcd59-119">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="fcd59-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="fcd59-120">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="fcd59-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
