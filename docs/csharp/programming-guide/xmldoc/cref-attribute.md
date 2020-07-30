---
title: CREF, attribut-Guide de programmation C#
description: En savoir plus sur l’attribut cref. L’attribut cref signifie « référence du code » et spécifie que le texte interne de la balise est un élément de code.
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: 31fa1a3f182d7b72a1dfbe1ce47386f87fbbff75
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381994"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="d6776-104">CREF, attribut (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="d6776-104">cref attribute (C# programming guide)</span></span>

<span data-ttu-id="d6776-105">L’attribut `cref` dans une balise de documentation XML signifie « référence de code ».</span><span class="sxs-lookup"><span data-stu-id="d6776-105">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="d6776-106">Il indique que le texte interne de la balise est un élément de code tel qu’un type, une méthode ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="d6776-106">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="d6776-107">Les outils de documentation comme [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) utilisent les attributs `cref` pour générer automatiquement des liens hypertexte vers la page où le type ou le membre est documenté.</span><span class="sxs-lookup"><span data-stu-id="d6776-107">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>

## <a name="example"></a><span data-ttu-id="d6776-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d6776-108">Example</span></span>

<span data-ttu-id="d6776-109">L’exemple suivant montre les `cref` attributs utilisés dans les [\<see>](./see.md) balises.</span><span class="sxs-lookup"><span data-stu-id="d6776-109">The following example shows `cref` attributes used in [\<see>](./see.md) tags.</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

<span data-ttu-id="d6776-110">Une fois compilé, le programme produit le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="d6776-110">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="d6776-111">Notez que l’attribut `cref` pour la méthode `GetZero`, par exemple, a été transformé par le compilateur en `"M:TestNamespace.TestClass.GetZero"`.</span><span class="sxs-lookup"><span data-stu-id="d6776-111">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="d6776-112">Le préfixe « M: » signifie « méthode » et représente une convention reconnue par les outils de documentation tels que DocFX et Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="d6776-112">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="d6776-113">Pour obtenir une liste complète de préfixes, consultez [Traitement du fichier XML](./processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="d6776-113">For a complete list of prefixes, see [Processing the XML File](./processing-the-xml-file.md).</span></span>

```xml  
<?xml version="1.0"?>
<doc>
    <assembly>
        <name>CRefTest</name>
    </assembly>
    <members>
        <member name="T:TestNamespace.TestClass">
            <summary>
            TestClass contains several cref examples.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor">
            <summary>
            This sample shows how to specify the <see cref="T:TestNamespace.TestClass"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.#ctor(System.Int32)">
            <summary>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.#ctor(System.Int32)"/> constructor as a cref attribute.
            </summary>
        </member>
        <member name="M:TestNamespace.TestClass.GetZero">
            <summary>
            The GetZero method.
            </summary>
            <example>
            This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.
            <code>
            class TestClass
            {
                static int Main()
                {
                    return GetZero();
                }
            }
            </code>
            </example>
        </member>
        <member name="M:TestNamespace.TestClass.GetGenericValue``1(``0)">
            <summary>
            The GetGenericValue method.
            </summary>
            <remarks>
            This sample shows how to specify the <see cref="M:TestNamespace.TestClass.GetGenericValue``1(``0)"/> method as a cref attribute.
            </remarks>
        </member>
        <member name="T:TestNamespace.GenericClass`1">
            <summary>
            GenericClass.
            </summary>
            <remarks>
            This example shows how to specify the <see cref="T:TestNamespace.GenericClass`1"/> type as a cref attribute.
            </remarks>
        </member>
    </members>
</doc>
```

## <a name="see-also"></a><span data-ttu-id="d6776-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6776-114">See also</span></span>

- [<span data-ttu-id="d6776-115">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="d6776-115">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="d6776-116">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="d6776-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
