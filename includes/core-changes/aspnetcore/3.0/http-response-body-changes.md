---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198421"
---
### <a name="http-response-body-infrastructure-changes"></a>HTTP : Changements dans l’infrastructure du corps d’intervention

L’infrastructure soutenant un organisme de réponse HTTP a changé. Si vous utilisez `HttpResponse` directement, vous ne devriez pas avoir besoin d’apporter des modifications de code. Lire la suite si vous `HttpResponse.Body` enveloppez, `HttpContext.Features`remplacez ou accédez .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Il y avait trois API associées à l’organisme de réponse HTTP :

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a>Nouveau comportement

Si vous `HttpResponse.Body`remplacez, il `IHttpResponseBodyFeature` remplace l’ensemble par `StreamResponseBodyFeature` un emballage autour de votre flux donné en utilisant pour fournir des implémentations par défaut pour toutes les API attendues. Le réglage du flux d’origine renvoie ce changement.

#### <a name="reason-for-change"></a>Raison du changement

La motivation est de combiner les API du corps de réponse en une seule nouvelle interface de fonctionnalité.

#### <a name="recommended-action"></a>Action recommandée

Utilisez `IHttpResponseBodyFeature` où vous `IHttpResponseFeature.Body` `IHttpSendFileFeature`utilisiez auparavant, , ou `IHttpBufferingFeature`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
