---
ms.openlocfilehash: f221f923381d874e1d9e8b420811a770d86f7578
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858539"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>Dans le domaine d’application par défaut, TargetFrameworkName ne prend plus la valeur Null par défaut quand il n’est pas défini

|   |   |
|---|---|
|Détails|Avant, <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> était défini sur la valeur Null dans le domaine d’application par défaut quand il n’était pas défini explicitement. À compter de la version 4.6, la valeur par défaut de la propriété <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> du domaine d’application par défaut est dérivée de TargetFrameworkAttribute (si celui-ci est présent). Les domaines d’application autres que ceux par défaut continuent d’hériter leur valeur <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=name> du domaine d’application par défaut (qui n’aura pas la valeur Null par défaut dans la version 4.6), sauf si cette valeur est substituée explicitement.|
|Suggestion|Le code doit être mis à jour pour ne pas attendre que <xref:System.AppDomainSetup.TargetFrameworkName> ait la valeur Null par défaut. Si vous avez besoin que cette propriété continue de prendre la valeur Null, vous pouvez la définir explicitement sur cette valeur.|
|Portée|Microsoft Edge|
|Version|4.6|
|Type|Runtime|
|API affectées|<ul><li><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|

