---
ms.openlocfilehash: 639cd13978cc33bd7c4524a17e92d566404bbaea
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96476801"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant ou Contract.Requires\<TException> ne considèrent pas String.IsNullOrEmpty comme pure

#### <a name="details"></a>Détails

Pour les applications qui ciblent le .NET Framework 4.6.1, si le contrat d’invariant pour <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> ou le contrat de condition préalable pour <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> appelle la <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> méthode, le ReWriter émet l’avertissement du compilateur CC1036 : un &quot; appel à la méthode’System. String. IsNullOrWhiteSpace (System. String) 'sans [pure] dans la méthode est détecté. &quot; Il s’agit d’un avertissement du compilateur plutôt qu’une erreur du compilateur.

#### <a name="suggestion"></a>Suggestion

Ce comportement est abordé dans le [problème 339](https://github.com/Microsoft/CodeContracts/issues/339), sur le site GitHub. Pour éviter cet avertissement, vous pouvez télécharger et compiler une version mise à jour du code source pour l’outil Contrats de code sur le site [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md). Des informations sur le téléchargement se trouvent au bas de la page.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.6.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)`
- `M:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)`

-->
