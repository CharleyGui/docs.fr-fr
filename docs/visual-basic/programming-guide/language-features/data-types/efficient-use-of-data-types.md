---
title: Utilisation efficace des types de données
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 0de02840cb18fde16134ef43df9d63abb503c979
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394169"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="7d663-102">Utilisation efficace des types de données (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d663-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="7d663-103">Le type de données est affecté aux variables non déclarées et aux variables déclarées sans type de données `Object` .</span><span class="sxs-lookup"><span data-stu-id="7d663-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="7d663-104">Cela facilite l’écriture rapide de programmes, mais peut entraîner une exécution plus lente.</span><span class="sxs-lookup"><span data-stu-id="7d663-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="7d663-105">Typage fort</span><span class="sxs-lookup"><span data-stu-id="7d663-105">Strong Typing</span></span>
 <span data-ttu-id="7d663-106">La spécification des types de données pour toutes vos variables est appelée *typage fort*.</span><span class="sxs-lookup"><span data-stu-id="7d663-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="7d663-107">L’utilisation du typage fort présente plusieurs avantages :</span><span class="sxs-lookup"><span data-stu-id="7d663-107">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="7d663-108">Il permet la prise en charge d’IntelliSense pour vos variables.</span><span class="sxs-lookup"><span data-stu-id="7d663-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="7d663-109">Cela vous permet de voir leurs propriétés et d’autres membres au fur et à mesure que vous tapez dans le code.</span><span class="sxs-lookup"><span data-stu-id="7d663-109">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="7d663-110">Elle tire parti de la vérification du type de compilateur.</span><span class="sxs-lookup"><span data-stu-id="7d663-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="7d663-111">Cela permet d’intercepter les instructions qui peuvent échouer au moment de l’exécution en raison d’erreurs telles que le dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="7d663-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="7d663-112">Il intercepte également les appels aux méthodes sur les objets qui ne les prennent pas en charge.</span><span class="sxs-lookup"><span data-stu-id="7d663-112">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="7d663-113">Cela permet d’accélérer l’exécution de votre code.</span><span class="sxs-lookup"><span data-stu-id="7d663-113">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="7d663-114">Types de données les plus efficaces</span><span class="sxs-lookup"><span data-stu-id="7d663-114">Most Efficient Data Types</span></span>
 <span data-ttu-id="7d663-115">Pour les variables qui ne contiennent jamais de fractions, les types de données intégraux sont plus efficaces que les types non intégraux.</span><span class="sxs-lookup"><span data-stu-id="7d663-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="7d663-116">Dans Visual Basic, `Integer` et `UInteger` sont les types numériques les plus efficaces.</span><span class="sxs-lookup"><span data-stu-id="7d663-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="7d663-117">Pour les nombres fractionnaires, `Double` est le type de données le plus efficace, car les processeurs sur les plateformes actuelles effectuent des opérations à virgule flottante en double précision.</span><span class="sxs-lookup"><span data-stu-id="7d663-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="7d663-118">Toutefois, les opérations avec `Double` ne sont pas aussi rapides que les types intégraux tels que `Integer` .</span><span class="sxs-lookup"><span data-stu-id="7d663-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="7d663-119">Spécification du type de données</span><span class="sxs-lookup"><span data-stu-id="7d663-119">Specifying Data Type</span></span>
 <span data-ttu-id="7d663-120">Utilisez l' [instruction Dim](../../../language-reference/statements/dim-statement.md) pour déclarer une variable d’un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="7d663-120">Use the [Dim Statement](../../../language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="7d663-121">Vous pouvez spécifier simultanément son niveau d’accès à l’aide du mot clé [public](../../../language-reference/modifiers/public.md), [protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md)ou [Private](../../../language-reference/modifiers/private.md) , comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7d663-121">You can simultaneously specify its access level by using the [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), or [Private](../../../language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="7d663-122">Conversion de caractères</span><span class="sxs-lookup"><span data-stu-id="7d663-122">Character Conversion</span></span>
 <span data-ttu-id="7d663-123">Les `AscW` `ChrW` fonctions et fonctionnent en Unicode.</span><span class="sxs-lookup"><span data-stu-id="7d663-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="7d663-124">Vous devez les utiliser de préférence pour `Asc` et `Chr` , qui doit traduire à l’intérieur et à l’extérieur d’Unicode.</span><span class="sxs-lookup"><span data-stu-id="7d663-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d663-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d663-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="7d663-126">Types de données</span><span class="sxs-lookup"><span data-stu-id="7d663-126">Data Types</span></span>](index.md)
- [<span data-ttu-id="7d663-127">Types de données numériques</span><span class="sxs-lookup"><span data-stu-id="7d663-127">Numeric Data Types</span></span>](numeric-data-types.md)
- [<span data-ttu-id="7d663-128">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="7d663-128">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="7d663-129">Using IntelliSense</span><span class="sxs-lookup"><span data-stu-id="7d663-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
