---
title: Le type pour la variable '<variablename>' ne sera pas déduit, car il est lié à un champ d'une portée englobante
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 3e76ffea283de2843fc5586179074c01a053ece8
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161281"
---
# <a name="bc42110-the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="ef652-102">BC42110 : le type de la variable' \<variablename> 'ne sera pas déduit, car il est lié à un champ dans une portée englobante</span><span class="sxs-lookup"><span data-stu-id="ef652-102">BC42110: The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="ef652-103">Le type de la variable' \<variablename> 'ne sera pas déduit, car il est lié à un champ dans une portée englobante.</span><span class="sxs-lookup"><span data-stu-id="ef652-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="ef652-104">Modifiez le nom de « \<variablename> » ou utilisez le nom complet (par exemple, « me. NomVariable » ou « MyBase. NomVariable »).</span><span class="sxs-lookup"><span data-stu-id="ef652-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="ef652-105">Une variable de contrôle de boucle dans votre code porte le même nom qu’un champ de la classe ou d’une autre portée englobante.</span><span class="sxs-lookup"><span data-stu-id="ef652-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="ef652-106">Étant donné que la variable de contrôle est utilisée sans `As` clause, elle est liée au champ dans la portée englobante, et le compilateur ne crée pas de variable pour celle-ci ou ne déduit pas son type.</span><span class="sxs-lookup"><span data-stu-id="ef652-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="ef652-107">Dans l’exemple suivant, `Index` la variable de contrôle de l' `For` instruction est liée au `Index` champ de la `Customer` classe.</span><span class="sxs-lookup"><span data-stu-id="ef652-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="ef652-108">Le compilateur ne crée pas de variable pour la variable de contrôle `Index` ou ne déduit pas son type.</span><span class="sxs-lookup"><span data-stu-id="ef652-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

    ' The following line will raise this warning.
        For Index = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

<span data-ttu-id="ef652-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="ef652-109">By default, this message is a warning.</span></span> <span data-ttu-id="ef652-110">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ef652-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="ef652-111">**ID d’erreur :** BC42110</span><span class="sxs-lookup"><span data-stu-id="ef652-111">**Error ID:** BC42110</span></span>

## <a name="to-address-this-warning"></a><span data-ttu-id="ef652-112">Pour traiter cet avertissement</span><span class="sxs-lookup"><span data-stu-id="ef652-112">To address this warning</span></span>

- <span data-ttu-id="ef652-113">Rendez la variable de contrôle de boucle locale en remplaçant son nom par un identificateur qui n’est pas également le nom d’un champ de la classe.</span><span class="sxs-lookup"><span data-stu-id="ef652-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="ef652-114">Précisez que la variable de contrôle de boucle est liée au champ de classe en préfixant `Me.` le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="ef652-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="ef652-115">Au lieu de vous appuyer sur l’inférence de type local, utilisez une `As` clause pour spécifier un type pour la variable de contrôle de boucle.</span><span class="sxs-lookup"><span data-stu-id="ef652-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="ef652-116"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ef652-116">Example</span></span>

 <span data-ttu-id="ef652-117">Le code suivant montre l’exemple précédent avec la première correction sur place.</span><span class="sxs-lookup"><span data-stu-id="ef652-117">The following code shows the earlier example with the first correction in place.</span></span>

```vb
Class Customer

    ' The class has a field named Index.
    Private Index As Integer

    Sub Main()

        For I = 1 To 10
            ' ...
        Next

    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="ef652-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef652-118">See also</span></span>

- [<span data-ttu-id="ef652-119">Instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="ef652-119">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="ef652-120">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="ef652-120">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="ef652-121">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="ef652-121">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="ef652-122">Comment : référencer l'instance actuelle d'un objet</span><span class="sxs-lookup"><span data-stu-id="ef652-122">How to: Refer to the Current Instance of an Object</span></span>](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="ef652-123">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="ef652-123">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="ef652-124">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="ef652-124">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
