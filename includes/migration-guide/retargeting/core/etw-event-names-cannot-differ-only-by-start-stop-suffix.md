---
ms.openlocfilehash: 0e25d5d9b545e5cb400cbf701fb13da572fadf10
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614454"
---
### <a name="etw-event-names-cannot-differ-only-by-a-start-or-stop-suffix"></a>Les noms d’événements ETW ne peuvent pas différer uniquement par le suffixe « Start » ou « Stop »

#### <a name="details"></a>Détails

Dans les .NET Framework 4,6 et 4.6.1, le runtime lève une exception <xref:System.ArgumentException> lorsque deux noms d’événements suivi d’v nements pour Windows (ETW) diffèrent uniquement par un suffixe « Start » ou « stop » (comme lorsqu’un événement est nommé `LogUser` et un autre est nommé `LogUserStart` ). Dans ce cas, le runtime ne peut pas construire la source d’événements, qui ne peut pas émettre de journalisation.

#### <a name="suggestion"></a>Suggestion

Pour éviter l’exception, assurez-vous que deux noms d’événements ne diffèrent que par un suffixe « Start » ou « stop ». Cette exigence est supprimée à partir de la .NET Framework 4.6.2 ; le runtime peut lever l’ambiguïté des noms d’événements qui diffèrent uniquement par le suffixe « Start » et « Stop ».

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6         |
| Type    | Reciblage |
