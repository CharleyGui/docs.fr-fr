---
title: Liaisons do
description: Découvrez comment une F# liaison’do’est utilisée pour exécuter du code sans définir une fonction ou une valeur.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630538"
---
# <a name="do-bindings"></a><span data-ttu-id="c4e00-103">Liaisons do</span><span class="sxs-lookup"><span data-stu-id="c4e00-103">do Bindings</span></span>

<span data-ttu-id="c4e00-104">Une `do` liaison est utilisée pour exécuter du code sans définir une fonction ou une valeur.</span><span class="sxs-lookup"><span data-stu-id="c4e00-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="c4e00-105">En outre, les liaisons peuvent être utilisées dans les classes, consultez [ `do` liaisons dans les classes](../members/do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="c4e00-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="c4e00-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4e00-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="c4e00-107">Notes</span><span class="sxs-lookup"><span data-stu-id="c4e00-107">Remarks</span></span>

<span data-ttu-id="c4e00-108">Utilisez une `do` liaison lorsque vous souhaitez exécuter du code indépendamment d’une définition de fonction ou de valeur.</span><span class="sxs-lookup"><span data-stu-id="c4e00-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="c4e00-109">L’expression dans une `do` liaison doit retourner `unit`.</span><span class="sxs-lookup"><span data-stu-id="c4e00-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="c4e00-110">Le code d’une liaison de `do` niveau supérieur est exécuté lors de l’initialisation du module.</span><span class="sxs-lookup"><span data-stu-id="c4e00-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="c4e00-111">Le mot `do` clé est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4e00-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="c4e00-112">Les attributs peuvent être appliqués à une liaison de `do` niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="c4e00-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="c4e00-113">Par exemple, si votre programme utilise COM Interop, vous souhaiterez peut-être `STAThread` appliquer l’attribut à votre programme.</span><span class="sxs-lookup"><span data-stu-id="c4e00-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="c4e00-114">Pour ce faire, vous pouvez utiliser un attribut sur `do` une liaison, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="c4e00-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="c4e00-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4e00-115">See also</span></span>

- [<span data-ttu-id="c4e00-116">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="c4e00-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="c4e00-117">Fonctions</span><span class="sxs-lookup"><span data-stu-id="c4e00-117">Functions</span></span>](index.md)
