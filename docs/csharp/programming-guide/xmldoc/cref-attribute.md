---
title: cref, attribut - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- cref [C#]
ms.assetid: 66a6b0e5-b961-4504-a461-3a4cf481fc8b
ms.openlocfilehash: 13bdfefaaa6f8daff0e7d9e30a6353af34654ba2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75697245"
---
# <a name="cref-attribute-c-programming-guide"></a><span data-ttu-id="2fc8f-102">cref, attribut (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2fc8f-102">cref Attribute (C# Programming Guide)</span></span>
<span data-ttu-id="2fc8f-103">L’attribut `cref` dans une balise de documentation XML signifie « référence de code ».</span><span class="sxs-lookup"><span data-stu-id="2fc8f-103">The `cref` attribute in an XML documentation tag means "code reference."</span></span> <span data-ttu-id="2fc8f-104">Il indique que le texte interne de la balise est un élément de code tel qu’un type, une méthode ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="2fc8f-104">It specifies that the inner text of the tag is a code element, such as a type, method, or property.</span></span> <span data-ttu-id="2fc8f-105">Les outils de documentation comme [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) utilisent les attributs `cref` pour générer automatiquement des liens hypertexte vers la page où le type ou le membre est documenté.</span><span class="sxs-lookup"><span data-stu-id="2fc8f-105">Documentation tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) use the `cref` attributes to automatically generate hyperlinks to the page where the type or member is documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2fc8f-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="2fc8f-106">Example</span></span>  
 <span data-ttu-id="2fc8f-107">L’exemple suivant montre les attributs `cref` utilisés dans des balises [\<see>](./see.md).</span><span class="sxs-lookup"><span data-stu-id="2fc8f-107">The following example shows `cref` attributes used in [\<see>](./see.md) tags.</span></span>  
  
 [!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]  
  
 <span data-ttu-id="2fc8f-108">Une fois compilé, le programme produit le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="2fc8f-108">When compiled, the program produces the following XML file.</span></span> <span data-ttu-id="2fc8f-109">Notez que l’attribut `cref` pour la méthode `GetZero`, par exemple, a été transformé par le compilateur en `"M:TestNamespace.TestClass.GetZero"`.</span><span class="sxs-lookup"><span data-stu-id="2fc8f-109">Notice that the `cref` attribute for the `GetZero` method, for example, has been transformed by the compiler to `"M:TestNamespace.TestClass.GetZero"`.</span></span> <span data-ttu-id="2fc8f-110">Le préfixe « M: » signifie « méthode » et représente une convention reconnue par les outils de documentation tels que DocFX et Sandcastle.</span><span class="sxs-lookup"><span data-stu-id="2fc8f-110">The "M:" prefix means "method" and is a convention that is recognized by documentation tools such as DocFX and Sandcastle.</span></span> <span data-ttu-id="2fc8f-111">Pour obtenir une liste complète de préfixes, consultez [Traitement du fichier XML](./processing-the-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="2fc8f-111">For a complete list of prefixes, see [Processing the XML File](./processing-the-xml-file.md).</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>CRefTest</name>  
    </assembly>  
    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains cref examples.  
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
    </members>    <members>  
        <member name="T:TestNamespace.TestClass">  
            <summary>  
            TestClass contains two cref examples.  
            </summary>  
        </member>  
        <member name="M:TestNamespace.TestClass.GetZero">  
            <summary>  
            The GetZero method.  
            </summary>  
            <example> This sample shows how to call the <see cref="M:TestNamespace.TestClass.GetZero"/> method.  
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
  
## <a name="see-also"></a><span data-ttu-id="2fc8f-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fc8f-112">See also</span></span>

- [<span data-ttu-id="2fc8f-113">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="2fc8f-113">XML Documentation Comments</span></span>](./index.md)
- [<span data-ttu-id="2fc8f-114">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="2fc8f-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
