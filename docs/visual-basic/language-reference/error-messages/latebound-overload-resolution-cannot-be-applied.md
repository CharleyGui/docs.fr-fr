---
title: La résolution de surcharge à liaison tardive ne peut pas être appliquée à '<procedurename>', car l'instance d'accès est un type interface
ms.date: 07/20/2015
f1_keywords:
- vbc30933
- bc30933
helpviewer_keywords:
- overload resolution [Visual Basic], with late-bound argument
- BC30933
ms.assetid: 8182eea0-dd34-4d6e-9ca0-41d8713e9dc4
ms.openlocfilehash: 090ec6f3bbf56350fda2ab15c974b0bc6b15e3d3
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162516"
---
# <a name="bc30933-latebound-overload-resolution-cannot-be-applied-to-procedurename-because-the-accessing-instance-is-an-interface-type"></a><span data-ttu-id="d3d47-102">BC30933 : la résolution de surcharge à liaison tardive ne peut pas être appliquée à' \<procedurename> ', car l’instance d’accès est un type interface</span><span class="sxs-lookup"><span data-stu-id="d3d47-102">BC30933: Latebound overload resolution cannot be applied to '\<procedurename>' because the accessing instance is an interface type</span></span>

<span data-ttu-id="d3d47-103">Le compilateur tente de résoudre une référence à une propriété ou une procédure surchargée, mais la référence échoue parce qu’un argument est de type `Object` et que l’objet de référence a le type de données d’une interface.</span><span class="sxs-lookup"><span data-stu-id="d3d47-103">The compiler is attempting to resolve a reference to an overloaded property or procedure, but the reference fails because an argument is of type `Object` and the referring object has the data type of an interface.</span></span> <span data-ttu-id="d3d47-104">L' `Object` argument force le compilateur à résoudre la référence comme étant à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="d3d47-104">The `Object` argument forces the compiler to resolve the reference as late-bound.</span></span>

<span data-ttu-id="d3d47-105">Dans ces circonstances, le compilateur résout la surcharge par le biais de la classe d’implémentation plutôt que par le biais de l’interface sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="d3d47-105">In these circumstances, the compiler resolves the overload through the implementing class instead of through the underlying interface.</span></span> <span data-ttu-id="d3d47-106">Si la classe renomme une des versions surchargées, le compilateur ne considère pas cette version comme étant une surcharge, car son nom est différent.</span><span class="sxs-lookup"><span data-stu-id="d3d47-106">If the class renames one of the overloaded versions, the compiler does not consider that version to be an overload because its name is different.</span></span> <span data-ttu-id="d3d47-107">Cela indique à son tour que le compilateur ignore la version renommée lorsqu’il peut être le bon choix pour résoudre la référence.</span><span class="sxs-lookup"><span data-stu-id="d3d47-107">This in turn causes the compiler to ignore the renamed version when it might have been the correct choice to resolve the reference.</span></span>

<span data-ttu-id="d3d47-108">**ID d’erreur :** BC30933</span><span class="sxs-lookup"><span data-stu-id="d3d47-108">**Error ID:** BC30933</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d3d47-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d3d47-109">To correct this error</span></span>

- <span data-ttu-id="d3d47-110">Utilisez `CType` pour effectuer un cast de l’argument de `Object` vers le type spécifié par la signature de la surcharge que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="d3d47-110">Use `CType` to cast the argument from `Object` to the type specified by the signature of the overload you want to call.</span></span>

  <span data-ttu-id="d3d47-111">Notez qu’il ne permet pas d’effectuer un cast de l’objet de référence en interface sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="d3d47-111">Note that it does not help to cast the referring object to the underlying interface.</span></span> <span data-ttu-id="d3d47-112">Vous devez effectuer un cast de l’argument pour éviter cette erreur.</span><span class="sxs-lookup"><span data-stu-id="d3d47-112">You must cast the argument to avoid this error.</span></span>

## <a name="example"></a><span data-ttu-id="d3d47-113"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d3d47-113">Example</span></span>

<span data-ttu-id="d3d47-114">L’exemple suivant montre un appel à une procédure surchargée `Sub` qui provoque cette erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d3d47-114">The following example shows a call to an overloaded `Sub` procedure that causes this error at compile time.</span></span>

```vb
Module m1
    Interface i1
        Sub s1(ByVal p1 As Integer)
        Sub s1(ByVal p1 As Double)
    End Interface
    Class c1
        Implements i1
        Public Overloads Sub s1(ByVal p1 As Integer) Implements i1.s1
        End Sub
        Public Overloads Sub s2(ByVal p1 As Double) Implements i1.s1
        End Sub
    End Class
    Sub Main()
        Dim refer As i1 = New c1
        Dim o1 As Object = 3.1415
        ' The following reference is INVALID and causes a compiler error.
        refer.s1(o1)
    End Sub
End Module
```

<span data-ttu-id="d3d47-115">Dans l’exemple précédent, si le compilateur a autorisé l’appel à `s1` comme étant écrit, la résolution a lieu via la classe `c1` au lieu de l’interface `i1` .</span><span class="sxs-lookup"><span data-stu-id="d3d47-115">In the preceding example, if the compiler allowed the call to `s1` as written, the resolution would take place through the class `c1` instead of the interface `i1`.</span></span> <span data-ttu-id="d3d47-116">Cela signifie que le compilateur ne tient pas compte du `s2` fait que son nom est différent dans `c1` , même s’il s’agit du bon choix, tel que défini par `i1` .</span><span class="sxs-lookup"><span data-stu-id="d3d47-116">This would mean that the compiler would not consider `s2` because its name is different in `c1`, even though it is the correct choice as defined by `i1`.</span></span>

<span data-ttu-id="d3d47-117">Vous pouvez corriger l’erreur en modifiant l’appel à l’une ou l’autre des lignes de code suivantes :</span><span class="sxs-lookup"><span data-stu-id="d3d47-117">You can correct the error by changing the call to either of the following lines of code:</span></span>

```vb
refer.s1(CType(o1, Integer))
refer.s1(CType(o1, Double))
```

<span data-ttu-id="d3d47-118">Chacune des lignes précédentes de code convertit explicitement la `Object` variable `o1` en l’un des types de paramètres définis pour les surcharges.</span><span class="sxs-lookup"><span data-stu-id="d3d47-118">Each of the preceding lines of code explicitly casts the `Object` variable `o1` to one of the parameter types defined for the overloads.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3d47-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3d47-119">See also</span></span>

- [<span data-ttu-id="d3d47-120">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="d3d47-120">Procedure Overloading</span></span>](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="d3d47-121">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="d3d47-121">Overload Resolution</span></span>](../../programming-guide/language-features/procedures/overload-resolution.md)
- [<span data-ttu-id="d3d47-122">CType Function</span><span class="sxs-lookup"><span data-stu-id="d3d47-122">CType Function</span></span>](../functions/ctype-function.md)
