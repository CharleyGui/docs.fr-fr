---
ms.openlocfilehash: 26e521a86b504824f035ad5d40e4a04d2ea26abc
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022963"
---
### <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a>Intergiciel : l’intergiciel (middleware) du gestionnaire d’exceptions lève une exception d’origine si le gestionnaire est introuvable

Avant le ASP.NET Core 5,0, l’intergiciel (middleware) du [Gestionnaire d’exceptions](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) exécute le gestionnaire d’exceptions configuré quand une exception s’est produite. Si le gestionnaire d’exceptions, configuré via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> , est introuvable, une réponse HTTP 404 est générée. La réponse est trompeuse en ce qui suit :

* Semble être une erreur de l’utilisateur.
* Masque le fait qu’une exception s’est produite sur le serveur.

Pour résoudre l’erreur trompeuse dans ASP.NET Core 5,0, le `ExceptionHandlerMiddleware` lève l’exception d’origine si le gestionnaire d’exceptions est introuvable. Par conséquent, une réponse HTTP 500 est générée par le serveur. La réponse sera plus facile à examiner dans les journaux du serveur lors du débogage de l’erreur qui s’est produite.

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288).

#### <a name="version-introduced"></a>Version introduite

5,0 RC 1

#### <a name="old-behavior"></a>Ancien comportement

L’intergiciel (middleware) du gestionnaire d’exceptions génère une réponse HTTP 404 si le gestionnaire d’exceptions configuré est introuvable.

#### <a name="new-behavior"></a>Nouveau comportement

L’intergiciel (middleware) du gestionnaire d’exceptions lève l’exception d’origine si le gestionnaire d’exceptions configuré est introuvable.

#### <a name="reason-for-change"></a>Motif de modification

L’erreur HTTP 404 ne fait pas de évidente qu’une exception s’est produite sur le serveur. Cette modification génère une erreur HTTP 500 pour le rendre évident :

* Le problème n’est pas dû à une erreur de l’utilisateur.
* Une exception a été rencontrée sur le serveur.

#### <a name="recommended-action"></a>Action recommandée

Il n’y a aucune modification de l’API. Toutes les applications existantes continueront à se compiler et à s’exécuter. L’exception levée est gérée par le serveur. Par exemple, l’exception est convertie en réponse d’erreur HTTP 500 par [Kestrel](/aspnet/core/fundamentals/servers/kestrel) ou [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!--

#### Affected APIs

Not detectable via API analysis

-->
