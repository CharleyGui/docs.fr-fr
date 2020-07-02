---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614523"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a>ServiceBase ne propage pas les exceptions OnStart

#### <a name="details"></a>Détails

Dans .NET Framework 4.7 et antérieur, les exceptions levées au démarrage du service ne sont pas propagées à l’appelant de <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.<br/>À compter des applications qui ciblent .NET Framework 4.7.1, le runtime propage les exceptions à <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> pour les services qui ne parviennent pas à démarrer.

#### <a name="suggestion"></a>Suggestion

Au démarrage du service, si une exception est rencontrée, cette exception est propagée. Le diagnostic des cas où les services ne parviennent pas à démarrer devrait s’en trouver facilité. <br/>Si ce comportement n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant l’élément &lt;AppContextSwitchOverrides&gt; suivant à la section &lt;runtime&gt; du fichier de configuration de votre application :

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

Si votre application cible une version antérieure à 4.7.1, mais que vous voulez ce comportement, ajoutez l’élément &lt;AppContextSwitchOverrides&gt; suivant à la section &lt;runtime&gt; du fichier de configuration de votre application :

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.7.1       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
