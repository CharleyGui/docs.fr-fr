---
ms.openlocfilehash: 204fe32ec8b7fbaab89e37d7e761469212091728
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237926"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant ou Contract.Requires\<TException> ne considèrent pas String.IsNullOrEmpty comme pure

|   |   |
|---|---|
|Détails|Pour les applications qui ciblent le cadre .NET 4.6.1, si le contrat invariant <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> pour ou le contrat de condition préalable pour <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> les appels de la <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> méthode, le rewriter émet l’avertissement compilateur CC1036: &quot;Appel détecté à la méthode 'System.String.IsNullOrWhteSpace (System.String)' sans [Pure] en méthode. &quot; Il s’agit d’un avertissement de compilateur plutôt que d’une erreur de compilateur.|
|Suggestion|Ce comportement est abordé dans le [problème 339](https://github.com/Microsoft/CodeContracts/issues/339), sur le site GitHub. Pour éviter cet avertissement, vous pouvez télécharger et compiler une version mise à jour du code source pour l’outil Contrats de code sur le site [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Des informations sur le téléchargement se trouvent au bas de la page.|
|Étendue|Secondaire|
|Version|4.6.1|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType></li></ul>|
