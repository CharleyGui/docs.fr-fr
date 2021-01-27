---
title: Comment tester l’égalité des références (identité)-Guide de programmation C#
description: Découvrez comment tester l’égalité des références (identité). Consultez un exemple de code et affichez des ressources supplémentaires disponibles.
ms.date: 07/20/2015
helpviewer_keywords:
- object identity [C#]
- reference equality [C#]
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
ms.openlocfilehash: 148f37b37639061e84cefafc5f057e6e7b54563f
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899150"
---
# <a name="how-to-test-for-reference-equality-identity-c-programming-guide"></a><span data-ttu-id="b7eb4-104">Comment tester l’égalité des références (identité) (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="b7eb4-104">How to test for reference equality (Identity) (C# Programming Guide)</span></span>

<span data-ttu-id="b7eb4-105">Il n’est pas utile d’implémenter une logique personnalisée pour prendre en charge les comparaisons d’égalité de références dans vos types.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-105">You do not have to implement any custom logic to support reference equality comparisons in your types.</span></span> <span data-ttu-id="b7eb4-106">Cette fonctionnalité est fournie pour tous les types par la méthode <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> statique.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-106">This functionality is provided for all types by the static <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b7eb4-107">L’exemple suivant montre comment déterminer si deux variables affichent une *égalité de références*, à savoir qu’elles font référence à un même objet en mémoire.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-107">The following example shows how to determine whether two variables have *reference equality*, which means that they refer to the same object in memory.</span></span>  
  
 <span data-ttu-id="b7eb4-108">L’exemple montre aussi pourquoi <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> retourne toujours `false` pour les types valeur et pourquoi vous ne devez pas utiliser <xref:System.Object.ReferenceEquals%2A> pour déterminer l’égalité de chaînes.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-108">The example also shows why <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> always returns `false` for value types and why you should not use  <xref:System.Object.ReferenceEquals%2A> to determine string equality.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7eb4-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b7eb4-109">Example</span></span>  

 [!code-csharp[TestingReferenceEquality](snippets/how-to-test-for-reference-equality-identity/Program.cs)]  
  
 <span data-ttu-id="b7eb4-110">L’implémentation de `Equals` dans la classe de base universelle <xref:System.Object?displayProperty=nameWithType> assure aussi une vérification de l’égalité de références, mais il est préférable de ne pas l’utiliser, car si une classe se substitue à la méthode, vous risquez d’obtenir des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-110">The implementation of `Equals` in the <xref:System.Object?displayProperty=nameWithType> universal base class also performs a reference equality check, but it is best not to use this because, if a class happens to override the method, the results might not be what you expect.</span></span> <span data-ttu-id="b7eb4-111">Il en va de même pour les opérateurs `==` et `!=`.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-111">The same is true for the `==` and `!=` operators.</span></span> <span data-ttu-id="b7eb4-112">Quand ils s’appliquent à des types référence, le comportement par défaut de `==` et de `!=` est d’effectuer une vérification de l’égalité des références.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-112">When they are operating on reference types, the default behavior of `==` and `!=` is to perform a reference equality check.</span></span> <span data-ttu-id="b7eb4-113">Cependant, les classes dérivées peuvent surcharger l’opérateur pour effectuer une vérification d’égalité de valeurs.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-113">However, derived classes can overload the operator to perform a value equality check.</span></span> <span data-ttu-id="b7eb4-114">Pour réduire le risque d’erreurs, il est recommandé d’utiliser systématiquement <xref:System.Object.ReferenceEquals%2A> quand il s’agit de déterminer si deux objets présentent une égalité de références.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-114">To minimize the potential for error, it is best to always use <xref:System.Object.ReferenceEquals%2A> when you have to determine whether two objects have reference equality.</span></span>  
  
 <span data-ttu-id="b7eb4-115">Les chaînes constantes au sein d’un même assembly sont toujours intégrées par le runtime.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-115">Constant strings within the same assembly are always interned by the runtime.</span></span> <span data-ttu-id="b7eb4-116">Autrement dit, une seule instance de chaque chaîne littérale unique est conservée.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-116">That is, only one instance of each unique literal string is maintained.</span></span> <span data-ttu-id="b7eb4-117">En revanche, le runtime ne garantit pas que les chaînes créées au moment de l’exécution sont intégrées, ni que deux chaînes constantes égales d’assemblys différents sont intégrées.</span><span class="sxs-lookup"><span data-stu-id="b7eb4-117">However, the runtime does not guarantee that strings created at runtime are interned, nor does it guarantee that two equal constant strings in different assemblies are interned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7eb4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7eb4-118">See also</span></span>

- [<span data-ttu-id="b7eb4-119">Comparaisons d’égalité</span><span class="sxs-lookup"><span data-stu-id="b7eb4-119">Equality Comparisons</span></span>](./equality-comparisons.md)
