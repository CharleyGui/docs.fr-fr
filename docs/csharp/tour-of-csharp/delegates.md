---
title: Délégués C# - Visite guidée du langage C#
description: Découvrez la liaison tardive avec les délégués C#
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 317d3ee6fb1350824fa9b3b4d0e3e851780ce4d4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346877"
---
# <a name="delegates"></a>Délégués

Un ***type délégué*** représente des références aux méthodes avec une liste de paramètres et un type de retour particuliers. Les délégués permettent de traiter les méthodes en tant qu’entités qui peuvent être affectées à des variables et passées comme paramètres. Les délégués sont similaires au concept de pointeurs de fonction dans d’autres langages, mais contrairement aux pointeurs de fonction, les délégués sont orientés objet et de type sécurisé.

L’exemple suivant déclare et utilise un type délégué nommé `Function`.

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

Une instance du type délégué `Function` peut faire référence à toute méthode qui accepte un argument `double` et retourne une valeur `double`. La méthode `Apply` applique une fonction donnée aux éléments d’un `double[]`, et retourne un `double[]` avec les résultats. Dans la méthode `Main`, `Apply` sert à appliquer trois fonctions différentes à un `double[]`.

Un délégué peut faire référence à une méthode statique (comme `Square` ou `Math.Sin` dans l’exemple précédent) ou à une méthode d’instance (comme `m.Multiply` dans l’exemple précédent). Un délégué qui référence une méthode d’instance référence aussi un objet particulier, et quand la méthode d’instance est appelée via le délégué, cet objet devient `this` dans l’appel.

Les délégués peuvent également être créés à l’aide de fonctions anonymes, qui sont des « méthodes inline » créées à la volée. Les fonctions anonymes peuvent voir les variables locales des méthodes qui l’entourent. Par conséquent, l’exemple de multiplicateur ci-dessus peut être écrit plus facilement sans utiliser une classe Multiplicateur :

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

Une propriété intéressante et utile d’un délégué est qu’il ne connaît pas la classe de la méthode qu’il référence, et cela lui est égal. Tout ce qui importe est que la méthode référencée ait les mêmes paramètres et type de retour que le délégué.

>[!div class="step-by-step"]
>[Précédent](interfaces.md)
>[Suivant](attributes.md)
