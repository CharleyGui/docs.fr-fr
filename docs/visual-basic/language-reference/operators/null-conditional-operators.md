---
title: Opérateurs conditionnels null (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 4815fe7ad337634cfb56127fbd24a47a37fdd74b
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062944"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="57249-102">?.</span><span class="sxs-lookup"><span data-stu-id="57249-102">?.</span></span> <span data-ttu-id="57249-103">et ? opérateurs de condition null () (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57249-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="57249-104">Teste la valeur de l’opérande de gauche pour la valeur null (`Nothing`) avant d’effectuer un accès au membre (`?.`) ou d’un index (`?()`) de l’opération ; retourne `Nothing` si l’opérande de gauche a la valeur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="57249-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="57249-105">Notez que dans les expressions qui retournent des types valeur en règle générale, l’opérateur conditionnel null renvoie un <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="57249-105">Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="57249-106">Ces opérateurs permettent d’écrire moins de code pour gérer les vérifications « null », en particulier lors de la descente dans les structures de données.</span><span class="sxs-lookup"><span data-stu-id="57249-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="57249-107">Exemple :</span><span class="sxs-lookup"><span data-stu-id="57249-107">For example:</span></span>

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

<span data-ttu-id="57249-108">Pour la comparaison, le code de remplacement pour la première de ces expressions sans opérateur conditionnel null est :</span><span class="sxs-lookup"><span data-stu-id="57249-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="57249-109">Parfois, vous devez entreprendre une action sur un objet qui peut être null, selon la valeur d’un membre Boolean sur cet objet (telles que la propriété booléenne `IsAllowedFreeShipping` dans l’exemple suivant) :</span><span class="sxs-lookup"><span data-stu-id="57249-109">Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):</span></span>

```vb
  Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
  
  If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
   ApplyFreeShippingToOrders(customer)
  End If
```

<span data-ttu-id="57249-110">Vous pouvez raccourcir votre code et éviter de vérifier manuellement les valeurs null à l’aide de l’opérateur conditionnel null comme suit :</span><span class="sxs-lookup"><span data-stu-id="57249-110">You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:</span></span>

```vb
 Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
 
 If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

<span data-ttu-id="57249-111">Les opérateurs conditionnels Null ont un effet de court-circuit.</span><span class="sxs-lookup"><span data-stu-id="57249-111">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="57249-112">Si une opération dans une chaîne d’opérations d’accès et des index membre conditionnel retourne `Nothing`, le reste de le de la chaîne exécution s’arrête.</span><span class="sxs-lookup"><span data-stu-id="57249-112">If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="57249-113">Dans l’exemple suivant, `C(E)` n’est pas évaluée si `A`, `B`, ou `C` prend la valeur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="57249-113">In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="57249-114">Utilisez un autre pour l’accès aux membres conditionnels null consiste à appeler des délégués de façon thread-safe avec beaucoup moins de code.</span><span class="sxs-lookup"><span data-stu-id="57249-114">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="57249-115">L’exemple suivant définit deux types, un `NewsBroadcaster` et un `NewsReceiver`.</span><span class="sxs-lookup"><span data-stu-id="57249-115">The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`.</span></span> <span data-ttu-id="57249-116">Éléments de News sont envoyés au destinataire par le `NewsBroadcaster.SendNews` déléguer.</span><span class="sxs-lookup"><span data-stu-id="57249-116">News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.</span></span>

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String) 

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

<span data-ttu-id="57249-117">Si aucun élément dans le `SendNews` liste d’appel, le `SendNews` délégué lève un <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="57249-117">If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="57249-118">Avant les opérateurs conditionnels null, de code comme celui-ci assuré que la liste d’appel de délégué n’était pas `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="57249-118">Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:</span></span>

```vb  
SendNews = SendNews.Combine({SendNews, client})  
If SendNews IsNot Nothing Then 
   SendNews("Just in...")
End If
```

<span data-ttu-id="57249-119">La nouvelle méthode est beaucoup plus simple :</span><span class="sxs-lookup"><span data-stu-id="57249-119">The new way is much simpler:</span></span>  

```vb
SendNews = SendNews.Combine({SendNews, client})  
SendNews?.Invoke("Just in...")
```

<span data-ttu-id="57249-120">La nouvelle méthode est thread-safe, car le compilateur génère du code qui évalue `SendNews` une seule fois, en conservant le résultat dans une variable temporaire.</span><span class="sxs-lookup"><span data-stu-id="57249-120">The new way is thread-safe because the compiler generates code to evaluate `SendNews` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="57249-121">Vous devez explicitement appeler la méthode `Invoke`, car il n'existe pas de syntaxe d'appel de délégué conditionnel Null `SendNews?(String)`.</span><span class="sxs-lookup"><span data-stu-id="57249-121">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `SendNews?(String)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="57249-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57249-122">See also</span></span>

- [<span data-ttu-id="57249-123">Opérateurs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57249-123">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="57249-124">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57249-124">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="57249-125">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="57249-125">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
