---
description: '@ - Référence C#'
title: '@ - Référence C#'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: 7d78b28479ed6128321207073dc94976710f10b6
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138902"
---
# <a name="-c-reference"></a><span data-ttu-id="ac73e-103">@ (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ac73e-103">@ (C# Reference)</span></span>

<span data-ttu-id="ac73e-104">Le caractère spécial `@` sert d’identificateur de chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="ac73e-104">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="ac73e-105">Il peut être utilisé selon les manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="ac73e-105">It can be used in the following ways:</span></span>

1. <span data-ttu-id="ac73e-106">Pour activer les mots clés C# à utiliser comme identificateurs.</span><span class="sxs-lookup"><span data-stu-id="ac73e-106">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="ac73e-107">Le caractère `@` est le préfixe d’un élément de code que le compilateur doit interpréter comme un identificateur plutôt qu’un mot clé C#.</span><span class="sxs-lookup"><span data-stu-id="ac73e-107">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="ac73e-108">L’exemple suivant utilise le caractère `@` pour définir un identificateur nommé `for` qu’il utilise dans une boucle `for`.</span><span class="sxs-lookup"><span data-stu-id="ac73e-108">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="ac73e-109">Pour indiquer qu’un littéral de chaîne doit être interprété textuellement.</span><span class="sxs-lookup"><span data-stu-id="ac73e-109">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="ac73e-110">Le caractère `@` dans cette instance définit un *littéral de chaîne textuelle*.</span><span class="sxs-lookup"><span data-stu-id="ac73e-110">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="ac73e-111">Les séquences d’échappement simples (comme `"\\"` pour une barre oblique inverse), hexadécimales (comme `"\x0041"` pour un A majuscule) et Unicode (comme `"\u0041"` pour un A majuscule), sont interprétées littéralement.</span><span class="sxs-lookup"><span data-stu-id="ac73e-111">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="ac73e-112">Seule une séquence d’échappement de guillemets ( `""` ) n’est pas interprétée littéralement ; elle produit un guillemet double.</span><span class="sxs-lookup"><span data-stu-id="ac73e-112">Only a quote escape sequence (`""`) is not interpreted literally; it produces one double quotation mark.</span></span> <span data-ttu-id="ac73e-113">En outre, dans le cas d’une [chaîne interpolée](interpolated.md) textuelle, les séquences d’échappement des accolades (`{{` et `}}`) ne sont pas interprétées littéralement ; elles produisent une seule accolade.</span><span class="sxs-lookup"><span data-stu-id="ac73e-113">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="ac73e-114">L’exemple suivant définit deux chemins de fichier identiques, un à l’aide d’un littéral de chaîne standard et l’autre à l’aide d’un littéral de chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="ac73e-114">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="ac73e-115">Il s’agit là de l’une des utilisations les plus courantes de littéraux de chaîne textuelle.</span><span class="sxs-lookup"><span data-stu-id="ac73e-115">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="ac73e-116">L’exemple suivant illustre l’effet de la définition d’un littéral de chaîne standard et d’un littéral de chaîne textuelle qui contiennent des séquences de caractères identiques.</span><span class="sxs-lookup"><span data-stu-id="ac73e-116">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="ac73e-117">Pour permettre au compilateur de faire la distinction entre les attributs en cas de conflit de noms.</span><span class="sxs-lookup"><span data-stu-id="ac73e-117">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="ac73e-118">Un attribut est une classe qui dérive de <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="ac73e-118">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="ac73e-119">Son nom de type comprend généralement le suffixe **Attribute**, bien que le compilateur n’applique pas cette convention.</span><span class="sxs-lookup"><span data-stu-id="ac73e-119">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="ac73e-120">L’attribut peut ensuite être référencé dans le code par son nom de type complet (par exemple, `[InfoAttribute]`) ou son nom abrégé (par exemple, `[Info]`).</span><span class="sxs-lookup"><span data-stu-id="ac73e-120">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="ac73e-121">Toutefois, un conflit survient si deux noms de type d’attribut abrégés sont identiques et que l’un d’eux inclut le suffixe **Attribute**, mais pas l’autre.</span><span class="sxs-lookup"><span data-stu-id="ac73e-121">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="ac73e-122">Par exemple, la compilation du code suivant échoue, car le compilateur ne peut pas déterminer si l’attribut `Info` ou `InfoAttribute` est appliqué à la classe `Example`.</span><span class="sxs-lookup"><span data-stu-id="ac73e-122">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="ac73e-123">Pour plus d'informations, consultez [CS1614](../compiler-messages/cs1614.md).</span><span class="sxs-lookup"><span data-stu-id="ac73e-123">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="ac73e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac73e-124">See also</span></span>

- [<span data-ttu-id="ac73e-125">Référence C#</span><span class="sxs-lookup"><span data-stu-id="ac73e-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ac73e-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ac73e-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ac73e-127">Caractères spéciaux C#</span><span class="sxs-lookup"><span data-stu-id="ac73e-127">C# Special Characters</span></span>](./index.md)
