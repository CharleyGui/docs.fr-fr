---
ms.openlocfilehash: 9ad283af76085c228bedceb6db723a1d18b10210
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804424"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Les noms d’événements ETW ne peuvent pas différer uniquement par le suffixe « Start » ou « Stop »

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6 et 4.6.1, le runtime lève un <xref:System.ArgumentException> quand deux noms d’événements ETW (Event Tracing for Windows) diffèrent uniquement par le suffixe &quot;Start&quot; ou &quot;Stop&quot; (comme quand un événement est nommé <code>LogUser</code> et un autre <code>LogUserStart</code>). Dans ce cas, le runtime ne peut pas construire la source d’événements, qui ne peut pas émettre de journalisation.|
|Suggestion|Pour empêcher cette exception, vérifiez qu’aucun des deux noms d’événement ne diffère uniquement par un suffixe &quot;Start&quot; ou &quot;Stop&quot;. À compter de .NET Framework 4.6.2, cette vérification n’est plus nécessaire. Le runtime est désormais capable de lever l’ambiguïté des noms d’événements qui diffèrent uniquement par le suffixe &quot;Start&quot; et &quot;Stop&quot;.|
|Portée|Microsoft Edge|
|Version|4.6|
|Type|Reciblage|

