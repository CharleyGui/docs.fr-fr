---
title: <summary> -Guide de programmation C#
description: En savoir plus sur le XML <summary> balise utilisée pour décrire un type ou un membre de type. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: f9243e598aaf0c12dd48b48045f461b4b307c18f
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380603"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="93335-105">\<summary>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="93335-105">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="93335-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93335-106">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="93335-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="93335-107">Parameters</span></span>

- `description`

  <span data-ttu-id="93335-108">Résumé de l’objet.</span><span class="sxs-lookup"><span data-stu-id="93335-108">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="93335-109">Notes</span><span class="sxs-lookup"><span data-stu-id="93335-109">Remarks</span></span>

<span data-ttu-id="93335-110">La `<summary>` balise doit être utilisée pour décrire un type ou un membre de type.</span><span class="sxs-lookup"><span data-stu-id="93335-110">The `<summary>` tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="93335-111">Utilisez [\<remarks>](./remarks.md) pour ajouter des informations supplémentaires à une description de type.</span><span class="sxs-lookup"><span data-stu-id="93335-111">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="93335-112">Utilisez l’[attribut cref](./cref-attribute.md) pour activer des outils de documentation tels que [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) afin de créer des liens hypertexte internes aux pages de documentation pour les éléments de code.</span><span class="sxs-lookup"><span data-stu-id="93335-112">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="93335-113">Le texte de la `<summary>` balise est la seule source d’informations sur le type dans IntelliSense et s’affiche également dans la fenêtre de l’Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="93335-113">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="93335-114">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="93335-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="93335-115">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="93335-115">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="93335-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="93335-116">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="93335-117">L’exemple précédent génère le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="93335-117">The previous example produces the following XML file.</span></span>

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
            </summary>
            <seealso cref="M:TestClass.Main"/>
        </member>
        <member name="M:TestClass.Main">
            text for Main
        </member>
    </members>
</doc>
```

## <a name="example"></a><span data-ttu-id="93335-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="93335-118">Example</span></span>

<span data-ttu-id="93335-119">L’exemple suivant montre comment effectuer une référence `cref` à un type générique.</span><span class="sxs-lookup"><span data-stu-id="93335-119">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="93335-120">L’exemple précédent génère le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="93335-120">The previous example produces the following XML file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="93335-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93335-121">See also</span></span>

- [<span data-ttu-id="93335-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="93335-122">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="93335-123">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="93335-123">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
