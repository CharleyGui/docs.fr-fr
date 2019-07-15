---
ms.openlocfilehash: c800b3fcc1eff5d7a669611cb0697aa8c87a37a4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804643"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData récupère maintenant les données au format UTF-8

|   |   |
|---|---|
|Détails|Pour les applications qui ciblent le .NET Framework 4 ou qui s’exécutent sur le .NET Framework 4.5.1 ou versions antérieures, <code>DataObject.GetData</code> récupère les données au format HTML sous forme de chaîne ASCII. Ainsi, les caractères non-ASCII (caractères dont les codes ASCII sont supérieurs à 0x7F) sont représentés par deux caractères aléatoires.<p/>Pour les applications qui ciblent le .NET Framework 4.5 ou version ultérieure et qui s’exécutent sur le .NET Framework 4.5.2, <code>DataObject.GetData</code> récupère les données au format HTML sous la forme de données UTF-8, qui représentent correctement les caractères supérieurs à 0x7F.|
|Suggestion|Si vous avez implémenté une solution de contournement pour ce problème d’encodage des chaînes au format HTML (par exemple, en encodant explicitement la chaîne HTML récupérée à partir du Presse-papiers en la passant à <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name>) et que vous reciblez votre application de la version 4 à la version 4.5, cette solution doit être supprimée. Si l’ancien comportement est nécessaire, l’application peut cibler le .NET Framework 4.0 pour l’obtenir.|
|Portée|Microsoft Edge|
|Version|4.5.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|

