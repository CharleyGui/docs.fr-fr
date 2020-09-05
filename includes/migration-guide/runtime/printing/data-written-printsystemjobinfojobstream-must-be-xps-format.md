---
ms.openlocfilehash: 19be8a7755d9b238ab6507eaa73319bddf39faa3
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497347"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Les données écrites dans PrintSystemJobInfo.JobStream doivent être au format XPS

#### <a name="details"></a>Détails

La propriété <xref:System.Printing.PrintSystemJobInfo.JobStream> expose le flux d’un travail d’impression. L’utilisateur peut envoyer des données brutes aux composants d’impression du système d’exploitation sous-jacent en écrivant dans ce flux. À compter de .NET Framework 4.5 sur Windows 8 et les versions ultérieures du système d’exploitation Windows, les données écrites dans ce flux doivent être au format XPS en tant que flux de package.

#### <a name="suggestion"></a>Suggestion

Pour sortir le contenu d’impression, vous pouvez procéder de l’une des manières suivantes :<ul><li>Utilisez la classe <xref:System.Windows.Xps.XpsDocumentWriter> pour sortir le contenu d’impression. Il s’agit de l’alternative recommandée.</li><li>Vérifiez que les données envoyées au flux retourné par la propriété <xref:System.Printing.PrintSystemJobInfo.JobStream> sont au format XPS en tant que flux de package.</li></ul>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Printing.PrintSystemJobInfo.JobStream`

-->
