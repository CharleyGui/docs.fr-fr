---
title: Liaisons let dans des classes
description: Découvrez comment définir des champs privés et des fonctions privées F# pour les classes en utilisant des liaisons’Let’dans la définition de classe.
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216530"
---
# <a name="let-bindings-in-classes"></a><span data-ttu-id="97988-103">Liaisons let dans des classes</span><span class="sxs-lookup"><span data-stu-id="97988-103">let Bindings in Classes</span></span>

<span data-ttu-id="97988-104">Vous pouvez définir des champs privés et des fonctions F# privées pour les `let` classes en utilisant des liaisons dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="97988-104">You can define private fields and private functions for F# classes by using `let` bindings in the class definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="97988-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97988-105">Syntax</span></span>

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a><span data-ttu-id="97988-106">Notes</span><span class="sxs-lookup"><span data-stu-id="97988-106">Remarks</span></span>

<span data-ttu-id="97988-107">La syntaxe précédente apparaît après l’en-tête de classe et les déclarations d’héritage, mais avant les définitions de membre.</span><span class="sxs-lookup"><span data-stu-id="97988-107">The previous syntax appears after the class heading and inheritance declarations but before any member definitions.</span></span> <span data-ttu-id="97988-108">La syntaxe est similaire à celle `let` des liaisons en dehors des classes, mais les noms définis dans une classe ont une portée limitée à la classe.</span><span class="sxs-lookup"><span data-stu-id="97988-108">The syntax is like that of `let` bindings outside of classes, but the names defined in a class have a scope that is limited to the class.</span></span> <span data-ttu-id="97988-109">Une `let` liaison crée une fonction ou un champ privé ; pour exposer publiquement des données ou des fonctions, déclarez une propriété ou une méthode de membre.</span><span class="sxs-lookup"><span data-stu-id="97988-109">A `let` binding creates a private field or function; to expose data or functions publicly, declare a property or a member method.</span></span>

<span data-ttu-id="97988-110">Une `let` liaison qui n’est pas statique est appelée liaison `let` d’instance.</span><span class="sxs-lookup"><span data-stu-id="97988-110">A `let` binding that is not static is called an instance `let` binding.</span></span> <span data-ttu-id="97988-111">Les `let` liaisons d’instance s’exécutent lorsque des objets sont créés.</span><span class="sxs-lookup"><span data-stu-id="97988-111">Instance `let` bindings execute when objects are created.</span></span> <span data-ttu-id="97988-112">Les `let` liaisons statiques font partie de l’initialiseur statique de la classe, dont l’exécution est garantie avant que le type ne soit utilisé pour la première fois.</span><span class="sxs-lookup"><span data-stu-id="97988-112">Static `let` bindings are part of the static initializer for the class, which is guaranteed to execute before the type is first used.</span></span>

<span data-ttu-id="97988-113">Le code dans les `let` liaisons d’instance peut utiliser les paramètres du constructeur principal.</span><span class="sxs-lookup"><span data-stu-id="97988-113">The code within instance `let` bindings can use the primary constructor's parameters.</span></span>

<span data-ttu-id="97988-114">Les attributs et les modificateurs d’accessibilité ne `let` sont pas autorisés sur les liaisons dans les classes.</span><span class="sxs-lookup"><span data-stu-id="97988-114">Attributes and accessibility modifiers are not permitted on `let` bindings in classes.</span></span>

<span data-ttu-id="97988-115">Les exemples de code suivants illustrent plusieurs `let` types de liaisons dans des classes.</span><span class="sxs-lookup"><span data-stu-id="97988-115">The following code examples illustrate several types of `let` bindings in classes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

<span data-ttu-id="97988-116">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="97988-116">The output is as follows.</span></span>

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a><span data-ttu-id="97988-117">Autres façons de créer des champs</span><span class="sxs-lookup"><span data-stu-id="97988-117">Alternative Ways to Create Fields</span></span>

<span data-ttu-id="97988-118">Vous pouvez également utiliser le `val` mot clé pour créer un champ privé.</span><span class="sxs-lookup"><span data-stu-id="97988-118">You can also use the `val` keyword to create a private field.</span></span> <span data-ttu-id="97988-119">Quand vous utilisez `val` le mot clé, le champ n’a pas de valeur lorsque l’objet est créé, mais est initialisé avec une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="97988-119">When using the `val` keyword, the field is not given a value when the object is created, but instead is initialized with a default value.</span></span> <span data-ttu-id="97988-120">Pour plus d’informations, [consultez champs explicites: Mot clé](explicit-fields-the-val-keyword.md)Val.</span><span class="sxs-lookup"><span data-stu-id="97988-120">For more information, see [Explicit Fields: The val Keyword](explicit-fields-the-val-keyword.md).</span></span>

<span data-ttu-id="97988-121">Vous pouvez également définir des champs privés dans une classe en utilisant une définition de membre et en `private` ajoutant le mot clé à la définition.</span><span class="sxs-lookup"><span data-stu-id="97988-121">You can also define private fields in a class by using a member definition and adding the keyword `private` to the definition.</span></span> <span data-ttu-id="97988-122">Cela peut être utile si vous envisagez de modifier l’accessibilité d’un membre sans réécrire votre code.</span><span class="sxs-lookup"><span data-stu-id="97988-122">This can be useful if you expect to change the accessibility of a member without rewriting your code.</span></span> <span data-ttu-id="97988-123">Pour plus d’informations, consultez [Contrôle d’accès](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="97988-123">For more information, see [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="97988-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97988-124">See also</span></span>

- [<span data-ttu-id="97988-125">Membres</span><span class="sxs-lookup"><span data-stu-id="97988-125">Members</span></span>](index.md)
- [<span data-ttu-id="97988-126">Liaisons `do` dans des classes</span><span class="sxs-lookup"><span data-stu-id="97988-126">`do` Bindings in Classes</span></span>](do-bindings-in-classes.md)
- [<span data-ttu-id="97988-127">`let`Liaisons</span><span class="sxs-lookup"><span data-stu-id="97988-127">`let` Bindings</span></span>](../functions/let-bindings.md)
