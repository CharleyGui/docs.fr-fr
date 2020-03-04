---
title: Délégués C# - Visite guidée du langage C#
description: Découvrez la liaison tardive avec les délégués C#
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159167"
---
# <a name="delegates"></a>Délégués

Un ***type délégué*** représente des références à des méthodes avec une liste de paramètres et un type de retour particuliers. Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres. Les délégués sont similaires au concept de pointeurs de fonction trouvés dans d’autres langages. Contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.

L’exemple suivant déclare et utilise un type délégué nommé `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Une instance du type délégué `Function` peut faire référence à toute méthode qui accepte un argument `double` et retourne une valeur `double`. La méthode `Apply` applique une fonction donnée aux éléments d’un `double[]`, et retourne un `double[]` avec les résultats. Dans la méthode `Main`, `Apply` sert à appliquer trois fonctions différentes à un `double[]`.

Un délégué peut faire référence à une méthode statique (comme `Square` ou `Math.Sin` dans l’exemple précédent) ou à une méthode d’instance (comme `m.Multiply` dans l’exemple précédent). Un délégué qui référence une méthode d’instance référence aussi un objet particulier, et quand la méthode d’instance est appelée via le délégué, cet objet devient `this` dans l’appel.

Les délégués peuvent également être créés à l’aide de fonctions anonymes, qui sont des « méthodes inline » qui sont créées lorsqu’elles sont déclarées. Les fonctions anonymes peuvent voir les variables locales des méthodes qui l’entourent. L’exemple suivant ne crée pas de classe :

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Un délégué ne connaît pas ou ne tient pas compte de la classe de la méthode qu’il référence ; Il est important que la méthode référencée ait les mêmes paramètres et le même type de retour que le délégué.

>[!div class="step-by-step"]
>[Précédent](interfaces.md)
>[Suivant](attributes.md)
