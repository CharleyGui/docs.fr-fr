---
title: Définition du type anonyme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 5f6486965d9e44524420975523e10ded32a135b7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755214"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="7c22b-102">Définition du type anonyme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c22b-102">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="7c22b-103">En réponse à la déclaration d’une instance d’un type anonyme, le compilateur crée une nouvelle définition de classe qui contient les propriétés spécifiées pour le type.</span><span class="sxs-lookup"><span data-stu-id="7c22b-103">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="7c22b-104">Code généré par le compilateur</span><span class="sxs-lookup"><span data-stu-id="7c22b-104">Compiler-Generated Code</span></span>

<span data-ttu-id="7c22b-105">Pour la définition suivante de `product`, le compilateur crée une nouvelle définition de classe qui contient les propriétés `Name`, `Price`, et `OnHand`.</span><span class="sxs-lookup"><span data-stu-id="7c22b-105">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="7c22b-106">La définition de classe contient des définitions de propriété semblables à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="7c22b-106">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="7c22b-107">Notez qu’il y a aucune `Set` méthode pour les propriétés de clé.</span><span class="sxs-lookup"><span data-stu-id="7c22b-107">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="7c22b-108">Les valeurs des propriétés de clé sont en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="7c22b-108">The values of key properties are read-only.</span></span>

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

<span data-ttu-id="7c22b-109">En outre, les définitions de type anonymes contiennent un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="7c22b-109">In addition, anonymous type definitions contain a parameterless constructor.</span></span> <span data-ttu-id="7c22b-110">Les constructeurs qui nécessitent des paramètres ne sont pas autorisées.</span><span class="sxs-lookup"><span data-stu-id="7c22b-110">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="7c22b-111">Si une déclaration de type anonyme contient au moins une propriété de clé, la définition de type substitue trois membres hérités de <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, et <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="7c22b-111">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="7c22b-112">Si aucune propriété de clé n’est déclarées uniquement <xref:System.Object.ToString%2A> est remplacée.</span><span class="sxs-lookup"><span data-stu-id="7c22b-112">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="7c22b-113">Les substitutions fournissent les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="7c22b-113">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="7c22b-114">`Equals` Retourne `True` si deux instances de type anonyme sont la même instance, ou si elles répondent aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="7c22b-114">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="7c22b-115">Ils ont le même nombre de propriétés.</span><span class="sxs-lookup"><span data-stu-id="7c22b-115">They have the same number of properties.</span></span>

  - <span data-ttu-id="7c22b-116">Les propriétés sont déclarées dans le même ordre, avec les mêmes noms et les mêmes types déduits.</span><span class="sxs-lookup"><span data-stu-id="7c22b-116">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="7c22b-117">Les comparaisons de noms ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="7c22b-117">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="7c22b-118">Au moins une des propriétés est une propriété de clé et le `Key` mot clé est appliqué aux propriétés identiques.</span><span class="sxs-lookup"><span data-stu-id="7c22b-118">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="7c22b-119">Comparaison de chaque paire correspondante des propriétés de clé retourne `True`.</span><span class="sxs-lookup"><span data-stu-id="7c22b-119">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="7c22b-120">Par exemple, dans les exemples suivants, `Equals` retourne `True` uniquement pour `employee01` et `employee08`.</span><span class="sxs-lookup"><span data-stu-id="7c22b-120">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="7c22b-121">Le commentaire précédant chaque ligne spécifie la raison pour laquelle la nouvelle instance ne correspond pas de raison `employee01`.</span><span class="sxs-lookup"><span data-stu-id="7c22b-121">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="7c22b-122">`GetHashcode` fournit un algorithme GetHashCode unique.</span><span class="sxs-lookup"><span data-stu-id="7c22b-122">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="7c22b-123">L’algorithme utilise uniquement les propriétés de clé pour calculer le code de hachage.</span><span class="sxs-lookup"><span data-stu-id="7c22b-123">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="7c22b-124">`ToString` Retourne une chaîne concaténée de valeurs de propriété, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7c22b-124">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="7c22b-125">La clé et les propriétés non-clé sont incluses.</span><span class="sxs-lookup"><span data-stu-id="7c22b-125">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="7c22b-126">Propriétés explicitement nommées d’un type anonyme ne peut pas entrer en conflit avec ces méthodes générées.</span><span class="sxs-lookup"><span data-stu-id="7c22b-126">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="7c22b-127">Autrement dit, vous ne pouvez pas utiliser `.Equals`, `.GetHashCode`, ou `.ToString` à une propriété de nom.</span><span class="sxs-lookup"><span data-stu-id="7c22b-127">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="7c22b-128">Les définitions de type anonyme qui incluent au moins une propriété de clé implémentent également le <xref:System.IEquatable%601?displayProperty=nameWithType> interface, où `T` est le type du type anonyme.</span><span class="sxs-lookup"><span data-stu-id="7c22b-128">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="7c22b-129">Déclarations de types anonymes crée le même type anonyme uniquement si elles se produisent dans le même assembly, leurs propriétés ont les mêmes noms et les mêmes types déduits, les propriétés sont déclarées dans le même ordre, et les mêmes propriétés sont marquées comme propriétés de clé.</span><span class="sxs-lookup"><span data-stu-id="7c22b-129">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c22b-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c22b-130">See also</span></span>

- [<span data-ttu-id="7c22b-131">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="7c22b-131">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="7c22b-132">Guide pratique pour Déduire les Types dans les déclarations de types anonymes et les noms de propriété</span><span class="sxs-lookup"><span data-stu-id="7c22b-132">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
