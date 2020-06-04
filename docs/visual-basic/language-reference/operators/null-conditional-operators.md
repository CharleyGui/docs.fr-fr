---
title: Opérateurs conditionnels null
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: bffbba859968e0a050397cd9e685c142f801798a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401470"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. les? () opérateurs conditionnels null (Visual Basic)

Teste la valeur de l’opérande de gauche pour la valeur null ( `Nothing` ) avant d’effectuer une opération d’accès au membre ( `?.` ) ou d’index ( `?()` ); retourne `Nothing` si l’opérande de gauche a la valeur `Nothing` . Notez que dans les expressions qui retournent normalement des types valeur, l’opérateur conditionnel null retourne un <xref:System.Nullable%601> .

Ces opérateurs vous aident à écrire moins de code pour gérer les contrôles de valeur null, en particulier dans les structures de données. Par exemple :

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

Pour comparaison, le code alternatif pour la première de ces expressions sans opérateur conditionnel null est le suivant :

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Parfois, vous devez effectuer une action sur un objet qui peut être null, en fonction de la valeur d’un membre booléen sur cet objet (comme la propriété booléenne `IsAllowedFreeShipping` dans l’exemple suivant) :

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

Vous pouvez raccourcir votre code et éviter de vérifier manuellement la valeur null à l’aide de l’opérateur conditionnel NULL comme suit :

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Les opérateurs conditionnels Null ont un effet de court-circuit.  Si une opération dans une chaîne d’accès aux membres conditionnels et d’opérations d’index retourne `Nothing` , le reste de l’exécution de la chaîne s’arrête.  Dans l’exemple suivant, `C(E)` n’est pas évalué si `A` , ou a la `B` `C` valeur `Nothing` .

```vb
A?.B?.C?(E)
```

Une autre utilisation de l’accès aux membres conditionnels null consiste à appeler des délégués de façon sécurisée au niveau des threads avec moins de code.  L’exemple suivant définit deux types, un `NewsBroadcaster` et un `NewsReceiver` . Les éléments de News sont envoyés au récepteur par le `NewsBroadcaster.SendNews` délégué.

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

S’il n’y a aucun élément dans la `SendNews` liste d’appel, le `SendNews` délégué lève une exception <xref:System.NullReferenceException> . Avant les opérateurs conditionnels null, le code comme celui-ci a vérifié que la liste d’appel de délégué n’était pas `Nothing` :

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

La nouvelle méthode est beaucoup plus simple :

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

La nouvelle méthode est thread-safe, car le compilateur génère du code qui évalue `SendNews` une seule fois, en conservant le résultat dans une variable temporaire. Vous devez explicitement appeler la méthode `Invoke`, car il n'existe pas de syntaxe d'appel de délégué conditionnel Null `SendNews?(String)`.

## <a name="see-also"></a>Voir aussi

- [Opérateurs (Visual Basic)](index.md)
- [Guide de programmation Visual Basic](../../programming-guide/index.md)
- [Informations de référence sur le langage Visual Basic](../index.md)
