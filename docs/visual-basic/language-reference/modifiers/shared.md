---
title: Partagé
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: bc63de4bda1e8e605e25fbe293686c187dd4d005
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290991"
---
# <a name="shared-visual-basic"></a><span data-ttu-id="57157-102">Shared (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57157-102">Shared (Visual Basic)</span></span>

<span data-ttu-id="57157-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés sont associés à une classe ou une structure au grand, et non à une instance spécifique de la classe ou de la structure.</span><span class="sxs-lookup"><span data-stu-id="57157-103">Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.</span></span>

## <a name="when-to-use-shared"></a><span data-ttu-id="57157-104">Quand utiliser le partagé</span><span class="sxs-lookup"><span data-stu-id="57157-104">When to Use Shared</span></span>

<span data-ttu-id="57157-105">Le partage d’un membre d’une classe ou d’une structure le rend disponible pour chaque instance, plutôt que *non partagée*, où chaque instance conserve sa propre copie.</span><span class="sxs-lookup"><span data-stu-id="57157-105">Sharing a member of a class or structure makes it available to every instance, rather than *non-shared*, where each instance keeps its own copy.</span></span> <span data-ttu-id="57157-106">Cela est utile, par exemple, si la valeur d’une variable s’applique à l’application entière.</span><span class="sxs-lookup"><span data-stu-id="57157-106">This is useful, for example, if the value of a variable applies to the entire application.</span></span> <span data-ttu-id="57157-107">Si vous déclarez cette variable comme étant `Shared` , toutes les instances accèdent au même emplacement de stockage et si une instance modifie la valeur de la variable, toutes les instances accèdent à la valeur mise à jour.</span><span class="sxs-lookup"><span data-stu-id="57157-107">If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.</span></span>

<span data-ttu-id="57157-108">Le partage ne modifie pas le niveau d’accès d’un membre.</span><span class="sxs-lookup"><span data-stu-id="57157-108">Sharing does not alter the access level of a member.</span></span> <span data-ttu-id="57157-109">Par exemple, un membre de classe peut être partagé et privé (accessible uniquement à partir de la classe), ou non partagé et public.</span><span class="sxs-lookup"><span data-stu-id="57157-109">For example, a class member can be shared and private (accessible only from within the class), or non-shared and public.</span></span> <span data-ttu-id="57157-110">Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="57157-110">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

## <a name="rules"></a><span data-ttu-id="57157-111">Règles</span><span class="sxs-lookup"><span data-stu-id="57157-111">Rules</span></span>

- <span data-ttu-id="57157-112">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="57157-112">**Declaration Context.**</span></span> <span data-ttu-id="57157-113">Vous pouvez utiliser `Shared` seulement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="57157-113">You can use `Shared` only at module level.</span></span> <span data-ttu-id="57157-114">Cela signifie que le contexte de déclaration pour un `Shared` élément doit être une classe ou une structure, et ne peut pas être un fichier source, un espace de noms ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="57157-114">This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.</span></span>

- <span data-ttu-id="57157-115">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="57157-115">**Combined Modifiers.**</span></span> <span data-ttu-id="57157-116">Vous ne pouvez pas spécifier `Shared` avec [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)ou [static](../../../visual-basic/language-reference/modifiers/static.md) dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="57157-116">You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.</span></span>

- <span data-ttu-id="57157-117">**L’accès à.**</span><span class="sxs-lookup"><span data-stu-id="57157-117">**Accessing.**</span></span> <span data-ttu-id="57157-118">Vous accédez à un élément Shared en le qualifiant avec son nom de classe ou de structure, et non avec le nom de variable d’une instance spécifique de sa classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="57157-118">You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure.</span></span> <span data-ttu-id="57157-119">Vous n’avez même pas besoin de créer une instance d’une classe ou d’une structure pour accéder à ses membres partagés.</span><span class="sxs-lookup"><span data-stu-id="57157-119">You do not even have to create an instance of a class or structure to access its shared members.</span></span>

     <span data-ttu-id="57157-120">L’exemple suivant appelle la procédure partagée <xref:System.Double.IsNaN%2A> exposée par la <xref:System.Double> structure.</span><span class="sxs-lookup"><span data-stu-id="57157-120">The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.</span></span>

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- <span data-ttu-id="57157-121">**Partage implicite.**</span><span class="sxs-lookup"><span data-stu-id="57157-121">**Implicit Sharing.**</span></span> <span data-ttu-id="57157-122">Vous ne pouvez pas utiliser le `Shared` modificateur dans une [instruction Const](../../../visual-basic/language-reference/statements/const-statement.md), mais les constantes sont partagées implicitement.</span><span class="sxs-lookup"><span data-stu-id="57157-122">You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared.</span></span> <span data-ttu-id="57157-123">De même, vous ne pouvez pas déclarer un membre d’un module ou une interface comme étant `Shared` , mais ils sont implicitement partagés.</span><span class="sxs-lookup"><span data-stu-id="57157-123">Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.</span></span>

## <a name="behavior"></a><span data-ttu-id="57157-124">Comportement</span><span class="sxs-lookup"><span data-stu-id="57157-124">Behavior</span></span>

- <span data-ttu-id="57157-125">**Rangement.**</span><span class="sxs-lookup"><span data-stu-id="57157-125">**Storage.**</span></span> <span data-ttu-id="57157-126">Une variable ou un événement partagé est stocké en mémoire une seule fois, quel que soit le nombre d’instances que vous créez de sa classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="57157-126">A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure.</span></span> <span data-ttu-id="57157-127">De même, une procédure ou une propriété partagée ne contient qu’un seul jeu de variables locales.</span><span class="sxs-lookup"><span data-stu-id="57157-127">Similarly, a shared procedure or property holds only one set of local variables.</span></span>

- <span data-ttu-id="57157-128">**Accès par le biais d’une variable d’instance.**</span><span class="sxs-lookup"><span data-stu-id="57157-128">**Accessing through an Instance Variable.**</span></span> <span data-ttu-id="57157-129">Il est possible d’accéder à un élément Shared en le qualifiant avec le nom d’une variable qui contient une instance spécifique de sa classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="57157-129">It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure.</span></span> <span data-ttu-id="57157-130">Bien que cela fonctionne généralement comme prévu, le compilateur génère un message d’avertissement et donne l’accès par le biais du nom de la classe ou de la structure au lieu de la variable.</span><span class="sxs-lookup"><span data-stu-id="57157-130">Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.</span></span>

- <span data-ttu-id="57157-131">**Accès par le biais d’une expression d’instance.**</span><span class="sxs-lookup"><span data-stu-id="57157-131">**Accessing through an Instance Expression.**</span></span> <span data-ttu-id="57157-132">Si vous accédez à un élément partagé par le biais d’une expression qui retourne une instance de sa classe ou structure, le compilateur effectue l’accès via le nom de la classe ou de la structure au lieu d’évaluer l’expression.</span><span class="sxs-lookup"><span data-stu-id="57157-132">If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression.</span></span> <span data-ttu-id="57157-133">Cela produit des résultats inattendus si vous avez souhaité que l’expression effectue d’autres actions et retourne l’instance.</span><span class="sxs-lookup"><span data-stu-id="57157-133">This produces unexpected results if you intended the expression to perform other actions as well as returning the instance.</span></span> <span data-ttu-id="57157-134">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="57157-134">The following example illustrates this.</span></span>
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     <span data-ttu-id="57157-135">Dans l’exemple précédent, le compilateur génère un message d’avertissement à la fois que le code accède à la propriété partagée `Total` par le biais d’une instance.</span><span class="sxs-lookup"><span data-stu-id="57157-135">In the preceding example, the compiler generates a warning message both times the code accesses the shared property `Total` through an instance.</span></span> <span data-ttu-id="57157-136">Dans chaque cas, il effectue l’accès directement par le biais de la classe `ShareTotal` et n’utilise aucune instance.</span><span class="sxs-lookup"><span data-stu-id="57157-136">In each case it makes the access directly through the class `ShareTotal` and does not make use of any instance.</span></span> <span data-ttu-id="57157-137">Dans le cas de l’appel prévu à la procédure `ReturnClass` , cela signifie qu’elle ne génère même pas d’appel à `ReturnClass` , donc l’action supplémentaire d’affichage de « Function ReturnClass () called » n’est pas effectuée.</span><span class="sxs-lookup"><span data-stu-id="57157-137">In the case of the intended call to the procedure `ReturnClass`, this means it does not even generate a call to `ReturnClass`, so the additional action of displaying "Function ReturnClass() called" is not performed.</span></span>

<span data-ttu-id="57157-138">Le modificateur `Shared` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="57157-138">The `Shared` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="57157-139">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="57157-139">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="57157-140">Event, instruction</span><span class="sxs-lookup"><span data-stu-id="57157-140">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="57157-141">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="57157-141">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="57157-142">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="57157-142">Operator Statement</span></span>](../operator-statement.md)
- [<span data-ttu-id="57157-143">Property Statement</span><span class="sxs-lookup"><span data-stu-id="57157-143">Property Statement</span></span>](../property-statement.md)
- [<span data-ttu-id="57157-144">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="57157-144">Sub Statement</span></span>](../sub-statement.md)
  
## <a name="see-also"></a><span data-ttu-id="57157-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57157-145">See also</span></span>

- [<span data-ttu-id="57157-146">Shadows</span><span class="sxs-lookup"><span data-stu-id="57157-146">Shadows</span></span>](shadows.md)
- [<span data-ttu-id="57157-147">Statique</span><span class="sxs-lookup"><span data-stu-id="57157-147">Static</span></span>](static.md)
- [<span data-ttu-id="57157-148">Durée de vie dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57157-148">Lifetime in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="57157-149">Procédures</span><span class="sxs-lookup"><span data-stu-id="57157-149">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="57157-150">Structures</span><span class="sxs-lookup"><span data-stu-id="57157-150">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="57157-151">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="57157-151">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
