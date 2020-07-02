---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619943"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad ne doit pas servir dans le fichier de fonctionnalités personnalisé, car il est désormais une fonctionnalité du navigateur

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, iPad étant un identificateur dans le fichier de fonctionnalités du navigateur ASP.NET par défaut, il ne doit pas être utilisé dans un fichier de fonctionnalités personnalisé

#### <a name="suggestion"></a>Suggestion

Si des fonctionnalités spécifiques à l’iPad sont requises, il est nécessaire de modifier le comportement de l’iPad en définissant des fonctionnalités sur la passerelle prédéfinie refID &quot;IPad&quot; et non en générant un ID &quot;IPad&quot; par mise en correspondance de l’agent utilisateur.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|
