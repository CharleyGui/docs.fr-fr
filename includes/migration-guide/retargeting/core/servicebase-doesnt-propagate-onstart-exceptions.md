---
ms.openlocfilehash: 519de92ca4201d199941afe6382ddf9fc480fbbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614523"
---
### <a name="servicebase-doesnt-propagate-onstart-exceptions"></a><span data-ttu-id="36f07-101">ServiceBase ne propage pas les exceptions OnStart</span><span class="sxs-lookup"><span data-stu-id="36f07-101">ServiceBase doesn't propagate OnStart exceptions</span></span>

#### <a name="details"></a><span data-ttu-id="36f07-102">Détails</span><span class="sxs-lookup"><span data-stu-id="36f07-102">Details</span></span>

<span data-ttu-id="36f07-103">Dans .NET Framework 4.7 et antérieur, les exceptions levées au démarrage du service ne sont pas propagées à l’appelant de <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="36f07-103">In the .NET Framework 4.7 and earlier versions, exceptions thrown on service startup are not propagated to the caller of <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType>.</span></span><br/><span data-ttu-id="36f07-104">À compter des applications qui ciblent .NET Framework 4.7.1, le runtime propage les exceptions à <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> pour les services qui ne parviennent pas à démarrer.</span><span class="sxs-lookup"><span data-stu-id="36f07-104">Starting with applications that target the .NET Framework 4.7.1, the runtime propagates exceptions to <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> for services that fail to start.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="36f07-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="36f07-105">Suggestion</span></span>

<span data-ttu-id="36f07-106">Au démarrage du service, si une exception est rencontrée, cette exception est propagée.</span><span class="sxs-lookup"><span data-stu-id="36f07-106">On service start, if there is an exception, that exception will be propagated.</span></span> <span data-ttu-id="36f07-107">Le diagnostic des cas où les services ne parviennent pas à démarrer devrait s’en trouver facilité.</span><span class="sxs-lookup"><span data-stu-id="36f07-107">This should help diagnose cases where services fail to start.</span></span> <br/><span data-ttu-id="36f07-108">Si ce comportement n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant l’élément &lt;AppContextSwitchOverrides&gt; suivant à la section &lt;runtime&gt; du fichier de configuration de votre application :</span><span class="sxs-lookup"><span data-stu-id="36f07-108">If this behavior is undesirable, you can opt out of it by adding the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=true" />
```

<span data-ttu-id="36f07-109">Si votre application cible une version antérieure à 4.7.1, mais que vous voulez ce comportement, ajoutez l’élément &lt;AppContextSwitchOverrides&gt; suivant à la section &lt;runtime&gt; du fichier de configuration de votre application :</span><span class="sxs-lookup"><span data-stu-id="36f07-109">If your application targets an earlier version than 4.7.1 but you want to have this behavior, add the following &lt;AppContextSwitchOverrides&gt; element to the &lt;runtime&gt; section of your application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.ServiceProcess.DontThrowExceptionsOnStart=false" />
```

| <span data-ttu-id="36f07-110">Nom</span><span class="sxs-lookup"><span data-stu-id="36f07-110">Name</span></span>    | <span data-ttu-id="36f07-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="36f07-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="36f07-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="36f07-112">Scope</span></span>   | <span data-ttu-id="36f07-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="36f07-113">Minor</span></span>       |
| <span data-ttu-id="36f07-114">Version</span><span class="sxs-lookup"><span data-stu-id="36f07-114">Version</span></span> | <span data-ttu-id="36f07-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="36f07-115">4.7.1</span></span>       |
| <span data-ttu-id="36f07-116">Type</span><span class="sxs-lookup"><span data-stu-id="36f07-116">Type</span></span>    | <span data-ttu-id="36f07-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="36f07-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="36f07-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="36f07-118">Affected APIs</span></span>

- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase)?displayProperty=nameWithType>
- <xref:System.ServiceProcess.ServiceBase.Run(System.ServiceProcess.ServiceBase[])?displayProperty=nameWithType>
