---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394479"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>SPAs: SpaServices et NodeServices marqués obsolètes

Le contenu des paquets NuGet suivants n’ont pas été nécessaires depuis ASP.NET Core 2.1. Par conséquent, les paquets suivants sont marqués comme obsolètes :

- [Microsoft.AspNetCore.SpaServices (en anglais seulement)](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [Microsoft.AspNetCore.NodeServices (en anglais seulement)](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

Pour la même raison, les modules npm suivants sont marqués comme dépréciés :

- [aspnet-angulaire](https://www.npmjs.com/package/aspnet-angular)
- [aspnet-prerendering](https://www.npmjs.com/package/aspnet-prerendering)
- [aspnet-webpack](https://www.npmjs.com/package/aspnet-webpack)
- [aspnet-webpack-réagir](https://www.npmjs.com/package/aspnet-webpack-react)
- [domaine-tâche](https://www.npmjs.com/package/domain-task)

Les paquets précédents et les modules npm seront plus tard supprimés en .NET 5.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les paquets dépréciés et les modules npm étaient destinés à intégrer ASP.NET Core avec divers cadres d’application à une page unique (SPA). Ces cadres incluent Angular, React, et React with Redux.

#### <a name="new-behavior"></a>Nouveau comportement

Un nouveau mécanisme d’intégration existe dans le paquet [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet. Le paquet demeure la base des modèles de projet Angular and React depuis ASP.NET Core 2.1.

#### <a name="reason-for-change"></a>Raison du changement

ASP.NET Core soutient l’intégration avec divers cadres d’applications à une seule page (SPA), y compris Angulaire, Réagir et réagir avec Redux. Initialement, l’intégration avec ces cadres a été réalisée avec ASP.NET composants core-spécifiques qui traitaient des scénarios comme le prerendering côté serveur et l’intégration avec Webpack. Au fil du temps, les normes de l’industrie ont changé. Chacun des cadres SPA a publié ses propres interfaces standard de ligne de commande. Par exemple, Angular CLI et create-react-app.

Lorsque ASP.NET Core 2.1 a été publié en mai 2018, l’équipe a réagi à la modification des normes. Une façon plus nouvelle et plus simple de s’intégrer aux propres chaînes d’outils des cadres SPA a été fournie. Le nouveau mécanisme d’intégration `Microsoft.AspNetCore.SpaServices.Extensions` existe dans le paquet et demeure la base des modèles de projets Angular et React depuis ASP.NET Core 2.1.

Pour préciser que les composants les plus anciens ASP.NET propres au noyau ne sont pas pertinents et ne sont pas recommandés :

- Le mécanisme d’intégration avant 2,1 est considéré comme obsolète.
- Les forfaits npm de soutien sont marqués comme dépréciés.

#### <a name="recommended-action"></a>Action recommandée

Si vous utilisez ces paquets, mettez à jour vos applications pour utiliser les fonctionnalités :

- Dans `Microsoft.AspNetCore.SpaServices.Extensions` le paquet.
- Fourni par les cadres SPA que vous utilisez

Pour activer des fonctionnalités telles que le prerendering côté serveur et le rechargement du module chaud, consultez la documentation du cadre SPA correspondant. La fonctionnalité `Microsoft.AspNetCore.SpaServices.Extensions` n’est *pas* obsolète et continuera d’être prise en charge.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
