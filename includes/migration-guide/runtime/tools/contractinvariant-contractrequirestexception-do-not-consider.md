---
ms.openlocfilehash: 794e43826af8f443a2cbb43b41f233766adc9dfd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802964"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant ou Contract.Requires\<TException> ne considèrent pas String.IsNullOrEmpty comme pure

|   |   |
|---|---|
|Détails|Pour les applications qui ciblent .NET Framework 4.6.1, si le contrat d’invariant pour <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> ou le contrat de condition préalable pour <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> appelle la méthode <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType>, le module de réécriture émet l’avertissement CC1036 du compilateur : &quot;Detected call to method 'System.String.IsNullOrWhteSpace(System.String)' without [Pure] in method.&quot; Il s’agit d’un avertissement du compilateur, plutôt que d’une erreur du compilateur.|
|Suggestion|Ce comportement est abordé dans le [problème 339](https://github.com/Microsoft/CodeContracts/issues/339), sur le site GitHub. Pour éviter cet avertissement, vous pouvez télécharger et compiler une version mise à jour du code source pour l’outil Contrats de code sur le site [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Des informations sur le téléchargement se trouvent au bas de la page.|
|Portée|Mineur|
|Version|4.6.1|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|

