---
ms.openlocfilehash: 5f1a8af37a305ab0904801002dd99e17e8eca62e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616057"
---
### <a name="two-way-data-binding-to-a-property-with-a-non-public-setter-is-not-supported"></a>La liaison de données bidirectionnelle avec une propriété ayant un accesseur Set non public n’est pas prise en charge

#### <a name="details"></a>Détails

La liaison de données avec une propriété sans accesseur Set public n’a jamais été prise en charge. À compter de .NET Framework 4.5.1, ce scénario lève une exception <xref:System.InvalidOperationException?displayProperty=fullName>. Notez que cette nouvelle exception sera levée uniquement pour les applications qui ciblent spécifiquement le .NET Framework 4.5.1. Si une application cible le .NET Framework 4.5, l’appel sera autorisé. Si l’application ne cible pas une version particulière du .NET Framework, la liaison sera traitée comme étant unidirectionnelle.

#### <a name="suggestion"></a>Suggestion

L’application doit être mise à jour pour utiliser une liaison unidirectionnelle ou exposer publiquement l’accesseur Set de la propriété. Vous pouvez également cibler le .NET Framework 4.5 pour obtenir l’ancien comportement de l’application.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.5.1       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Data.BindingMode.TwoWay?displayProperty=nameWithType>
