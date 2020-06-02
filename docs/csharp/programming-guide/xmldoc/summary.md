---
title: <summary> -Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- <summary>
- summary
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
ms.openlocfilehash: e1a8c9d61e61eae7ba6bf7f0c1b9d2a8dc8a4171
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287205"
---
# <a name="summary-c-programming-guide"></a><span data-ttu-id="490e4-102">\<summary>(Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="490e4-102">\<summary> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="490e4-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="490e4-103">Syntax</span></span>

```xml
<summary>description</summary>
```

## <a name="parameters"></a><span data-ttu-id="490e4-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="490e4-104">Parameters</span></span>

- `description`

  <span data-ttu-id="490e4-105">Résumé de l’objet.</span><span class="sxs-lookup"><span data-stu-id="490e4-105">A summary of the object.</span></span>

## <a name="remarks"></a><span data-ttu-id="490e4-106">Notes</span><span class="sxs-lookup"><span data-stu-id="490e4-106">Remarks</span></span>

<span data-ttu-id="490e4-107">La `<summary>` balise doit être utilisée pour décrire un type ou un membre de type.</span><span class="sxs-lookup"><span data-stu-id="490e4-107">The `<summary>` tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="490e4-108">Utilisez [\<remarks>](./remarks.md) pour ajouter des informations supplémentaires à une description de type.</span><span class="sxs-lookup"><span data-stu-id="490e4-108">Use [\<remarks>](./remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="490e4-109">Utilisez l’[attribut cref](./cref-attribute.md) pour activer des outils de documentation tels que [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) afin de créer des liens hypertexte internes aux pages de documentation pour les éléments de code.</span><span class="sxs-lookup"><span data-stu-id="490e4-109">Use the [cref Attribute](./cref-attribute.md) to enable documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>

<span data-ttu-id="490e4-110">Le texte de la `<summary>` balise est la seule source d’informations sur le type dans IntelliSense et s’affiche également dans la fenêtre de l’Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="490e4-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>

<span data-ttu-id="490e4-111">Compilez avec [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="490e4-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="490e4-112">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [DocFX](https://dotnet.github.io/docfx/) ou [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="490e4-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [DocFX](https://dotnet.github.io/docfx/) or [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>

## <a name="example"></a><span data-ttu-id="490e4-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="490e4-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

<span data-ttu-id="490e4-114">L’exemple précédent génère le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="490e4-114">The previous example produces the following XML file.</span></span>

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

## <a name="example"></a><span data-ttu-id="490e4-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="490e4-115">Example</span></span>

<span data-ttu-id="490e4-116">L’exemple suivant montre comment effectuer une référence `cref` à un type générique.</span><span class="sxs-lookup"><span data-stu-id="490e4-116">The following example shows how to make a `cref` reference to a generic type.</span></span>

[!code-csharp[csProgGuideDocComments#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#11)]

<span data-ttu-id="490e4-117">L’exemple précédent génère le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="490e4-117">The previous example produces the following XML file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="490e4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="490e4-118">See also</span></span>

- [<span data-ttu-id="490e4-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="490e4-119">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="490e4-120">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="490e4-120">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
