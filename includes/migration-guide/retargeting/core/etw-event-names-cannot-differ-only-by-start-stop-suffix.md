---
ms.openlocfilehash: 71c81cf188fa4c2300661f10eb87e7ae00e031f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804424"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Les noms d’événements ETW ne peuvent pas différer uniquement par le suffixe « Start » ou « Stop »

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6 et 4.6.1, le runtime lève un <xref:System.ArgumentException> quand deux noms d’événements ETW (Event Tracing for Windows) diffèrent uniquement par le suffixe &quot;Start&quot; ou &quot;Stop&quot; (comme quand un événement est nommé <code>LogUser</code> et un autre <code>LogUserStart</code>). Dans ce cas, le runtime ne peut pas construire la source d’événements, qui ne peut pas émettre de journalisation.|
|Suggestion|Pour empêcher cette exception, vérifiez qu’aucun des deux noms d’événement ne diffère uniquement par un suffixe &quot;Start&quot; ou &quot;Stop&quot;. À compter de .NET Framework 4.6.2, cette vérification n’est plus nécessaire. Le runtime est désormais capable de lever l’ambiguïté des noms d’événements qui diffèrent uniquement par le suffixe &quot;Start&quot; et &quot;Stop&quot;.|
|Étendue|Edge|
|Version|4.6|
|Type|Reciblage|
