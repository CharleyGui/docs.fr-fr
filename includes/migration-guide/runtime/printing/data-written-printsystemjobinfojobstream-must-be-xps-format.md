---
ms.openlocfilehash: 74f00821f2304664729faa8de2f0163c6611f513
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379569"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>Les données écrites dans PrintSystemJobInfo.JobStream doivent être au format XPS

|   |   |
|---|---|
|Détails|La propriété <xref:System.Printing.PrintSystemJobInfo.JobStream> expose le flux d’un travail d’impression. L’utilisateur peut envoyer des données brutes aux composants d’impression du système d’exploitation sous-jacent en écrivant dans ce flux. À compter de .NET Framework 4.5 sur Windows 8 et les versions ultérieures du système d’exploitation Windows, les données écrites dans ce flux doivent être au format XPS en tant que flux de package.|
|Suggestion|Pour sortir le contenu d’impression, vous pouvez procéder de l’une des manières suivantes :<ul><li>Utilisez la classe <xref:System.Windows.Xps.XpsDocumentWriter> pour sortir le contenu d’impression. Il s’agit de l’alternative recommandée.</li><li>Vérifiez que les données envoyées au flux retourné par la propriété <xref:System.Printing.PrintSystemJobInfo.JobStream> sont au format XPS en tant que flux de package.</li></ul>|
|Portée|Mineur|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
