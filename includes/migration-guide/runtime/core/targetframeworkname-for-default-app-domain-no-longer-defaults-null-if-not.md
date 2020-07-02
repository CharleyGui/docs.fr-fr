---
ms.openlocfilehash: f955e270f709ddf6eea2e44bbcf386e372b9f6e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621312"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>Dans le domaine d’application par défaut, TargetFrameworkName ne prend plus la valeur Null par défaut quand il n’est pas défini

#### <a name="details"></a>Détails

Avant, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> était défini sur la valeur Null dans le domaine d’application par défaut quand il n’était pas défini explicitement. À compter de la version 4.6, la valeur par défaut de la propriété <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> du domaine d’application par défaut est dérivée de TargetFrameworkAttribute (si celui-ci est présent). Les domaines d’application autres que ceux par défaut continuent d’hériter leur valeur <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> du domaine d’application par défaut (qui n’aura pas la valeur Null par défaut dans la version 4.6), sauf si cette valeur est substituée explicitement.

#### <a name="suggestion"></a>Suggestion

Le code doit être mis à jour pour ne pas attendre que <xref:System.AppDomainSetup.TargetFrameworkName> ait la valeur Null par défaut. Si vous avez besoin que cette propriété continue de prendre la valeur Null, vous pouvez la définir explicitement sur cette valeur.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
